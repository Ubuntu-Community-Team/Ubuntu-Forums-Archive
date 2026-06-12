---
title: "Grub dual boot"
date: 2008-05-30
forum: General Help
---

### Post by DarkMadder on 2008-05-30
Hi,

I've been running Ubuntu for about a month, but recently decided that (sadly) I still need access to Windows XP for some programs I can't do without.

I have 2 hard drives in the computer (hd0 & hd1), Linux is installed to hd0 and hd1 is empty. For reasons too foolish and convoluted to go into here, I swapped the position of the hard-drive's sata cables on the motherboard (so now hd0 = free space, hd1 = linux) then I installed XP to hd0. Eventually I had the OS installed and updated and all my tools and applications in place. So I booted from the Ubuntu live CD and entered these commands:
```
sudo grub
grub> find /boot/grub/stage1
grub> root (hd1,0)
grub> setup (hd0)
grub> quit
```
I hoped that this would replace the MBR on hd0 and let me boot to Ubuntu located on hd1. It did not. I think the problem is that both operating systems expect to find themselves located on hd0... perhaps?

Since I had destroyed the Windows MBR I couldn't boot to either OS, so I swapped the positions of the sata cables back to how they were before (linux on hd0, windows now on hd1)

```
grub> find /boot/grub/stage1
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
This allowed me to boot into Ubuntu again so I then added the following to /boot/grub/menu.lst
```
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1
```

But when I select this XP entry from the Grub menu it hangs at "Starting Up..."

Is there any way I can recover my Windows installation and get both OS's dual booting without having to reinstall XP and all its applications and updates?


Thanks

---

### Post by ajgreeny on 2008-05-30
It may be necessary to change the menu.lst further, but to know anything more it will be easier if we can see the output of ```
sudo fdisk -l
``` in ubuntu's terminal.  This will give full details of the partition names for your OSs and may help.

---

### Post by meierfra. on 2008-05-30
Use this:

title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by DarkMadder on 2008-05-31
Thank you so much!
It's working perfectly now :)

---

