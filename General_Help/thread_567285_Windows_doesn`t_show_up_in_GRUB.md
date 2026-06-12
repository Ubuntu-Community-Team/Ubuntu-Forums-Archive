---
title: "Windows doesn`t show up in GRUB"
date: 2007-10-04
forum: General Help
---

### Post by Naatan on 2007-10-04
Help! I just installed 7.10 and expected my windows installation to show up as an option in GRUB like it did with 7.04..

but it aint there..... :(

Can anyone help me out???

---

### Post by tubasoldier on 2007-10-04
Its fairly easy to add it back in.

> sudo gedit /boot/grub/menu.lst

Then make your way to the bottom of the file. and add

> title		Windows 95/98/NT/2000/XP
root		(hd0,0)
makeactive
chainloader	+1


Of course making sure that the root entry is the correct partition that windows is in.
Of you want Windows to be the default boot entry you can add "savedefault" under the chainloader line. 

Good Luck.

---

### Post by Naatan on 2007-10-04
sweetness, that did it! Thanks :)

---

### Post by P3RH4PS on 2007-10-04
This is exactly what I need to do also but I was wondering about:

> Of course making sure that the root entry is the correct partition that windows is in.

How would I determine this...  I know this is an easy question and I'm relatively certain it has to do with primary/secondary master/slave, but I want to double check because I am consumed with the fear of breaking my computer.

Yay!  Thanks!

---

### Post by P3RH4PS on 2007-10-04
Ok, then I did that and now I have two Ubuntu and two Ubuntu (recovery mode)s in the grub menu, which I don't find to be a huge deal, and my XP option is there too (Yay!), but my NTLDR is missing.  Is there an easy way to bring that back without interfering with Ubuntu?

---

### Post by P3RH4PS on 2007-10-05
I fixed it yay thanks!

---

### Post by willz06jw on 2007-10-15
This worked for me too ... why is this bug appearing?  Every time they do a kernel update I have to redo this fix.  I hope they find it before launch in 3 days!

Will

---

### Post by Buzzdee on 2007-12-27
I have the same problem.
I had Gutsy installed for a while. Then I added Windows and restored GRUB by doing
```
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
```
after mounting my root partition.
I have only one SATA-2 drive installed, partitioned to 
sda1 ext3
sda3 ntfs
sda5 swap
while the Device Manager (System -> Preferences) seems to refer to the entire drive as "sda2", according to the size of the individual devices. 

Now my question is, if I do
```
title Windows 95/98/NT/2000/XP
root (hd0,0)
makeactive
chainloader +1
```
won't this give me just another linux entry (as hd0,0 was the result above) called "Windows"?
And how do I find the reference of my Windows partition?

Thanks a lot in advance, 

Bastian

---

### Post by Buzzdee on 2007-12-28
```
title Windows 95/98/NT/2000/XP
root (hd0,2)
makeactive
chainloader +1
```
gave me a working Windows. This will unfortunately be overwritten the next time a new kernel is installed. 
```
sudo grub-update
``` doesn't find the windows partition, although it can be read in Nautilus (SATA-2, NTFS formatted), i.e. drivers are there. 
Could someone please help me?

System info:
Gutsy Gibbon 64bit, Thinkpad T61p with a Core2Duo, SATA-2 160 GiB formatted 
sda1 ext3 ubuntu
sda3 ntfs vista
sda5 swap

---

