---
title: "postfix, dovecot, SMTP problem"
date: 2014-01-08
forum: General Help
---

### Post by grizdog on 2014-01-08
Hello,

I recently upgraded to a new computer with Ubuntu 13.10.  I have long run a web an mail server on my computer, using my own domain.  The web server is working, and the domain name is recognized.  But mail is not working.

I have been using dovecot and postfix, with SASL authentication.  I use Thunderbird as my client.  Thunderbird appears to be working fine, I read mail on several other sites with no problem.  At first, it would fail to find my own mail server, but now it does, and I can use Thunderbird to peruse old saved messages on my server.  I can also send myself an email, from this computer to itself, and I can send an email with this computer as a return address.  The problem is no one else can send me an email from outside.  I ran a test from outside and got an error that SMTP could not connect to my computer.

Also, I have been having some permission problems with ~/Maildir. I have a tried a lot of different permission/ownership combinations, but nothing I have tried seems to help.   Here are some representative lines from the logfile, with the domain x'ed out.

```
Jan  8 16:26:39 xxxxxxxx dovecot: imap(alex): Error: stat(/home/alex/Maildir/dovecot.index.log) failed: Permission denied (euid=1000(alex) egid=1000(alex) missing +x perm: /home/alex/Maildir, dir owned by 130:1000 mode=0700)
Jan  8 16:26:39 xxxxxxxx dovecot: imap(alex): Error: stat(/home/alex/Maildir/dovecot.index) failed: Permission denied (euid=1000(alex) egid=1000(alex) missing +x perm: /home/alex/Maildir, dir owned by 130:1000 mode=0700)
Jan  8 16:26:39 xxxxxxxx dovecot: imap(alex): Error: stat(/home/alex/Maildir/new) failed: Permission denied
```


Even though the errors talk about dovecot, it seems like postfix is the problem with SMTP not connecting.  Anyone seen this?  Incidentally, the standard Ubuntu documentation on this appears to be a trifle out of date - the files are  a little different now.

Thanks for any help.

---

### Post by grizdog on 2014-01-09
Not a lot of interest here - do I have to report more log messages?

Question for others who have a mail server at home in the U.S:  Is it possible that my line provider or ISP is locking me out of any smtp connections?

---

