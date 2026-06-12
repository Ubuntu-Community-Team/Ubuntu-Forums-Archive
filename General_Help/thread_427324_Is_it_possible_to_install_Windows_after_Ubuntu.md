---
title: "Is it possible to install Windows after Ubuntu?"
date: 2007-04-29
forum: General Help
---

### Post by Jump on 2007-04-29
I tried this back during the Hoary days but it was recommended to load Windows first then Ubuntu. This worked for me with very little hassle. It's also allowed me to put xp, vista and feisty on a new laptop.

My question is for a friend who recently allowed me to install feisty on desktop. He's a completely new to linux so I did all the setup with beryl, dual monitors, his logitech mouse and keyboard, etc. The problem is now he wants to add windows back as a dual boot so he can plays certain games. I'm wondering whether I can install XP on a new partition and then update grub to boot from both OS. Is this possible or does Windows for some reason insist on being the first partition? I seem to recall that being the problem I had back when I used Hoary.

---

### Post by cas_ on 2007-04-29
Some time ago I've tried installing Win XP as a second OS (Ubuntu had been there already). Unfortunately Windows' installer was unable to even start - it gave me a black screen. I had to remove Linux partition to get it working.

---

### Post by Rui Pais on 2007-04-29
Windows install will overwrite grub loader at MBR. You will need it to recover.
here how:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 
Or here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

hth

---

