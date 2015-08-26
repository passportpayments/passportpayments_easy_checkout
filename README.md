# PassportPayments Client Library in JS
The repository contains the client support library for [PassportPayments API](https://api.passportpayments.com/docs/) written in Javascript

## Usage

```html

<html>
	<head>
		<script type="text/javascript" src="PassportPaymentsCheckout-1.0.0.min.js"></script>
		<script type="text/javascript" src="http://code.jquery.com/jquery-1.11.1.js"></script>
	</head>
	<body>
		<button id="pp_checkout" data-amount="2000">Pay</button>
	</body>

	<footer>
		<script>
			var instantPay = function (api_base, amount, public_key, params){
				var pp = new PassportPaymentsBuy(public_key, api_base, afterPayment);
				pp.openForm(amount, params);
			};
			// call Back function
			var afterPayment = function(transactionId){
				// Do whatever you want to do with this transaction id
				cnsole.log( transactionId );
			};

			$("#pp_checkout").on('click', function(e) {
				var api_base = "https://sandbox.passportpayments.com"; // replace sandbox with api in live mode
				var amount = $("#pp_checkout").data('amount'); // Amount is in Dollars (Rupees for India).
				var public_key = '{YOUR PUBLIC KEY}';
				var params = {
								'email':'sanborn.sen@gmail.com' // optional
							};
				instantPay(api_base, amount, public_key, params);
			});
		</script>
	</footer>
</html>

```