---
title: "Boot in command line, how?"
date: 2008-06-30
forum: General Help
---

### Post by okos on 2008-06-30
I have Hardy Heron
I want to boot into console instead of x
I tried the following and I still boot in to x:
I edited grub as stated [here.]("https://lists.ubuntu.com/archives/ubuntu-users/2005-November/057420.html")
```
This is what I did to have run level 3 as console mode and add it to the
grub menu:

Step 1:
	update-rc.d -f gdm start 13 2 4 5 . stop 01 0 1 3 6 .

Step 2: Modify /boot/grub/menu.lst by adding a new menu entry:

	title           Ubuntu, kernel 2.6.12-9-386 (CONSOLE)
	root            (hd0,6)
	kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro acpi=on quiet splash 3
	initrd          /boot/initrd.img-2.6.12-9-386
	boot

Make sure to adjust the root line to your hard drive setup and to run
"sudo update-grub"

```

Ive tried this in console:
```
sudo update-rc.d -f gdm remove
```
I am not sure what else to do.

Any answers?

---

### Post by Sinkingships7 on 2008-06-30
You can try removing GDM.

---

### Post by cmileto on 2008-07-12
sudo apt-get remove gdm

---

### Post by markharding557 on 2008-07-12
simply kill your xserver
> /etc/init.d/gdm stop

this will leave you on the command line when you want your gui back then do
> startx

---

### Post by u-slayer on 2008-07-12
I do this all the time. You need to get bum (boot up manager)

Run bum and deselect the checkbox for gdm.

---

### Post by WRDN on 2008-07-12
Click System > Administration > Services and deselect the "Graphical Login Manager (gdm)" service.

---

