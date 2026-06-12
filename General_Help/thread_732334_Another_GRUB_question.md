---
title: "Another GRUB question"
date: 2008-03-22
forum: General Help
---

### Post by daitheflu08 on 2008-03-22
I want both the 40 gig and 110 gig hard drives completely clean of any boot material or any data.  When I disconnect the 110 from the cpu, the pc won't boot.

What do I need to do?

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf384f384

Device Boot Start End Blocks Id System
/dev/sda1 13996 14593 4803435 5 Extended

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74063980

Device Boot Start End Blocks Id System
/dev/sdb1 1 48479 389400576 7 HPFS/NTFS
/dev/sdb2 * 48480 90444 337083862+ 83 Linux
/dev/sdb3 90445 91201 6080602+ 5 Extended
/dev/sdb5 90445 91201 6080571 82 Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x353d353d

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 4865 39078081 7 HPFS/NTFS
daniel@daniel-desktop:~$

---

### Post by teryowen on 2008-03-22
In your BIOS boot priority set it to the 750GB hard drive.

---

### Post by Antarctica on 2008-03-22
First off, how's this related to GRUB?  If you want to simply format the two drives, just pop in the Live CD and go to Applications, Accessories, Terminal and type ```
gparted
```  Then you'll be able to format and partition your hard drives from there.  Just remember to unmount them first if necessary.

---

### Post by daitheflu08 on 2008-03-22
The reason it is a grub bootloader issue is when I disconnect the 120 drive from the cpu and turn on the pc.  It says GRUB error 21 or 23.

So first I need to get my bootloader straight before I format any drive entirely.

---

### Post by teryowen on 2008-03-22
so just install grub on the 750GB hard drive.

do this in terminal:

sudo grub
root (hdX,Y)
setup (hdX)
quit

where X is the hard drive number starting with 0 being the 1st hard drive 1 being the 2nd and 2 being the 3rd
where Y is the partition number oh where linux is on starting with 0 being the 1st partition 1 being the 2nd partition and so on.

so for you i think this is what you should do
```

sudo grub
root (hd1,1)
setup (hd1)
quit

```

so now the computer will us ethe grub which is on the 2nd hard drive and on the 2nd partition of that hard drive.

---

### Post by daitheflu08 on 2008-03-22
I can't get the root command to work heres what it says:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd1,1)

Error 22: No such partition

grub>

---

### Post by teryowen on 2008-03-22
ok try "root (hd0,1)" or "root (hd2,1)" instead of "root (hd1,1)"

---

### Post by daitheflu08 on 2008-03-22
grub> 

grub> root (hd0,1)

Error 22: No such partition

grub> root (hd2,1)

grub> 



I'm assuming that hd2,1 actually worked now what command for the setup

---

### Post by daitheflu08 on 2008-03-22
ran setup hd2 and everything went succesfully

---

### Post by daitheflu08 on 2008-03-22
Next update:

everything has gone to hell, I get the boot screen to select windows or linux but when I choose windows it says MBR boot loader does not exist (or something like that) and linux says partition does not exist.

the 750 drive was split down the middle with windows and linux on it.  I did this using windows, I think this isn't gong to work and I'm going to have to use that command in your quote.

Just wondering does that format the drives into Linux format or is it just removing all the data?

---

### Post by teryowen on 2008-03-22
its because the locations which are specified in the menu.lst file on the 750 gb hard drive are wrong we just need to specifiy the correct ones. 

so next time you see the grub menu

press 'e' over the linux selection
then 'e' again over the root.... part
and edit the root part to have hd2,1
after editting press enter and then 'b'
this will let u boot into ubuntu from there make the change permanent, do this by editing the /boot/grub/menu.lst file where you see the ubuntu root lines make sure they have hd2,1 and as for the windows it sholuld have hd2,0

---

### Post by daitheflu08 on 2008-03-22
Well thanks for tryin I just wiped out my computer.  It's no biggie anyway.

---

### Post by teryowen on 2008-03-22
haha alright, well this was fixable... but hey starting from scratch is always good too.

---

