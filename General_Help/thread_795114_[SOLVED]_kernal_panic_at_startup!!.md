---
title: "[SOLVED] kernal panic at startup!!"
date: 2008-05-15
forum: General Help
---

### Post by boyce1 on 2008-05-15
ok, i just installed a splashscreen from gnome-look, the usplash fingerprint theme.

followed instructions fine, install went perfect.

powered off computer, ive had problems with shutdown before due to some ACPI problems, so i generally have to hit the powerbutton to fully turn off. however, this time some more messages were appearing, but i turned off anyway.


rebooted computer, except the splash screen didn't appear, just a black screen. i reset, and went into the grub booter and had a look, i had added a command in the boot line 'vga=791', as listed in the instructions.

I took this out, and did a manual boot by pressing 'b'.

This immediatly came up with the error "kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0).



Now i am absolutely stuck. :(

---

### Post by boyce1 on 2008-05-15
...anyone?

---

### Post by boyce1 on 2008-05-15
sorry to bump, but im really stuck :S

---

### Post by Xoanan on 2008-05-15
Hi there!

I had a similar issue when I tried to install Gutsy on my mother's pc.  I eventually did a reinstallation of Xubuntu on it on another partition. When I did that, I found I had choices of OS's I could boot. 

> kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

My message was slightly different; it could not find the root at all.  This one indicates it can't install the root on that block(or it can't find a partition to place it. 

What are your specs on the pc?  Does it have another OS on it?

---

### Post by boyce1 on 2008-05-15
hey :)

i havn't got any other OS's on my hdd, 7.10 gutsy is the only one.

I have a ASUS m2n4-sli motherboard
nvidia 7600gt
2gb of ram

I can get into a livecd boot, if thats any help

---

### Post by boyce1 on 2008-05-15
...?

---

### Post by Xoanan on 2008-05-15
That might help; Let me see if I can find some more info that may be helpful to you so I can send it to you.  Give me some time on it though.

---

### Post by Xoanan on 2008-05-15
Try this thread

[http://ubuntuforums.org/showthread.php?t=787658&highlight=kernel+panic]("http://ubuntuforums.org/showthread.php?t=787658&highlight=kernel+panic")

---

### Post by chrisccoulson on 2008-05-15
This panic is because your root filesystem cannot be found. Most likely this is because GRUB is pointing to the wrong place. You are going to have to fix this from the live CD.

First of all boot in to the live CD then mount your root filesystem. To do this:
```
sudo mkdir /media/target
sudo mount -t ext3 /dev/sdxx /media/target
```
..where /dev/sdxx is the device node for your root filesystem (if you know it). If you need help identifying it, please post the output of:
```
sudo fdisk -l
```
...and I might be able to help.

Once the root filesystem is mounted, you'll need to open up your /boot/grub/menu.lst (which will be /media/target/boot/grub/menu.lst). There will be a line beginning with '# kopt', which will look something like this:
```
# kopt=root=UUID=4a810ba8-bfc5-4a54-b9f3-e7588805b872 ro
```
...this is an example from my menu.lst. It might also use device node instead of UUID, like this:
```
# kopt=root=/dev/sda1 ro
```

Basically, the 'root=' bit needs to point to your root filesystem. You can use the device node or UUID (like in the 2 examples I gave). To find the UUID's of all your volumes, type this in a terminal:
```
sudo blkid
```
If you are unsure about the output, then post it here.

Note also that the 'root=' option should also point to the root filesystem as identified in your /etc/fstab (or, /media/target/etc/fstab from the live CD). Please have a look in your fstab and make sure that they both match up. Again, if you are unsure, post your fstab here along with your menu.lst and the output of 'sudo blkid'.

Once you have fixed your menu.lst, then you need to run update-grub (from inside your mounted environment). To do this:
```
sudo chroot /media/target
sudo update-grub
```

---

### Post by boyce1 on 2008-05-18
thank you very much, i solved the problem :)

i managed to actually boot into my computer, by adding some lines in the grub startup (forgot which ones sorry)

once i was in my computer, i fixed my fstab config, which allowed me to boot normally :D


thanks again :)

---

### Post by kevdog on 2008-05-18
chrisccoulson

Nice bit of help.  Very informative.

---

