---
title: "mail-notification and IMAP/SSL"
date: 2006-10-31
forum: General Help
---

### Post by Lutze on 2006-10-31
Hello everyone,

I was very glad to see that mail-notification is back with SSL-Support in edgy. However, it does not work.

mail-notification-INFO: user@host: connecting to mail.host (IP) port 993
mail-notification-INFO: user@host: connected successfully
mail-notification-INFO: user@host: connected successfully

And that's it. I get no connection to the imapd afterwards. This happens on both of my IMAP mail accounts.

What both of them have in common are "bad" certificates. No idea, if that might be a reason.

Any ideas?

regards,

Lutze

---

### Post by KillerBOB on 2006-11-03
Hi, I have the very same problem with mail-notification and IMAP/SSL. I was also very happy when SSL seemed to be enabled by default in the repositories M-N... too bad it doesn't work as supposed

On dapper I had to compile in support myself, haven't yet tried that in edgy.

*EDIT*
I am by no means an expert packager, but I have managed to build a mail-notification package for Egdy with SSL-support included. It's not a checkinstall, I have rather used the repo-source (apt-get source mail-notification) and edited the debian/rules (enable SSL), debian/changelog (to bump version to *9 to prevent apt to update) and debian/control (add dependency for libssl).

This *should* install and work nicely on Edgy systems without interfering with the repositories. But I don't take any resposibility if it breaks your system. It works very good for me though =).
Please give me some feedback if it works or not, and what possible mistakes I have made in the progress.

Download the attached file to your home directory, and then open up a terminal and type:

```
tar xvzf mail-notification.tar.gz
sudo dpkg -i mail-notification_3.0.dfsg.1-3ubuntu9_i386.deb
```


Take care

---

### Post by rpw on 2006-11-03
Hello,

I can confirm this behaviour too.

Sorry to say, but this is a same. Mail-notification (with SSL) did not work in breezy, not in dapper and now it's not working in edgy.

I'm not a programmer, but is it really that damned hard to create a mail-notification that really works (including SSL)?

That's why at the moment i switched to Kubuntu, and surprise surprise, korn (the name of the mail-notification program for KDE) is doing absolutly fine on exact the same mailboxes!

It's kind of strange too me, if not even unbelievable.

rpw

---

### Post by KillerBOB on 2006-11-03
The reason why it's not enabled seems to be a licensing issue (i don't know the details). This is from the README.Debian:

```
mail-notification for Debian
----------------------------

I had to disable SSL because of a license issue.
Hopefully, this will be solve soon.
....

```

But it seems strange that other packages are allowed to come precompiled with SSL-support??

---

### Post by Lutze on 2006-11-14
> **KillerBOB said:**
> The reason why it's not enabled seems to be a licensing issue (i don't know the details). This is from the README.Debian:

```
mail-notification for Debian
----------------------------

I had to disable SSL because of a license issue.
Hopefully, this will be solve soon.
....

```

But it seems strange that other packages are allowed to come precompiled with SSL-support??

The README-Notice has not changed since breezy - I did not trust it, because the SSL option was greyed out before and is not anymore. Anyway, the package above works well - thanks a lot!

The reason, why other applications come with SSL is that mail-notification is not built against gnutls, but another SSL-library that is not entirely free. It should not be a problem at all to build it with gnutls, but for any reason, it's not done. One should contact the maintainer.

---

