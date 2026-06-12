---
title: "Cannot boot windows XP"
date: 2007-01-17
forum: General Help
---

### Post by keke20 on 2007-01-17
This is what i get when i try to boot:
[http://img458.imageshack.us/my.php?image=winxpboottw5.jpg](http://img458.imageshack.us/my.php?image=winxpboottw5.jpg)

It just doesnt do anything after that.

Anyone know how i can get windows XP working again?

---

### Post by DerHesse on 2007-01-17
looks like your menu.lst in /boot/grub/ is messed up. You must have changed something recently, e.g. adding/removing a disk or partion?

You could try to edit as follows:

$ sudo gedit /boot/grub/menu.lst 

**search for something like:**

[I]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title           Microsoft Windows XP Professional
root            (hd[COLOR="Red"]0,2[/COLOR])
savedefault
makeactive
chainloader     +1[/I]

duplicate this part and copy it several times underneath.
now change the red marked numbers. one nuber up an down.
save and reboot. Try the different entries in the boot menu until one of them fits.



Or you could just copy and paste the result of what you get when you type:
$ mount

---

### Post by bodhi.zazen on 2007-01-17
> **keke20 said:**
> This is what i get when i try to boot:
[http://img458.imageshack.us/my.php?image=winxpboottw5.jpg](http://img458.imageshack.us/my.php?image=winxpboottw5.jpg)

It just doesnt do anything after that.

Anyone know how i can get windows XP working again?

Can you post the stanza for windows from /boot/grub/menu.lst and the output of ```
sudo fdisk -l
```This is better then "guessing" your windows partition if you do not know what it may be ....

I think all you need to add is "boot" like this:

> title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
**boot**

---

### Post by keke20 on 2007-01-18
First i tried to do FIXMBR for windows, but then i couldnt launch any OS anymore, only from the CD, so i just re-installed Windows XP and removed ubuntu. I dont think i try to install ubuntu in the future anymore, it just has too much problems... Thanks for your help anyways.

---

### Post by bodhi.zazen on 2007-01-18
Sorry you had so much trouble :(

You may want to play with the live CD for a while.

If you would like help, come on back any time :p

---

