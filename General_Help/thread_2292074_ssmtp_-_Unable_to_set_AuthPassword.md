---
title: "ssmtp - Unable to set AuthPassword"
date: 2015-08-24
forum: General Help
---

### Post by meeotch on 2015-08-24
I'm trying to get ssmtp working, and I can't get it to accept a password in ssmtp.conf.  Here's what I've got, appropriately sanitized:

```
root=user@host.com
mailhub=mail.host.com:465
AuthUser=user@host.com
AuthPassword=thisisthepassword
hostname=hostname
FromLineOverride=YES
UseTLS=YES
```

If I try to send a test message with:
```
ssmtp someone@foo.com
```

It fails with the following in /var/log/mail.log:
```
Unable to set AuthPassword="thisisthepassword"
```

However, if I give it the password on the command line:
```
ssmtp -ap thisisthepassword someone@foo.com
```

It succeeds (with the same error in mail.log).  I've tried various permutations of file permissions, thinking it might be a security feature to reject passwords in the ssmtp.conf if it was world-readable or something, but no love.  For now, I've implemented the ugly workaround of wrapping ssmtp in a script that tacks on the -ap argument, and symlinking sendmail to that script.  But I'd like to get this working the "right" way.

---

### Post by steeldriver on 2015-08-25
Hmm... I thought the field name was [FONT=courier new]AuthPass[/FONT] rather than [FONT=courier new]AuthPass*word*[/FONT]? check the ssmtp.conf man page to be sure

---

### Post by meeotch on 2015-08-25
Ha - that was it.  I'm an idiot.  Thanks!

...and it looks like I'm not the only one:  [http://blog.gerv.net/2014/02/why-is-email-so-hard/](http://blog.gerv.net/2014/02/why-is-email-so-hard/)

---

