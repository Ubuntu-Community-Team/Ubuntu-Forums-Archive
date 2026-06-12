---
title: "PLEASE HELP--Installing Ubuntu to external drive- how to put GRUB on external drive"
date: 2007-01-24
forum: General Help
---

### Post by presbp on 2007-01-24
I have Ubuntu installed on a partition on my external hard drive.  When I go to the part of the install where I am manually editing the partition table I have a choice of /dev/sda (my internal drive) and /dev/sdb my external drive.  I've installed Ubuntu to the 2nd partition of my external harddrive and when it gets to the screen that asks me where I want to install GRUB the option that is there id (hd0)  How do I know what hd0 is and how do I know which hd number is my external drive??  Thanks.  Please Don't Look at this post and ignore it like the others I have posted about this.

---

### Post by Ramses de Norre on 2007-01-24
hd0 is hda, grub uses only numbers and starts counting from 0. Your second drive will probably be hd1.
Maybe it's easier to skip the grub install and perform it manually from a live disc or other install from the grub prompt or with grub-install. You've got far more options then.

---

### Post by presbp on 2007-01-24
so how do I go about installing grub manuall?.  I am typing this on the Ubuntu Live CD can i go to the terminal and type grub-install and how do I tell it then to install GRUB to my external hard-drive.  My goal is to have GRUB and ubuntu installed on my external harddrive so that when the drive is not plugged in it will automatically go to Windows and when it is plugged in I have the choice.    Thanks guys.

PLEASE DO NOT JUST OVERLOOK THIS POST>>PLEASE HELP THANKS

---

### Post by earlsven on 2007-01-24
Don't know if this is what you're after, surely you could just disconnect the internal drive whilst installing Ubuntu, then the install only has one option.

---

### Post by geek_Man on 2007-01-24
You can try going with the default, see if it works and if not, change it.

DON'T WORRY! WE WON'T IGNORE YOUR POST!!! ;)

---

### Post by bodhi.zazen on 2007-01-24
> **presbp said:**
> I have Ubuntu installed on a partition on my external hard drive.  When I go to the part of the install where I am manually editing the partition table I have a choice of /dev/sda (my internal drive) and /dev/sdb my external drive.  I've installed Ubuntu to the 2nd partition of my external harddrive and when it gets to the screen that asks me where I want to install GRUB the option that is there id (hd0)  How do I know what hd0 is and how do I know which hd number is my external drive??  Thanks.  Please Don't Look at this post and ignore it like the others I have posted about this.

Here is a basic guide on partitioning that review Linux (/dev/hda1) and gurb (hd0,0) numbering:

[http://www.ubuntuforums.org/showthread.php?&t=282018](http://www.ubuntuforums.org/showthread.php?&t=282018)

To manually install grub:

```
sudo grub
```

This brings up the grub prompt. You need to know your ubuntu root in grub speak, in your case (hd1,1) (second partition of second drive ; grub starts numbering at 0 )

At the grub prompt : ```
root (hd1,1)
setup hd0
quit
```

But, as geek_Man suggests you can take the default during your installation (hd0) and go with it ...

No reason to change the default unless you have a reason (AKA know what your are doing and why you want to change from the default).

How to grub: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

HTH 8)

---

### Post by Ramses de Norre on 2007-01-24
In reply to your PM: **sudo grub-install /dev/???** should work, with the right device node instead of the "???".
If that doesn't work like it should you can also try this:
```
sudo grub
root (hd?,?)
setup (hd?)
quit
sudo update-grub
```
But I'm not sure which number you'll need to fill in for the '?'... After root you need to specify the partition containing /boot/ and after setup the drive (or partition) to install grub to.
So use the first command if that works.

EDIT: I'm repeating others.. I went away and didn't refresh the page before I answered again, sorry ;)

---

