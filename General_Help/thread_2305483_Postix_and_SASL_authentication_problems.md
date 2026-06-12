---
title: "Postix and SASL authentication problems"
date: 2015-12-06
forum: General Help
---

### Post by SuperGeorge on 2015-12-06
i am unable to sendmail with my current postfix sasl config.  It won't accept the password when entered and mail generates this error report:

Dec  6 10:19:44 supergeorge-desktop postfix/smtpd[5805]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Dec  6 10:19:44 supergeorge-desktop postfix/smtpd[5805]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Dec  6 10:19:44 supergeorge-desktop postfix/smtpd[5805]: warning: SASL authentication failure: no secret in database
Dec  6 10:19:44 supergeorge-desktop postfix/smtpd[5805]: warning: localhost[127.0.0.1]: SASL DIGEST-MD5 authentication failed: authentication failure

/etc/sasldb2 does exist so i'm confused.

Any help wouuld be appreciated. thanx

---

### Post by T.J. on 2015-12-06
Your SASL (Simple Authentication and Security Layer)  file is not configured properly, and so Postfix cannot authenticate.  Use the "saslpasswd2" utility to create the necessary sasldb2 file.  =)  This may help:  [https://cyrusimap.org/docs/cyrus-sasl/1.5.28/sysadmin.php](https://cyrusimap.org/docs/cyrus-sasl/1.5.28/sysadmin.php)

As someone who used to work on email sersvers for ISPs, I'm not trying to be mean or rude when I say that it's extremely important that you read the documentation and manuals for the software you are using.  Email is far more complex a maintenance task than people think it is.  It is very important that you learn the specific details of what you are using if you are going to solve support cases.

---

### Post by SuperGeorge on 2015-12-07
Thanx for your reply and yes, i'm a super newb to linux if it don't show :)

---

### Post by SuperGeorge on 2015-12-07
Solved.   i had no smtpd.conf file so i executed these commands to finish the set up.   Hope this helps someone :)

echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
echo 'mech_list: plain login' >> /etc/postfix/sasl/smtpd.conf

---

### Post by T.J. on 2015-12-07
Awesome-sauce!  Please mark the thread "Solved"

---

