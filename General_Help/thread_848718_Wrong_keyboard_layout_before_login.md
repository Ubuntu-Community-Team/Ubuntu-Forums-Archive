---
title: "Wrong keyboard layout before login"
date: 2008-07-03
forum: General Help
---

### Post by qwallis on 2008-07-03
This is probably something I have done while trying to solve another problem recently which I have resolved.

My partner complained that she couldn't login and I have discovered that the keyboard layout at the login screen is English (which I guess is the default setting), after login the correct keyboard map is assigned (German).

Luckly for me my password doesn't hit any of the different keys, or I wouldn't have been able to figure out what was going on.
I know it's a keyboard map issue because I **can** login to her account by swapping Y for Z in her password which is the only character affected.

How do I go about changing the keyboard map used before login?

---

### Post by Diabolis on 2008-09-22
Edit this file: **/etc/default/console-setup**

ex:
> # The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="es"
XKBVARIANT=""
XKBOPTIONS=""


[http://www.linuxquestions.org/questions/linux-newbie-8/cant-change-keyboard-layout-in-ubuntu-8.04-login-screen-637811/#post3133435](http://www.linuxquestions.org/questions/linux-newbie-8/cant-change-keyboard-layout-in-ubuntu-8.04-login-screen-637811/#post3133435)

Or

also give a look to your xorg.conf file **/etc/X11/xorg.conf**

> 
OK, I fixed it configuring /etc/X11/xorg.conf:
in Section "InputDevice" I added:
  Option "XkbModel" "pc105"
  Option "XkbLayout" "es"

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/46046/comments/11](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/46046/comments/11)

---

### Post by sarthorks on 2010-02-08
> **Diabolis said:**
> Edit this file: **/etc/default/console-setup**

ex:


[http://www.linuxquestions.org/questions/linux-newbie-8/cant-change-keyboard-layout-in-ubuntu-8.04-login-screen-637811/#post3133435](http://www.linuxquestions.org/questions/linux-newbie-8/cant-change-keyboard-layout-in-ubuntu-8.04-login-screen-637811/#post3133435)

Or

also give a look to your xorg.conf file **/etc/X11/xorg.conf**


[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/46046/comments/11](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/46046/comments/11)

Hey thanks! It worked for me too! The console-setup file had XKBLAYOUT="in" instead of "us". I had explicitly edited xorg.conf and added a section on Keyboard and put XkbLayout as "us", but it hadnt worked. So i guess console-setup was the more important file.

---

