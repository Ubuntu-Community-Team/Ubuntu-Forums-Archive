---
title: "I need to install grub seperatly... how?"
date: 2008-06-07
forum: General Help
---

### Post by McTricks on 2008-06-07
I have Ubuntu 8.04 installed on an external hard drive, and at first, I liked being able to have an entire 100 GB for Ubuntu, but now I found out something that I should have thought of.... GRUB is also on the external hard drive, so I need to have the External HD plugged in even to boot into windows... Now, I was wondering if I could possibly put GRUB on my Internal drive in my laptop, so it will load GRUB, and I don't have to have my external plugged in, but still have Ubuntu on my external.

---

### Post by housam on 2008-06-07
Read this [[COLOR="Red"]_[U]document _[/U][/COLOR]]("http://www.troubleshooters.com/linux/grub/grubpartition.htm")about creating dedicated grub partition

---

### Post by McTricks on 2008-06-07
ok, thanks, I'll try that, thanks again

---

### Post by wdaniels on 2008-06-07
> **McTricks said:**
> GRUB is also on the external hard drive, so I need to have the External HD plugged in even to boot into windows...

That doesn't seem right - you should still be able to boot normally into Windows from the internal drive if the BIOS is set to boot from it, unless something destroyed the MBR on that drive, which the Ubuntu installer should not do. Exactly what happens if you try to boot from the internal drive? 

> **McTricks said:**
> Now, I was wondering if I could possibly put GRUB on my Internal drive in my laptop, so it will load GRUB, and I don't have to have my external plugged in, but still have Ubuntu on my external.

You would need a Linux partition (albeit a small one) on the internal drive for GRUB to store it's files, or use something like [Grub4dos]("http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial") instead.

---

### Post by meierfra. on 2008-06-07
You can also  solve your problem by installing Grub to the MBR of the external drive and restore the MBR of the internal drive. Click on "Dual" in my signature for detailed instruction.
(Since your are using Hardy, there is a small problems with that HowTo. "ms-sys" is not in the hardy repositories. You need to get the Debian package instead:[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys"). Download the i386 version.  Right Click to install)

---

### Post by meierfra. on 2008-06-07
> unless something destroyed the MBR on that drive, which the Ubuntu installer should not do.

By default Ubuntu installs Grub onto the MBR of the internal drive.

---

### Post by wdaniels on 2008-06-07
It just occurred to me that perhaps you are mistaken about which disk GRUB is actually on. Perhaps the reason you need the external disk connected to boot the internal one is that the GRUB MBR is on the internal disk, but pointing to the external one for stage 2/3?

I'm not 100% sure about exactly what is done by each stage of the GRUB process to know if this is a logical explanation or not. I think it's stage 2 that shows the menu selection, but as I understand it, the stage 2 code is usually written directly after the MBR, so presumably in that case you would still see some kind of error message from GRUB when booting without the external drive...?

Or probably I'm just confused and way off track here :D

---

### Post by meierfra. on 2008-06-07
> Perhaps the reason you need the external disk connected to boot the internal one is that the GRUB MBR is on the internal disk, but pointing to the external one for stage 2/3?

Exactly. The stage 1 files are on the MBR of the internal drive. The stage 1.5 files are located right after that.  But the stage 2 files and "menu.lst" are on the Ubuntu partition.  This makes it impossible to boot without the external drive attached.

There are three different ways to resolve the situation:

Post 2:   Place the stage 2 and menu.lst on  the internal drive: [Dedicated Grub Partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

Post 5:  Place stage 1 and stage 1.5 files on the external drive: [Reinstall Grub]("http://ubuntuforums.org/showthread.php?p=3995006")

Post 4:   Use a different boot loader:  [Grub4Dos]("http://users.bigpond.net.au/hermanzone/p9.html") for XP and[ EasyBCD]("http://neosmart.net/wiki/display/EBCD/Ubuntu") for Vista.

---

### Post by McTricks on 2008-06-07
I'm not sure exactly what answer I should use now.... but when I star my computer with my external unplugged, it gives me an error
called "error 21".....

---

### Post by meierfra. on 2008-06-07
Open a terminal (Applications->Accesories->Terminal).  Post the output of the following commands:

```
sudo fdisk -l
```
(l is a lower case L)

Also type

```
sudo grub
```
and at the "grub>" prompt

```
find /boot/grub/stage2
```


With this information  I can write up  my HowTo  with all the correct numbers inserted. (It's really fairly easy once you don't have to worry about the correct numbers anymore)

---

### Post by McTricks on 2008-06-08
For the first thing, I get:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10        9123    73208205    7  HPFS/NTFS
/dev/sda3            9124        9729     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeccf6b16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11859    95257386   83  Linux
/dev/sdb2           11860       12188     2642692+   5  Extended
/dev/sdb5           11860       12188     2642661   82  Linux swap / Solaris
mctricks@lester:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.


And for the second, I get:

 (hd1,0)

---

### Post by meierfra. on 2008-06-08
Step 1 Edit menu.lst

Open a terminal and type

```
cd /boot/grub

sudo cp menu.lst menu.lst.backup

gksudo gedit menu.lst

```
(the "l" in menu.lst is a lower case L, not the number one)

This creates a backup of "menu.lst" and opens it in a new window.
Look for the line

#groot (hd1,0)

Change it to

#groot (hd0,0)

Change your Windows title to

title Windows XP
root (hd1,1)
map (hd0) (hd1)
map  (hd1)  (hd0)
savedefault
makeactive
chainloader +1

To complete Step 1, go back to the terminal and type

```
sudo update-grub
```

Step 2: Install Grub to the MBR of the external drive:

In the terminal type:

```
 sudo grub
```

and at the "grub>" prompt

```

root (hd1,0)

setup (hd1)

quit

```

Step 3 Restore the MBR of the internal drive 

Get the Debian package  for "ms-sys"  [http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys"). Download the i386 version. Double clicking the icon to install the package

In the terminal

```
sudo ms-sys -m /dev/sda
```

Reboot. Change the boot order in the Bios so that the external drive comes before the internal drive.

---

### Post by meierfra. on 2008-06-08
I just realized that I never asked whether you have XP or Vista. If you have Vista leave out the two "map" lines in the Windows item (and change the title)

---

### Post by McTricks on 2008-06-08
When I click on the link for debian, I get an error saying there is no such pakage

---

### Post by meierfra. on 2008-06-08
Oops. There was an extra period at the end of the url. I fixed it.

---

### Post by McTricks on 2008-06-08
Ok, I got around to finishing it, Sorry it took so long, I had to go somewhere..... Now, when my external is not plugged in, it goes strait to windows, and when it is plugged in, it will load grub. There is a problem, however.... When I try to load Ubuntu, it says..... hold on I'll go get the exact wording.....

---

### Post by McTricks on 2008-06-08
Ok, the exact wording is....

"Error 17: Cannot mount the selected partition"

---

### Post by wdaniels on 2008-06-08
When you change the boot order in the BIOS, sometimes that affects the disk numbering as seen by GRUB. I think probably when the external drive is connected now, GRUB sees it as hd0 instead of hd1. To check that hit C at the GRUB menu to go into the command prompt and type:

```
find /vmlinuz
```

This should tell you what driver number the Linux partition is now.

---

### Post by meierfra. on 2008-06-08
I sound like you forgot to change "#groot" or you didn't do  "sudo update-grub".  Do what wdaniels said:

Press "c" at the grub menu. Type

```
find /vmlinuz
```

This should return (hd0,0)


Press "esc" to get to the Grub menu.  Select ubuntu and press "e" for edit. At the new screen press "e" again. Change

root (hd1,0)

to

root (hd0,0)  (use the output "find /vmlinuz")


Press "enter" and then "boot".  This should boot you into Ubuntu.


Once you booted into "ubuntu"  repeat Step 2 of my instruction.

Just to double check:  After "sudo update grub"  type "gksudo gedit /boot/grub/menu.lst"

Look for 

title Ubuntu ......
root (hd0,0)
.....

It should say "root (hd0,0)" and not "root (hd1,0)". If it still says "root (hd1,0)" change all the the "root (hd1,0)" in the ubuntu items and in "memtest" to  "root (hd0,0)".

---

### Post by McTricks on 2008-06-08
Ok, everything is working now, Thank you so much!

---

