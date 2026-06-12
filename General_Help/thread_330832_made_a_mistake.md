---
title: "made a mistake"
date: 2007-01-03
forum: General Help
---

### Post by fracktor on 2007-01-03
I am currently running Ubuntu Edgy and I made a huge mistake somewhere after following these directions. --> [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)
Now when I boot my pc, it starts to load the Ubuntu load screen then it stops and goes to the following message on my screen...

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

I tried to boot in to the safe mode option as well, and the same message comes up. I am able to boot to the Ubuntu cd and get to a shell, but I am unsure as to how I can undo the changes.

Any help would be much appreciated.

---

### Post by raul_ on 2007-01-03
I think your filesystem is ext2 and not ext3. Load the Live CD, then type this in the terminal:

```

sudo mount <device here> /mnt
sudo nautilus

```

And undo the changes from there. Check if your file system is really ext3

---

### Post by fracktor on 2007-01-03
Thanks for the quick reply, I'll give that a try.
I also found this in another forum here, do you think this may be a possible resolution?

sudo mkinitramfs -o /boot/initrd.img-2.6.17-10-generic 2.6.17-10-generic
sudo update-grub
sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic

---

### Post by raul_ on 2007-01-03
My solution is based in the same error i had :mrgreen: i didn't remember i hadn't converted my file system to ext3 from ext2 (this is system is sum of update since i used Hoary ;) )

When you have to hard reboot, does your system always run fsck? If so, you're probably using ext2

---

### Post by fracktor on 2007-01-03
How could I tell if it runs fsck?

Do I need to use a Live cd in order to issue those commands. I booted to the installation cd and I can get to a shell, but none of those options are available. If I use sudo it says its unknown command.

---

### Post by raul_ on 2007-01-03
As far as I know, you'll need a Live CD to do those options. I hope you have broadband ;)

---

### Post by fracktor on 2007-01-04
I download the live cd and I am now booted into it.
I ran
sudo mount <device here> /mnt

I was able to mount the drive, but when running
sudo nautilus
all it does is open a folder.

I can see in device manager it is showing the file system as ext3.

I cant find out how to access my harddrive with Ubuntu installed. If I try goin into mnt, i get permission denied.

---

### Post by raul_ on 2007-01-04
```

sudo nautilus

```
 
and then browse to /mnt

---

### Post by fracktor on 2007-01-04
awesome.

sorry, I just switched to ubuntu a few weeks ago from XP, so I am still getting used to this.

I appreciate your help raul_

---

### Post by raul_ on 2007-01-04
Glad you solved it ;)

---

