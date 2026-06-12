---
title: "Ubuntu can not regognize any partitions"
date: 2007-12-04
forum: General Help
---

### Post by warnec on 2007-12-04
Hello. I have a bad problem with my Ubuntu 7.10 installation. I thinnk it all started when i instaled Ext2 driver on Windows XP and i copied some files from Win XP to Linux partition. Else, it may be caused by something else. I wanted to try VirtualBox with my Ubuntu. However, i chose that the file with virtual partition (it was *.vdi file, AFAIK) was not saved in Ubuntu partition, but inside linux partition. After that, i tuned PC off. AFAIK, tommorow, when i tuned PC on, there wasn't anything like GRUB ( but i am not sure, sry my memory is really bad ;)). My computer behaved like it was completely annihilated (GRUB, not computer :D), or it was just never present in my MBR - it booted WinXP without any errors,questions, anything like that, though i still can see swap partition and linux partition in My Computer. I ran LiveCD and wanted to reinstall GRUB, but got some error which i can't fix. See my thread here:
[http://ubuntuforums.org/showthread.php?t=631239](http://ubuntuforums.org/showthread.php?t=631239)
Now, i even tried formatting and reinstalling Linux - gparted did not see any partitions, just plain, raw hard drive! I tried 
```

fdisk -l

```
But it returned nothing. It just returned me to command prompt with nothing. It looked like that
```

myname-blablabla : fdisk-l
myname-blablabla 

```
So i got no reports, nothing. I do not understand that. Is there any way to make Ubuntu see partitions? I repeat, WinXP works completely flawlessly. I would rather not format, it  took me much effort to get Compiz Fusion running on my PC from git with no-xcb patch :)

---

### Post by meierfra on 2007-12-04
You need to use "sudo" with fdisk:

```
sudo fdisk -l
```

Post the output.

---

### Post by warnec on 2007-12-05
here you go:
```

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13870   104857168+   7  HPFS/NTFS
/dev/sda2           13871       41344   207696352+   f  W95 Ext'd (LBA)
/dev/sda3           15258       41344   197217688+   7  HPFS/NTFS
/dev/sda5           13871       14928     7984242   83  Linux
/dev/sda6           14929       15193     2000061   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by meierfra on 2007-12-05
Try this:

reinstalling grub via:

```
sudo grub
root (hd0,4)
setup (hd0)      (Opps, left this out originally)
quit
```

Open  menu.lst via:

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda5 /ubuntu
cd /ubuntu/boot/grub
cp menu.lst menu.lst.backup
gksudo gedit menu.lst
```


Change "#groot (hd0,6)" to "#groot (hd0,4)"

Change all "root (hd0,6)" to "root (hd0,4)"  (there are three of them)

Save the file and reboot.

---

### Post by warnec on 2007-12-05
thank you for trying to help me, but it did not help. My PC still boots straight to WinXP. And shouldn't iI do
```

setup (hd0)

```
after 
```

root (0,4)

```
? I think that would install GRUB to MBR. Am i not right? If GRUB isn't installed, PC would use ntldr, right?

Please tell me if i'm thinking correctly.You tried to save GRUB on windows partition, am i right? Or what did you do?

---

### Post by el escocés on 2007-12-05
going through the same thing with someone else right now, have a look at the thread...

[http://ubuntuforums.org/showthread.php?t=631975](http://ubuntuforums.org/showthread.php?t=631975)

---

### Post by meierfra on 2007-12-05
Sorry. I left out the "setup (hd0)".

> f GRUB isn't installed, PC would use ntldr, right?
yes.

---

### Post by meierfra on 2007-12-05
deleted

---

### Post by el escocés on 2007-12-05
deleted

---

### Post by meierfra on 2007-12-05
deleted

---

### Post by warnec on 2007-12-05
Strange. In "Computer" linux sees win partitions. They are named "volume 100GB" and "volume 188GB" or something like that. When i double-click first, its name changes to "disk-1" and double-clickd second changes name to "disk-2" And then, double clicking these "disks" reveals the contents of windows partitions. Ok, but now when i do "sudo grub" and "root (hd0,4)" it works, but then i do 
```

setup (hd0)

```
And it returns:
```

Error 17: Cannot mount selected partiton

```
What to do now?

---

### Post by meierfra on 2007-12-05
> /dev/sda1   *           1       13870   104857168+   7  HPFS/NTFS
/dev/sda2           13871       41344   207696352+   f  W95 Ext'd (LBA)
/dev/sda3           15258       41344   197217688+   7  HPFS/NTFS
/dev/sda5           13871       14928     7984242   83  Linux
/dev/sda6           14929       15193     2000061   82  Linux swap / Solaris


Your partition table is screwed-up. The primary partition "sda3" sits inside the extended partition "sda2".  testdisk  (see my signature) might be able to fix the problem.

---

### Post by warnec on 2007-12-05
Actually, it is really strange, I always had only 4 partitions: sda1 as my primary WinXP partition, sda5 as secondary WinXP partition, then swan and linux partition. I also had ~500MB of raw, unformatted space, but that does not count, i think.

PS.: i have an idea. Maybe it is pendrive? Its FS is FAT32. I am not sure if i had it plugged in when i run the command, though.

PS2.: The usage of TestDisk isn't quite easy. I am also not sure if i need to recover my partitions if my WinXP runs fine. I would just want to be ABSOLUTELY sure that my windows XP partitions remain untouched. TestDisk looks seriously, and i think that if it can cause any loss of data, i would rather wait (On Christmas i build new computer, the same Hard Drive, but entirely formatted)

---

### Post by meierfra on 2007-12-05
sda2 by itself is not a problem. It is an extended partition. An extended partiton is just a container for other partitions. Any hard drive can only have four  primary partition. So to be able to have more than four partitions one creates an extended partition. An extended partition can hold lots of partitions.  Partition inside an extended partition are called logical partition. Partitions not inside an extended partition are called primary partitions.


if you look at fdisk information  you see that 
  sda2   starts at 13871 and ends at 41344
  sda5   starts at 13871 and ends at 14928 
  sda6   starts at 14929 and ends at 15193
  sda3   starts at 15258 and ends at 41344


So sda2 is an extended partition containing the logical partitions sda5, sda6 and sda3.


Now primary partitions are named sda1, sda2, sda3, sda4.  Logical partition  are named sda5, sda6, sda7 and so on. 

So sda3 should be a primary partition. But it's not,  it sits inside the extended partition
That means that there is a mistakes in your partition table. testdisk is a program that among can help you recover data, but it also fixes partition tables.

Don't be scared of testdisk. Read the Hermazone info on testdisk. Start "testdisk", select "analyze"  and then play around a little bit to find out what is going on. Just don't select  "write" before you know what you are doing.

---

### Post by warnec on 2007-12-06
So partition can be both primary and extended? (like sda2 here)  If primary are sda1-4 and logical are sda5 and more, why is sda2 chosen for extended partition, and not e.g. sda4 if it is the last of primary partitions?

---

### Post by meierfra on 2007-12-06
> So partition can be both primary and extended? (like sda2 here)

yes.

---

### Post by warnec on 2007-12-08
Read my topic here:
[http://gparted-forum.surf4.info/viewtopic.php?pid=5206#p5206](http://gparted-forum.surf4.info/viewtopic.php?pid=5206#p5206)

---

