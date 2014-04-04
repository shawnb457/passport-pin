# passport-pin



[Passport](http://passportjs.org/) strategy for authenticating with a pin

This module lets you authenticate using a pin in your Node.js
applications.  By plugging into Passport, local authentication can be easily and
unobtrusively integrated into any application or framework that supports
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

## Install

    $ npm install passport-pin

## Usage

#### Configure Strategy

The local authentication strategy authenticates users using a username and
password.  The strategy requires a `verify` callback, which accepts these
credentials and calls `done` providing a user.

    passport.use(new PinStrategy(
      function(pin, done) {
        User.findOne({ pin: pin }, function (err, user) {
          if (err) { return done(err); }
          if (!user) { return done(null, false); }
          if (!user.verifyPassword(password)) { return done(null, false); }
          return done(null, user);
        });
      }
    ));

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'pin'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

    app.post('/pinlogin', 
      passport.authenticate('local', { failureRedirect: '/login' }),
      function(req, res) {
        res.redirect('/');
      });

## Examples

For complete, working examples, refer to the multiple [examples](https://github.com/jaredhanson/passport-local/tree/master/examples) included.

## Tests

    $ npm install
    $ npm test

## Credits

  - [Shawn Brinkman](http://github.com/shawnb457)

## License

[The MIT License](http://opensource.org/licenses/MIT)

Copyright (c) 2011-2014 Shawn Brinkman 
