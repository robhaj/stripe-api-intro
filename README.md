## Stripe.js
Stripe.js makes it easy to collect credit card (and other similarly sensitive) details without having the information touch your server. If you need help after reading this, check out our answers to common questions or chat live with other developers in #stripe on freenode.

### Register an account with Stripe
[Register] (https://dashboard.stripe.com/register)

### API Keys
Once registered and logged in, go to your Account Settings and click on the API Keys tab. Or click [here](https://dashboard.stripe.com/account/apikeys).
You should see a Test Secret Key and Test Publishable Key.


### Including the Stripe Library on the Front-End
- Including Stripe.js
- Add this script tag to your page to get started with Stripe.js.

``` <script type="text/javascript" src="https://js.stripe.com/v2/"></script>```

### Setting Your Publishable Key

You must set your publishable key before using Stripe.js to identify your website when communicating with Stripe.

```Stripe.setPublishableKey('pk_test_5y4vYN3HeeeDJieExOlz2Fmk'); ```

### Collecting card details

createToken converts sensitive card data to a single-use token which you can safely pass to your server to charge the user. The tutorial explains this flow in more detail.

```Stripe.card.createToken({
  number: $('.card-number').val(),
  cvc: $('.card-cvc').val(),
  exp_month: $('.card-expiry-month').val(),
  exp_year: $('.card-expiry-year').val()
}, stripeResponseHandler); ```

- The first argument to createToken is a JavaScript object containing credit card data entered by the user. It should contain the following required fields:

  - number: card number as a string without any separators, e.g. '4242424242424242'.

  - exp_month: two digit number representing the card's expiration month, e.g. 12.
  - exp_year: two or four digit number representing the card's expiration year, e.g. 2017.


- The following fields are optional but recommended to help prevent fraud:

  - cvc: card security code as a string, e.g. '123'.
