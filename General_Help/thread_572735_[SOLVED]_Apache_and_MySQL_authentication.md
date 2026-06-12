---
title: "[SOLVED] Apache and MySQL authentication"
date: 2007-10-10
forum: General Help
---

### Post by Daveski on 2007-10-10
I can't seem to find the correct documentation for the libapache2-mod-auth-mysql package. Every time I search the web I seem to find a different set of directives as it looks like the auth_mysql module has had a few forks.

Can someone point me at the docs for the version in the repositories? Or can someone post a working set of directives I can use as a template?

I am just trying to use basic authentication in apache to get username and passwords from a MySQL table.

Many thanks.

---

### Post by landryr on 2007-10-11
I also need assistance with this. I'm migrating an old intranet site from Slackware to Feisty and absolutely CANNOT get auth_mysql to work. I've tried directives from the Feisty docs, from SourceForge, and from various other HOWTOs... No luck.

I greatly appreciate any help out there.

---

### Post by Daveski on 2007-10-11
This might be broken as I found this Gusty bug listed:

[https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649](https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649)

I seem to be having similar problems with Feisty and this module. Has anyone got this working?

---

### Post by Daveski on 2007-10-12
I think I have this cracked.

Here is the additions I made to my apache2.conf after enabling the module:
```

Auth_MySQL_Info localhost webaccess xxx
Auth_MySQL_General_DB database

<Directory /var/www/test>
     AllowOverride All
</Directory>
```

and here is the sample .htaccess file in the protected area (test):

```
Options -Indexes

AuthBasicAuthoritative off
AuthMYSQL on

AuthType Basic
AuthName "test"

AuthMySQL_User webaccess
AuthMySQL_Password xxx
AuthMySQL_Host localhost
AuthMySQL_Authoritative on
AuthMySQL_DB database
AuthMySQL_Password_Table users
AuthMySQL_Username_Field username
AuthMySQL_Password_Field password

AuthMySQL_Empty_Passwords off
Auth_MySQL_Encryption_Types Plaintext Crypt_DES

AuthUserFile /var/www/test/test.html

require valid-user
```

The AuthUserFile seems to need to point to a real file, or perhaps /dev/null

---

### Post by landryr on 2007-10-15
Well... damn...

I'm in.

Daveski, many, MANY thanks. The first round is on me.

r

---

### Post by landryr on 2007-10-15
Now that I have a config that's working, I've done a little tinkering to see what specifically breaks it.

It seems that the filename directive is not the key... authentication on my machine doesn't require it. The deal-breaker is "AuthBasicAuthoritative off". Apparently, the Apache2 default of "on" blocks auth_mysql from handling the authentication.

r

---

