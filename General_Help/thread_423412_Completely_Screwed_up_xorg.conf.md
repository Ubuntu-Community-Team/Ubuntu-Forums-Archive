---
title: "Completely Screwed up xorg.conf"
date: 2007-04-25
forum: General Help
---

### Post by Luigi239 on 2007-04-25
I was trying to install a trackpad driver for my macbook (in fiesty), and part of that was to add a line to the xorg.conf file. So I did, restarted gnome, and now X will not start at all. I then tried to edit the file with nano edit, but the problem line was not there, so I stupidly deleted another line, which I thought would fix it, and didnt.

What I am asking, is if there is a way to create a new xorg.conf file, without doing the dpkg method, which asks you to select you video card, resolution, ext. I tried that before, and none of the Intel ones are on there, so I got lost.

Any help is appreciated, please.

---

### Post by RedSquirrel on 2007-04-25
In my opinion, using

```
sudo dpkg-reconfigure xserver-xorg
```

is still probably your best option.

Which version of Intel graphics do you have? I think i810 is the driver you would choose for a lot of those Intel ones.

---

### Post by dreadlord_chris on 2007-04-26
> **Luigi239 said:**
> I was trying to install a trackpad driver for my macbook (in fiesty), and part of that was to add a line to the xorg.conf file. So I did, restarted gnome, and now X will not start at all. I then tried to edit the file with nano edit, but the problem line was not there, so I stupidly deleted another line, which I thought would fix it, and didnt.

What I am asking, is if there is a way to create a new xorg.conf file, without doing the dpkg method, which asks you to select you video card, resolution, ext. I tried that before, and none of the Intel ones are on there, so I got lost.

Any help is appreciated, please.

just reconfigure xorg the normal way:
```

sudo dpkg-reconfigure xserver-xorg

```
and choose **vesa** as your video driver - this will allow you to log into your desktop. From there you can figure which Intel GPU you have and the proper driver to install.

---

