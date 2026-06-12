---
title: "deleted Win 8 partition, forgot to back up win8, help plz"
date: 2015-03-19
forum: General Help
---

### Post by FuVinatro on 2015-03-19
So hello guys, so as the title says, I am a n idiot. So basically what I did , was that when I  installed Ubuntu GNOME on my desktop, I deleted all other partitions, including the one with win 8 boot loader. I did'nt install any dual boot software. When I boot now, I am Welcomed with a black screen with a blinking cursor. Anyone know how to fix this?(I have win8 licence) Do I also have an immediate case of idiotica. edit: AH ****, my win8 product code is used

---

### Post by yancek on 2015-03-19
You will need to provide more detailed information.  If you cannot boot from the hard drive, boot the Ubuntu installation medium then open a terminal and enter the following:

```
sudo gparted
```

That should open a window showing the partitions on yoru  computer.  Post the output of that image here and someone should be able to advise you.

---

### Post by FuVinatro on 2015-03-19
How do I post it, and what do I post

---

### Post by oldfred on 2015-03-19
Take a screen shot when you have gparted open, and then using advanced editor attach that screen shot. Do not post in line. Some users have slow Internet.

 If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

You can also from terminal post this, but just copy & paste terminal output. If longer use code tags to preserve format and make it easier to use, # in advanced editor: 
sudo parted -l

 Code tags
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

