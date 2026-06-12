---
title: "Cyrus21-IMAPd Configuration Help"
date: 2005-05-05
forum: General Help
---

### Post by hypenazer on 2005-05-05
I'm trying to configure my Ubuntu box to work as a mail server running Postfix & Cyrus.  So far I have simply installed the Postfix and Cyrus packages (and dependencies) using the "Synaptic Package Manager".  I then edited the /etc/postfix/main.cf file.

I've confirmed that Postfix works but Cyrus is causing me trouble.  It responds to a telnet request (telnet 127.0.0.1 imap) and will even respond to ". noop".  the problem is I cannot seem to create any users within Cyrus.  I get an authentication failure every time I try to log in using the Cyrus admin (cyradm -u cyrus localhost). I'm using the Cyrus admin specified in /etc/imapd.conf.

I've tried to follow the directions located in /usr/share/doc/cyrus21-doc/README.Debian.simpleinstall.gz. but I run in to trouble at step 2.

Step 2 is to "make sure /etc/sasldb2 is readable by group sasl" the trouble that I'm having is, I don't even have /etc/sasldb2

Might anyone be able to suggest a solution or point me in the direction of some "simpleinstall" documentation that isn't 18 months old?  I would classify my level of experience as "beginner with a handicap".

Scott ](*,)

---

### Post by Klunk on 2005-05-12
I had a similar problem, I upgraded to hoary and installed the sasl package. The next thing I had to do was change the Cyrus config file (imapd.conf) to change the authentication method.

change sasl_pwcheck_method to be set to auxprop

I did this last night and hey presto it worked :)

---

### Post by nocturn on 2005-08-16
Did you get this working?

I'm strugling with a similar problem:
[http://ubuntuforums.org/showthread.php?p=303763#post303763](http://ubuntuforums.org/showthread.php?p=303763#post303763)

---

### Post by sundancer on 2006-01-17
Have you set password for user cyrus? This is done using ```
sudo saslpasswd2 cyrus
```? That was all i had to do on a fresh install of cyrus.

---

