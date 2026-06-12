---
title: "Help!"
date: 2007-10-20
forum: General Help
---

### Post by bash on 2007-10-20
Ok I got a huge problem now. Lovely Vista installer did a quick format of my / and /home partition instead the one I told him. Just terrific. The whole thing took only 3 secs, so I dont think that anything was really deleted off it, but now my LiveCD gparted tells me that its just "empty" space. 

Any way I can get my data of that and or restore the partition table they way it was? Help would be really appreciated.

---

### Post by ddrichardson on 2007-10-20
Yes, testdisk can. You can use the [System Rescue CD]("http://www.sysresccd.org/Main_Page") to boot and run testdisk

---

### Post by Pedro0727 on 2007-10-20
ok try this!

insert the Ubuntu live cd. then restart the PC

boot on CD
after the GUI of ubuntu is loaded 
opern the terminal

type the following:

sudo grub
> root (hd0,0)
> setup (hd0)
>quit
its Done!

Note:
(hd0) means the HDD/harddisk
and the 0 after the comma is the partition # ok.. 
enter the correct partition, where the Ubuntu installed..

---

### Post by ddrichardson on 2007-10-20
> **Pedro0727 said:**
> ok try this!

insert the Ubuntu live cd. then restart the PC

boot on CD
after the GUI of ubuntu is loaded 
opern the terminal

type the following:

sudo grub
> root (hd0,0)
> setup (hd0)
>quit
its Done!

Note:
(hd0) means the HDD/harddisk
and the 0 after the comma is the partition # ok.. 
enter the correct partition, where the Ubuntu installed..
No don't do that, yet. It wont help, sorry - the OP has lost the two partitions not just the grub config. Do that after testdisk restores the partitions.

---

### Post by bash on 2007-10-20
Well got mixed results with testdisk. It restored my home and root partition nicely. Lost my two Luks encrypted ones though. But didn't really rely on them so its not all that bad. Important thing was to get my home partition back.

And know the Grub config trick. But as ddrichardson said that wouldn't have helped at that point.

---

### Post by ddrichardson on 2007-10-20
Good to hear - I'm consistantly impressed by test disk - it restored an HP recovery partition that a friend of mine deleted off his laptop, so he could no longer reinstall windows.

---

### Post by bapoumba on 2007-10-20
Moved to "General Help".

---

### Post by bash on 2007-10-25
> **ddrichardson said:**
> Good to hear - I'm consistantly impressed by test disk - it restored an HP recovery partition that a friend of mine deleted off his laptop, so he could no longer reinstall windows.

Yeah. Never knew such a handy piece of software existed. I think it should be default on the Ubuntu Live CD. In case you need to recover on a box that doesn't have internet access.

---

