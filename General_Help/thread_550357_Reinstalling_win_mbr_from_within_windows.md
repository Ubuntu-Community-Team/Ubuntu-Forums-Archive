---
title: "Reinstalling win mbr from within windows"
date: 2007-09-13
forum: General Help
---

### Post by phillips321 on 2007-09-13
Hi guys,

Use linux on most of my kit but my girlfriend wants windows.

Laptop cannot boot from cd but can boot from floppy, i've tried the 6 winodws boot disks but it keeps crashing.

I currently have both winXP and ubuntu(no gui) installed, im using grub to boot into windows.

What i would like to do is remove grub+ubuntu and simply use the windows boot manager.
I can get into windows just fine, how can i reinstall the windows boot manager from within windows?

Cheers guys

Matt

---

### Post by bodhi.zazen on 2007-09-13
I do not think you can, but I am not sure ...

You can do it from Ubuntu :

Install  ms-sys
		```
sudo apt-get update && sudo apt-get install ms-sys
```

Restore MBR
		```
ms-sys -w /dev/<drive>
```
		<drive> = your windows hard drive (/dev/hda)

* you might need to ms-sys -p or ms-sys -w /dev/<partition>

How to : [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/) #scroll down and look at the readme file posted on that page.

man page : [http://linux.die.net/man/1/ms-sys](http://linux.die.net/man/1/ms-sys)

---

### Post by maybeway36 on 2007-09-13
Or from an MS-DOS or FreeDOS floppy, type:
```
fdisk /mbr
```

---

