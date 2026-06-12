---
title: "wubi help"
date: 2007-04-02
forum: General Help
---

### Post by offbow on 2007-04-02
Hi
I am new to the forum and i need some help.
I have just installed ubuntu with wudi but when it starts i have no screen image. 
All that happens is i hear sounds of some bongos so i guess this is the login screen.
So i type in my username and password and press enter, then i hear some more bongos sounds.
I think there is some thing wrong with the graphics driver(nvidia geforce 6800 xt).
one of the lines of code at startup of ubuntu says "fail" in red.

Any help welcome:) 
  offbow

---

### Post by tuxcantfly on 2007-04-02
ctrl-alt-f1

login with your username and password

type this in the command line:

```
sudo nano /etc/X11/xorg.conf
```

an editor should pop up

find the line that says "nv" (it'll be under some section that says driver)

change that to "vesa"

ctrl-x

y

enter

```
sudo /etc/init.d/gdm stop
```

```
sudo /etc/init.d/gdm start
```

hope that helps

---

### Post by mute33 on 2007-06-08
hello,
I just installed wubi on my windows xp system and I am having some problems.
I am not really familiar with this so maybe i'm doing something wrong. But I get error messages
like "failed to set xfermode" "cant read superblock X version" "No RAID disks". I don't know what
any of this means so if anyone can help me in fixing this it would be greatly appreciated.
Thanks for all the help.
mute33

---

### Post by mute33 on 2007-06-11
That doesn't help me at all i type that in and some menu comes up on the bottom 
and i cant get into it theres nothing about drivers or anything like that. So idk im really not familiar
with this at all. I keep getting error messages like "failed to set xfer mode" "No RAID disks" something 
about my graphics card. So anymore help would be appreciated.

Thanks.

Mute33

---

