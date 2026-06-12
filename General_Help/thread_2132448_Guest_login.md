---
title: "Guest login"
date: 2013-04-04
forum: General Help
---

### Post by RyeMan on 2013-04-04
To keep kids off my computer (and the internet) I would like to either remove the "guest" option when logging in or require a password for it.  Any guidance will be appreciated.

---

### Post by Rex Bouwense on 2013-04-04
A quick search yielded this site;
[http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html)
It is talking about Ubuntu 12.04 but I believe that the procedure is the same.

A further search revealed similar results:
[http://ubuntuforums.org/showthread.php?t=1982467](http://ubuntuforums.org/showthread.php?t=1982467)

---

### Post by RyeMan on 2013-04-05
Thanks Rex, but for some reason, it isn't working for me (I've tried it several times).  If I type it in the terminal I get prompted for my pw but when I enter the 2nd line I get "command not found".

---

### Post by HiImTye on 2013-04-05
you likely don't have gedit installed. to verify, run one of:
```
apt-cache policy gedit | grep Installed
aptitude search ~igedit
```

if it's not installed, then replace the 'gedit' in the command for another editor - I believe 'leafpad' is the default editor for Lubuntu

---

### Post by Rex Bouwense on 2013-04-06
My error  (by omission).  Of course Leafpad is the default editor and the procedure works fine with Lubuntu 12.10.  I just tried it.  Thanks for pointing that out HiImTye.

---

### Post by RyeMan on 2013-04-06
Used leafpad, no problem...until I re-booted.  Now I get "The disk drive for UUID= (then a bunch of numbers) is not ready or not present, Press S to skip or M for manual recovery."  But neither option does anything.  It just shows the Lubuntu boot logo.  Using Puppy Linux right now.

---

### Post by Rex Bouwense on 2013-04-06
RyeMan what did you do?  I just repeated the procedure.  I am using Lubuntu 12.10 which requires you to use
```
gksudo leafpad /etc/lightdm/lightdm.conf
```
That will bring up lightdm config file in which you will type using leafpad

> allow-guest=false

Save and exit.
Type in the terminal
```
sudo restart lightdm
```
That will restart your computer with the guest login gone.

---

### Post by RyeMan on 2013-04-07
Not sure what happened. I didn't see any syntax errors. The added line was at the top instead of the bottom, would that matter?  I did it again and it works fine...thanks so much!

---

### Post by Rex Bouwense on 2013-04-07
Glad to be of assistance.  It should have been at the bottom.  All that matters is that your problem is solved.

---

