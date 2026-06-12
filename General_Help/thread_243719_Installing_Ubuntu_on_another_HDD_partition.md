---
title: "Installing Ubuntu on another HDD partition?"
date: 2006-08-25
forum: General Help
---

### Post by Bubblemanx on 2006-08-25
Hello, i have windows vista on this laptop and i was wondering if i could install Ubuntu on the other partition i made just not sure how to make ubuntu install on the partition with nothing on could any one help thanks :rolleyes:

---

### Post by VirtuAlex on 2006-08-25
As far as I remember the installer should give you an option to use available free space. If not, choose manual partitioning and make at least two partitions - one for swap and one for root. If you have plenty of space separate home partition also would be good for you.

---

### Post by Bubblemanx on 2006-08-25
ok thanks il try that :)

---

### Post by az on 2006-08-25
If the other partition is already set, it will not be shown as free space.

If you still want to take advantage of the automatic partitioning, start the install, chose manual partitioning and delete that partition.  The go back and you should then see the FREE SPACE option.

---

### Post by VirtuAlex on 2006-08-25
on the second read... yes, if partition is already there, then manual partitioning is the only option. Either delete it and go back to default partitioning, or resize, reuse and set the mount point by hands. Depending on your level of cluelessness.

---

### Post by Bubblemanx on 2006-08-25
How do i make it boot up with the other oporating system :-o

---

### Post by VirtuAlex on 2006-08-25
and under "other" operating system you mean...?
In general ubuntu will automatically install linux boot loader called Grub. It will (hopefully) detect all operating systems installed on the computer and make an entry in the boot menu. So when you start your computer you'll see the menu giving you a choice what to boot.

---

### Post by Bubblemanx on 2006-08-25
Hmmm have 2 oporating systems installed but i dont see menu giving you a choice what to boot :sad:

---

### Post by VirtuAlex on 2006-08-25
and what it boots by default, vista, ubuntu, nothing at all?

---

### Post by Bubblemanx on 2006-08-25
boots up with ubuntu

---

### Post by az on 2006-08-25
> **Bubblemanx said:**
> Hmmm have 2 oporating systems installed but i dont see menu giving you a choice what to boot :sad:

By default, it should be displayed.  Does it say "press escape to reveal grub menu" or something?

In that case, press escape...

---

### Post by Bubblemanx on 2006-08-25
yes but then when i press esc all the opions it has is 
Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel Ubuntu, kernel (recovery mode)
Ubuntu, memtet86+

thats all the opions :eek:

---

### Post by thibeaz on 2006-08-25
yeah I had that problem with that on my parents computer when I installed the ubuntu operating system but I solved that by reinstalling windows first and then ubuntu on a seperate hard drive. I did that because I felt like it and my parents never had anything that they needed on it anyway.

---

### Post by VirtuAlex on 2006-08-25
first make sure your windows partition is still there:
```
sudo fdisk -l
```
if it is you need to edit /boot/grub/menu.lst and add the entry at the end manually.
search the forums for this because vista may behave differently, but for my xp the entry looks like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by Bubblemanx on 2006-08-25
thanks but im a bit new to ubuntu where do i type that code in :oops:

---

### Post by VirtuAlex on 2006-08-25
open terminal Applications>Accessories>Terminal
and type it there
to edit a grub menu file use
```
gksu gedit /boot/grub/menu.lst
```
do not edit anything else, just add an entry to the end of file and search first forums if XP entry works for vista

---

