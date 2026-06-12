---
title: "Concerning booting and xserver-xgl"
date: 2008-01-28
forum: General Help
---

### Post by Bontrey on 2008-01-28
First of all, is there a way to make the vista bootloader boot directly into Ubuntu instead of chaining to GRUB? I'm currently using easyBCD to edit the bootloader.

And second, compiz doesn't work for me unless I install xserver-xgl, but doing so makes my subsequent logins unable to play fullscreen games. When I try to launch the games, they either flash the screen black then do nothing, or logout my session.

---

### Post by pointone on 2008-01-28
What kind of video card do you use? If it's an ATI card, you can install the latest version of their graphics driver following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"), which allows use of the composite extension without Xgl.

---

### Post by Bontrey on 2008-01-30
I'm using an intel card. I commented out the 965 one in the compiz blacklist and got compiz to work as well as games, but my videoplaying still crashes.

EDIT: and that's WITHOUT installing xserver-xgl

And another thing is that videos worked when I ran compiz with xserver-xgl installed, ironically, but they were kinda messed up. Like, sometimes the top black border on a fullscreen video would have lines of a bunch of colors, and the frame-rate sometimes decreases.

---

### Post by Bontrey on 2008-01-30
bump..

---

### Post by Computer Guru on 2008-02-02
You can't entirely skip GRUB.  Just set the GRUB timeout to zero and it'll be as if EasyBCD boots directly to Ubuntu.

---

