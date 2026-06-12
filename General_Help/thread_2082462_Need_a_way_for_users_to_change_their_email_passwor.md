---
title: "Need a way for users to change their email passwords"
date: 2012-11-09
forum: General Help
---

### Post by icedutah on 2012-11-09
Hello,

Is there an easy way for an end user to change their email password? I just installed Ubuntu 12.04 server, Postfix, LAMP, Dovecot, Horde 5 webmail, etc....

I don't like to ask someone what they want their password to be for creating an email account. 

I am about to roll out this new server that replaces a very old Redhat 9.0 email server which used /etc/passwd local authentication. This new Ubuntu server will use virtual user accounts in a Mysql database.

---

### Post by slickymaster on 2012-11-09
Make sure you have installed all the libldap related libraries - for eg., libnss-ldap, libpam-ldap, libkrb53. Post that, try imposing the policies once again.

---

### Post by icedutah on 2012-11-09
Switched from Horde mail to using Roundcube. Have it working fine now.

---

