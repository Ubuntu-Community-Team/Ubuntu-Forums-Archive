---
title: "New kernel(?) does not show up in bootloader"
date: 2007-08-30
forum: General Help
---

### Post by ArtF10 on 2007-08-30
I think this is **kernel** related although I may be way off.

```
uname -r gave me
``` 
2.6.20-15-generic

I was installing my video card drivers for Xubuntu and after entering this line
```
sudo apt-get install linux-generic
``` and got a message saying something about 2.6.20-16...something that looked like that, but I'm not sure what.

However, upon rebooting I do not see it in the GRUB menu...I have Ubuntu and Xubuntu dual booting and the 2 kernels show up for Ubuntu, HOWEVER they don't for Xubuntu.  Now, my GRUB bootloader screen is full so maybe that has something to do with it?  I had Xubuntu installed on hda1, formatted hda1 and then re-installed Xubuntu on hda1...they new Xubuntu(upon reinstallation) kernel shows up as the default and under "Other Operating Systems" I see the old and new kernels for Ubuntu.  Right beneath them, I ALSO see the **OLD kernels from the removed Xubuntu**<------Is there a way to remove **these**?  Could **these** (occupying the screen) be the reason why the new Xubuntu kernel (for the reinstalled Xubuntu) is not showing up in the bootloader?

Is this a problem or am I missing something?

---

### Post by ArtF10 on 2007-08-30
Here's the boot screen I'm talking about(same screen....3 views):

[http://img98.imageshack.us/img98/8966/0000031de3.jpg](http://img98.imageshack.us/img98/8966/0000031de3.jpg)
[http://img98.imageshack.us/img98/5339/0000032oe7.jpg](http://img98.imageshack.us/img98/5339/0000032oe7.jpg)
[http://img183.imageshack.us/img183/3430/0000033zp4.jpg](http://img183.imageshack.us/img183/3430/0000033zp4.jpg)

---

### Post by rsambuca on 2007-08-30
In xubuntu, open up Synaptic and search for "linux-image".  Which ones do you have installed?

---

### Post by ArtF10 on 2007-08-30
Package - Installed version
linux image 2.6.20-15-generic    -   2.6.20-15.27
linux image generic   -   2.6.20.15.14

Those are the only 2 that show up....how do I know that I have the lastest one running in the bootloader?  All that ```
uname -r
``` gives me is 2.6.20-15-generic.

Also, how do I get rid of those bottom 2 or 3 entries? menu.lst?  I've never edited it before.

---

### Post by rsambuca on 2007-08-30
You only have the one kernel installed, so that is why only one shows up in your grub.  To delete those other entries from your grub, just```
gksudo gedit /boot/grub/menu.lst
```

Delete the entries you don't want, or put a # sign in front of the lines.  You have to do this for the lines starting:

title
root
kernel
initrd

---

### Post by ArtF10 on 2007-08-30
So is the kernel installed the latest version?  OR has that somehow not ended up showing up in the bootloader?

Thanks for the menu.lst tips.  I;'ll remove some lines.

---

### Post by rsambuca on 2007-08-30
If you want to know if you are up-to-date, open a terminal```
sudo apt-get update
sudo apt-get upgrade
```

---

