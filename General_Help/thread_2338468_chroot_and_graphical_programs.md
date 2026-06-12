---
title: "chroot and graphical programs"
date: 2016-09-28
forum: General Help
---

### Post by Jim_Lawrence on 2016-09-28
I have followed all of the instructions on this page to try and get a graphical program running from inside a chrooted environment

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

The only difference is that I substituted xenial for trusty.

The installation went fine and no complaints in the terminal at issuing any of the commands.

However, when I get to the part where is says I can run firefox in a chrooted environment with this command:

gksudo chroot /var/chroot firefox -DISPLAY=:0.0
the firefox window does not come up. A window comes up asking for my administrative password, which I enter, and then nothing, it just exits to a command prompt with no messages.

I'm hoping there is a simple answer to this, thanks for any help



[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by TheFu on 2016-09-29
Don't think it is possible.
a) don't run GUI programs as root.
b) chroot doesn't mean the X/Server DISPLAY is available and definitely NOT to a different, untrusted, userid.  You'll need to setup all the X/client libraries inside the chroot if there is any hope of this working.  X is inherently non-secure due to design choices made ... 40-ish years ago (udp).

In 16.04, you could use **firejail**. It uses "containers" and definitely does work with browsers and other GUI programs as non-priviledged users. It is in the repos and has default settings for chromium/bash/firefox and 50 other programs.

---

### Post by Jim_Lawrence on 2016-10-15
Thanks for the info! I tried firejail and it works great.

---

### Post by TheFu on 2016-10-16
Please mark thread as "solved", to help out others.
Firejail is relatively new and not everyone knows about it yet.  It isn't perfect, but it pretty awesome for what it does.

---

