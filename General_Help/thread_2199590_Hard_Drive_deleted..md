---
title: "Hard Drive deleted."
date: 2014-01-14
forum: General Help
---

### Post by zorro2 on 2014-01-14
Hello ubuntuforums, I firstly want to say that I am new to linux and I didn't know what to do. So look at what I did:
I tried to install ubuntu and it says "Input/Output device error on reading /sda1" something like that. I read something on a forum and it says that I need to format my hard drive, I did exactly what that tutorial says and my hard drive totally dispear. In that tutorial it was says something like:

Go to Disk utlity (find Hard Drive * Your memory, click on it and then click on Format Drive) I did that and then my Hard drive totally disapear from there. 
[IMG]http://s27.postimg.org/uq2b9pb83/look.png[/IMG]

How can I recorver my Hard Drive?
Thanks, 
Pickzo Elan.

---

### Post by Bashing-om on 2014-01-14
zorro2; Hi Welcome to the forum.

With no file system imposed on the hard disk, I can readily comprehend that "Disk Utility" may not see the drive.
Let's look at the hard disk with different tools.
Boot the liveDVD -> terminal -> dash -> search term GParted -> GParted iccon;
Upper right corner of GParted utility make sure "sda" is selected,;
show us that screen shot.

Also from the terminal, post back the out puts of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```
Once we know the data and partition tables are gone, perhaps we can then (re-)format the drive (with GParted) and work at installing ubuntu !

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by zorro2 on 2014-01-15
> **Bashing-om said:**
> zorro2; Hi Welcome to the forum.

With no file system imposed on the hard disk, I can readily comprehend that "Disk Utility" may not see the drive.
Let's look at the hard disk with different tools.
Boot the liveDVD -> terminal -> dash -> search term GParted -> GParted iccon;
Upper right corner of GParted utility make sure "sda" is selected,;
show us that screen shot.

Also from the terminal, post back the out puts of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```
Once we know the data and partition tables are gone, perhaps we can then (re-)format the drive (with GParted) and work at installing ubuntu !
[INDENT][INDENT]where there is a will there is a way[/INDENT]
[/INDENT]


Hello mate, did what you said and here is the result:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: /dev/sda: unrecognised disk label                                  
ubuntu@ubuntu:~$ 


```

And the screen shot [IMG]http://s10.postimg.org/fauin16cp/saved.png[/IMG]

Thanks.

---

### Post by Bashing-om on 2014-01-15
zorro2; Not Good !

OK, is there anything on that disk you can not live without ?
What I propose to do next will not permit any form of data recovery from that hard disk.

[INDENT]drastic situations == drastic measures
[/INDENT]

---

### Post by zorro2 on 2014-01-15
> **Bashing-om said:**
> zorro2; Not Good !

OK, is there anything on that disk you can not live without ?
What I propose to do next will not permit any form of data recovery from that hard disk.[INDENT]drastic situations == drastic measures
[/INDENT]


There is nothing on the disk that I care about. Everything I care about is my disk and how can I reinstall ubuntu on my laptop.
EDIT: Tried to install ubuntu, seems that my disk is back but I am getting an error:
[IMG]http://s30.postimg.org/d95064v9d/hba.png[/IMG]
Can't click any of the 3 options, nothing happens. What is the next step?

---

### Post by Bashing-om on 2014-01-15
zorro2; Hey;

As this point, with that error, I really think the thing to do is to zero out that hard drive, and begin the install anew,
The 'dd' process of writing zeros to the hard disk is lengthly to insure it is thorough will do it s l o w l y.
EDIT2: We are interested more in quality rather than quantity,; S L O W L Y
This impelementation of "dd" will take about 10 hours on a 1TB hard disk. There is no status in the original window, in order to get a status, follow the instructions as given:
```

man dd

```

Terminal command to zero out that hard drive:
EDIT: Must be run from the liveDVD !
```

sudo dd if=/dev/zero of=/dev/sda bs=1M

```


dd is known as Disk Destroyer ! USE with extreme care and caution, Here the objective disk is well defined as sda, and the end result is known; so use dd as directed.

When completed, one may look at the disk with GParted, or try the install directly.

[INDENT][INDENT]hope for the best
[/INDENT][/INDENT]

---

### Post by zorro2 on 2014-01-15
Yeah did what you said, here is the result.
```
 ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=1M
dd: writing `/dev/sda': No space left on device
715405+0 records in
715404+0 records out
750156374016 bytes (750 GB) copied, 403.667 s, 1.9 GB/s


```

Also tried to install it and get this error.
[IMG]http://s18.postimg.org/c0wmefrhl/ggda.png[/IMG]

[IMG]http://s10.postimg.org/p7660a5pl/acc.png[/IMG]

[IMG]http://s21.postimg.org/5f3jh8frb/post.png[/IMG]

---

### Post by Bashing-om on 2014-01-15
zorro2; ouch !

I have never encountered a situation that the low level tool "dd" could not write to the disk.
We must entertain the possibility that the hard disk is toast. Let's get confirmation, or maybe some other means to check that hard disk.
Like perhaps the manufacturers' disk check utility (??)
Hang on and let me see if I can get a compatriots' attention, Maybe he can come up with an alternative.

Nope, He is presently off-line,> I will check periodically for ya and ->

[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-01-16
I don't have much experience to share but it looks to me like the dd command completed OK

```
750156374016 bytes (750 GB) copied, 403.667 s, 1.9 GB/s
```

but the subsequent ext filesystem creation fails none the less (the I/O error @ sector 2048) - maybe worth looking at the SMART status of the disk if available (install smartmontools)?

---

### Post by 3rdalbum on 2014-01-16
If you can now see the disk in Disk Utility, you can use that to check the Smart Statistics. I suspect it will tell you that there are lots of bad/remapped sectors. If it does, then the disk is dead and should be thrown out and replaced. It cannot be used.

If it doesn't show more than about ten bad sectors, or if you can't get to SMART Statistics, then maybe just replace the cable connecting the hard disk to the computer.

---

### Post by oldfred on 2014-01-16
What was this drive before.
Did it have RAID, gpt partitioning, Intel SRT, Windows dynamic or other special configuration?

Is BIOS set to AHCI, not RAID nor IDE?

Bit strange that error is 2048 as that is first sector of first partition with all new partition configurations.

---

### Post by Bashing-om on 2014-01-16
@ oldfred; Wow !
> 
Bit strange that error is 2048 as that is first sector of first partition with all new partition configurations.


There is no substitute for knowledge and experience, beautiful observation that it may be "meta data" on the disk resulting in this situation.

@ zorro2;
We can install the dmraid tools and -if this meta data exist - remove it.

[INDENT][INDENT]as we live and learn[/INDENT][/INDENT]

---

### Post by silvervulpus on 2014-01-16
one way you can always check to see if the HDD is shot, is use a sata cable (whatever size fits) and connect it to a computer that is running windows (and trust me i HATE windows but....) using seagate HDD analysis and Belarc Hardware analysis from these two links, should tell you if it is a dead/burnt/broken drive [http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)   and [http://www.seagate.com/support/downloads/seatools/](http://www.seagate.com/support/downloads/seatools/)    (if it is burnt/dead/broken and less than 2 years old, its because you probably removed alot of flash drives without ejecting or safely removing which can kill buffers in a very very short amount of time, its also possible it came in contact with a magnetic field of some kind or it became heated above 140 degrees Fahrenheit) i also recommend belarc for any techs who need to install drivers and need to know the hardware but cant take the casing off or cant access ubuntu hardware profiler (ubuntu hardware profiler might give you an inclination as to whether your drive is buster or not too!... i forgot about it for a second because i was thinking about demon windows)

---

