---
title: "cannot remove /etc/mail/sendmail.cf :read only file system"
date: 2007-06-21
forum: General Help
---

### Post by zoutmax on 2007-06-21
Hello,

When booting, at the orange Ubuntu splash screen the headings of what is booting apear like normal woth the [OK] apearing next to them, 
until Ubuntu reaches BASIC NETWORKING. 
From here a black and white screen appears and says the following:

[COLOR="Blue"]cannot remove /etc/mail/sendmail.cf :read only file system
Updating Autehntication
/usr/share/sendmail/update_auth : line 98 : cannot create temp file for here

Creating /etc/mail/relay
Optional file

You should Issue "/etc/init.d/sendmail reload"[/COLOR]

There is the result of the requested command :

[COLOR="blue"]root@mailserver:~# /etc/init.d/sendmail reload
Reloading Mail Transport Agent configuration: sendmail.
root@mailserver:~#[/COLOR]

And the error come back a the next reboot like if the command did nothing.

There is a link where another user get exactly the same error :( :
[http://ubuntuforums.org/archive/index.php/t-269582.html](http://ubuntuforums.org/archive/index.php/t-269582.html)

Please help me i already reinstalled sendmail but the error is still there.

Thanks :D

---

