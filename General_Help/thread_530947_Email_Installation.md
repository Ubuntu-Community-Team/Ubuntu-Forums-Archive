---
title: "Email Installation"
date: 2007-08-21
forum: General Help
---

### Post by kroynos on 2007-08-21
I cannot get my email to get any mail from my ubuntu server, all the postfix is setup by the howto from this site. but it keeps asking for the password. anybody know how to get the email client to work to pull mail from your server?

---

### Post by kevstar31 on 2007-08-22
Did you try your password for login that you used to setup the machine?

---

### Post by kroynos on 2007-08-22
Yes i did, this is the error i am getting even know the password is correct but i am still get the same error everytime.

There was a problem logging onto your mail server. Your Password was rejected. Account: '192.168.1.108', Server: '192.168.1.108', Protocol: POP3, Server Response: '-ERR Login failed.', Port: 995, Secure(SSL): Yes, Server Error: 0x800CCC90, Error Number: 0x800CCC92

---

### Post by kevstar31 on 2007-08-22
Point me to the guide you used.

---

### Post by kroynos on 2007-08-22
[https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html)

hope this helps

---

### Post by kroynos on 2007-08-24
can somebody tell me why i am getting a relay denied?

here is the Denial

Connected to deepmine.deepmine.info.
Escape character is '^]'.
220 mail.deepmine.info ESMTP Postfix (Ubuntu)
HELO mail.deepmine
250 mail.deepmine.info
MAIL FROM:
501 5.5.4 Syntax: MAIL FROM:<address>
MAIL FROM:kroynos@gmail.com
250 2.1.0 Ok
RCPT TO:kroynos@gmail.com
554 5.7.1 <kroynos@gmail.com>: Relay access denied

---

