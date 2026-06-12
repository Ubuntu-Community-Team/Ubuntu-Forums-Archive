---
title: "Change my Xorg.conf file using live CD"
date: 2007-02-10
forum: General Help
---

### Post by mattgaunt on 2007-02-10
heya

I tried installing fglrx drivers on my laptop and the X server fails everytime, anyone got any ideas??

I reckon i hav to mount something somewhere but i cant see what

Any help would be great

matt

---

### Post by taurus on 2007-02-10
You can either 

1.  Boot into recovery mode and reconfigure your X again with
```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

or 

2.  Copy the /etc/X11/xorg.conf from the LiveCD to your harddrive, replacing the broken one.
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming /dev/hda1 is where Ubuntu, /, is located.)
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
sudo umount /mnt/ubuntu
```

---

### Post by mattgaunt on 2007-02-10
Yeah i cant find out how to get my hard drive mounted in the live CD for sum reason i cant see which bit i should be mounting

And how do i get into recovey mode??

Sorry im still a bit of a noob at this sorta stuff

Matt

---

### Post by taurus on 2007-02-10
From a terminal, what's the output of this command?

```
sudo fdisk -l
```

When you first boot your machine (without the LiveCD), you will get to the GRUB screen and you have three seconds to press the Esc key to see the menu.  The recovery mode should be the second option on that menu.

---

### Post by mattgaunt on 2007-02-10
Thanks for the help i used the recovery mode to reset it and its started up, last time i try and install fglrx on that computer

Thank you so much for the help

Matt

---

