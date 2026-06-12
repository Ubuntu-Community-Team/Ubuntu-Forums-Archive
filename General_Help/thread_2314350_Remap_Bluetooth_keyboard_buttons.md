---
title: "Remap Bluetooth keyboard buttons?"
date: 2016-02-20
forum: General Help
---

### Post by Terence_Eden on 2016-02-20
Is there any way to tell Ubuntu that when Key $X is pressed on the *external* keyboard, do Action $Y?

I have a Bluetooth "selfie" dongle - the AB Shutter 3.  

I can pair the dongle to my Ubuntu laptop.  When I press the button, it sends the Volume Up command (key 123).

I don't want do change the behaviour of my laptop's volume up key.

Some things I found which didn't work:

  
[LIST]
[*]I don't want to [change the language of the external keyboard]("http://superuser.com/questions/75817/two-keyboards-on-one-computer-when-i-write-with-a-i-want-a-us-keyboard-layout") using setxkbmap. 
[*]Using xkb [seems to remap keys on all keyboards]("https://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04/347382#347382"). 
[*]xinput can [remap mouse buttons but not keyboard keys]("https://wiki.ubuntu.com/X/Config/Input"). 
[/LIST]
  
Any ideas? Ubuntu 14.04.4 LTS. Thanks.

---

### Post by ik-0 on 2016-02-20
see the multiple keyboard options of xkb: [https://wiki.archlinux.org/index.php/X_KeyBoard_extension#Multiple_keyboards](https://wiki.archlinux.org/index.php/X_KeyBoard_extension#Multiple_keyboards)

---

