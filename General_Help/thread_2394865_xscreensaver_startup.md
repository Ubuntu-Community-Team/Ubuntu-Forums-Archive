---
title: "xscreensaver startup"
date: 2018-06-22
forum: General Help
---

### Post by larryrink on 2018-06-22
Please help me to learn how to get "xscreensaver" to startup automagically. I have it listed in the startup app but it fails to launch successfully. I want to get the daemon to launch and for it to run as it should.

---

### Post by ajgreeny on 2018-06-22
In your startup applications command box you need to use ```
xscreensaver --no-splash
```
That has always worked for me.

In future please use the default font when posting, not the huge font you used; a large font will not be noticed any quicker by forum users and is considered rather rude and demanding.

---

### Post by larryrink on 2018-06-23
I'm sorry about the size of my post. I will refrain from doing that ever again. I thank you for your advice and I copied and pasted it in my "startup" app but it still does not load the daemon that is needed.  I must be doing something wrong still. Any further advice will be tried.

I am sorry, but I am actually using Mint. I thought that the two are similar enough.

Thank you.

Larry

---

### Post by #&amp;thj^% on 2018-06-23
Can you first show us this:
```
locate screensaver.desktop
```
Paste back the result here.

---

### Post by larryrink on 2018-06-23
locate screensaver.desktop
/etc/xdg/autostart/mate-screensaver.desktop
/home/larry/.config/autostart/mate-screensaver.desktop
/home/larry/.config/autostart/xscreensaver.desktop
/usr/share/app-install/desktop/chocolate-doom:screensavers__chocolate-doom-screensaver.desktop
/usr/share/app-install/desktop/cinnamon-screensaver:cinnamon-screensaver.desktop
/usr/share/app-install/desktop/cinnamon:cinnamon-settings-screensaver.desktop
/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Screen-Saving-disable_xscreensaver.desktop
/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Screen-Saving-enable_xscreensaver.desktop
/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Screen-Saving-reinitialize_xscreensaver.desktop

---

### Post by #&amp;thj^% on 2018-06-23
Great Thanks I can see a few things that would interfere with xscreensaver not auto starting.
```
mate-screensaver.desktop
chocolate-doom:screensavers__chocolate-doom-screensaver
cinnamon-screensaver:cinnamon-screensaver
and others
```
And I just need to be sure you do infact have "xscreensaver" installed via:
```
apt policy xscreensaver
```
paste that back here also please.

---

### Post by Dennis N on 2018-06-23
since you have both mate screensaver and xscreensaver, you should probably disable the one you don't want to work from your startup applications. Otherwise they can conflict; for example the one which comes on first (I think) is the one that displays the visible screensaver (or a blank screen, perhaps). 

Note: mate-screensaver can display all the screensavers that xcreensaver can, so you probably don't need xscreensaver when using MATE.

---

### Post by #&amp;thj^% on 2018-06-23
> **Dennis N said:**
> 
Note: mate-screensaver can display all the screensavers that xcreensaver can, so you probably don't need xscreensaver when using MATE.

+1 That was going to be my next point. :)

---

### Post by larryrink on 2018-06-23
apt policy xscreensaver
xscreensaver:
  Installed: 5.34-2ubuntu1
  Candidate: 5.34-2ubuntu1
  Version table:
 *** 5.34-2ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by #&amp;thj^% on 2018-06-23
> **larryrink said:**
> apt policy xscreensaver
xscreensaver:
  Installed: 5.34-2ubuntu1
  Candidate: 5.34-2ubuntu1
  Version table:
 *** 5.34-2ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

So if you have read the above two posts it comes down to which one you wanted to use then. :)
Amusing you are using Mate then first try disabling one of them from the Autostart menu scroll to see and disable one or the other.
But your results from "locate screensaver.desktop" show very different from mine IE:
```
locate screensaver.desktop
/etc/xdg/autostart/xscreensaver.desktop

```
I would probably leave the mate screensaver checked in autostart.
Let us know if you need any more help here, as there is a couple of other things to try if this fails to work for you.

---

