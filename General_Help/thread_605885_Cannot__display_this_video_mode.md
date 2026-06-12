---
title: "Cannot  display this video mode"
date: 2007-11-07
forum: General Help
---

### Post by muppett on 2007-11-07
Hello

I got this same problem when doing a fresh install of 7.10. When it boots it just goes into this black screen with that error message, so i can't get into ubuntu at all.

So i installed 7.04 and upgraded to 7.10. Everything was working i restarted system and it worked, it then prompted me to download some drivers, which i did, and restarted. On restart this same black screen with error message came up.

Any ideas?

I'm a bit of a newbie, so please keep the lingo down a notch haha.

Thanks

---

### Post by taurus on 2007-11-07
Press <Ctrl><Alt>F2 to get into a console.  Log in with your username and password.  Then, reconfigure X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

When you are done with it, press <Alt>F7 to get back to the GUI login screen.  Now, restart your X again with <Ctrl><Alt>Backspace.

What video card do you have anyway?

---

### Post by muppett on 2007-11-08
Yes! I got into ubuntu!

It says its running on proprietary drivers and is prompting me to install an ATI driver, this seemed to screw it up before. Any ideas?

Thanks alot

EDIT: Its a ATI RADEON X1300

It only allows me to use 800 resolution else it starts complaining.

---

