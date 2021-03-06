Discourse + Auth0
=================

<a href="https://auth0.com">
 <img src="https://s3.amazonaws.com/assets.auth0.com/logo/logo-180.png" />
</a>

[Auth0](https://auth0.com) is an authentication broker that supports social identity providers as well as enterprise identity providers such as Active Directory, LDAP, Office365, Google Apps, Salesforce.

----------------------------------

<a href="http://discourse.org">
  <img src="http://blog.ohheyworld.com/wp-content/uploads/2013/11/discourse-logo.png" />
</a>

[Discourse](http://discourse.org) is an open source forum software.

----------------------------------

This is a discourse plugin to do Single Sign On using Auth0.

### Demo: https://ask.auth0.com

![discourse login](https://dl.dropboxusercontent.com/u/21665105/discourse-login.gif)

## What do I get by using Auth0?

* Support for Active Directory / LDAP (see [animated gif](#adding-active-directory--ldap))
  * No matter if Discourse is on the cloud or on-prem, it will work transparently
  * Support for Kerberos too (configured by IP ranges)
* Support for other enterprise logins like SAML Protocol, Windows Azure AD, Google Apps, Salesforce, etc. All supported here: https://docs.auth0.com/identityproviders.
* Support for social providers without having to add OmniAuth strategies by hand. Just turn on/off social providers (see [animated gif](#adding-social-providers))
* Support for Single Sign On with other Discourse instances and any other application in your account (see [animated gif](#single-sign-on-between-multiple-discourse-forums).

## Installation

-  Create an account on [Auth0](http://auth0.com) and open the application settings.

-  Run in your discourse root folder:

```
rake plugin:install repo=https://github.com/auth0/discourse-plugin name=auth0
rm -rf tmp public/assets
rake assets:precompile
```

-  Login as an adminstrator to your discourse setting using one of the pre-existing auth plugins.

-  Configure the Auth0 plugin in the admin section

<img src="http://blog.auth0.com.s3.amazonaws.com/ss-2014-02-03T14-32-49.png">̇</img>

Enjoy!

----

#### Adding Active Directory / LDAP

![active directory config](https://dl.dropboxusercontent.com/u/21665105/ad-connection.gif)

#### Adding Social Providers

![social providers config](https://dl.dropboxusercontent.com/u/21665105/social-connections.gif)

#### Single Sign On Between multiple Discourse forums

![single sign on](https://dl.dropboxusercontent.com/u/21665105/sso-discourse.gif)

#### Single Sign On with Windows Authentication

![windows auth](https://s3.amazonaws.com/blog.auth0.com/login_discourse_kerberos-2.gif)

### Using Discourse Login Dialog instead of Auth0

You can keep using Discourse Login dialog and integrate only a specific connection from Auth0. It will show up as another button like the social providers.

Go to admin site settings for Auth0 and change the `auth0_connection` with the connection name you want to use from Auth0.

![](https://s3.amazonaws.com/blog.auth0.com/login_discourse_ad.gif)

### Give admin rights to an email

```
$ RAILS_ENV=production bundle exec rails c
$ u = User.find_by_email('the-email-you-want-to-make-admin@whatever.com')
$ u.admin = true
$ u.save!
```

## License

MIT - 2014 - AUTH0, INC.
