---
title: "partitoning ineffective"
date: 2022-11-17
forum: General Help
---

### Post by andrasszoke on 2022-11-17
Hi Anybody
I cannot delete partition from a microsd. Anytime and with any program - gnomedisks, gparted, fdisk, testdisk - I delete the partition table it says everything went ok, but after refreshing everything is there, all lthe data is untuched. I made a clean libreelec install on the card, it got infected with some malware wich made the rpi to attack with ddos some servers - I got a coll from the ISP. I removed the card and tried to clean it with ubuntu and windows too, nothing helped, it keeps reappearing untouched after formatting or repartitioning. Tt's not a big loss for a card, it just makes me crazy not being able to do such a "simple" thing wich came out is not so simple....
I would be greatful for any idea or opinion

---

### Post by TheFu on 2022-11-17
Wipe the entire storage device starting from the beginning.  I'd use dd, but cp, ddrescue, and many others can be used.  Then setup partitions as desired. I'd use 'gparted' if I wanted a GUI. Don't forget to create a new GUID partition table first. Gparted has the 'Apply' button to actually perform the different requested changes.

Flash media center storage devices do wear out and typically, the first sign of that is they cannot be modified. Soon, even read won't work.  I've had some wear out in 1 yr of use.  The next time, I specifically bought high endurance flash storage, disabled all local logging and only stream media from other network devices.  Since making those changes, it has been 5+ yrs without any issues.

Some ARM-based media players use a self-sizing installer. This means that effort to specifically setup partitions is a complete waste of time.

If you can provide some facts, perhaps someone can help?  To start:
```
sudo parted -l
lsblk -e 7 -o name,size,type,fstype,uuid,mountpoint

```
Remove any 'loop' devices. Those aren't real storage.

---

### Post by tea for one on 2022-11-17
> **andrasszoke said:**
> I delete the partition table it says everything went ok, but after refreshing everything is there, all lthe data is untuched.
Did you create a new partition table?

---

### Post by andrasszoke on 2022-11-17
Hi, I didn't try to set up partitions for libreelec i just copied the image with dd, and also tried to get rid of the infected system with dd /dev/zero with the same results as partitioning programs, after refresh nothing changed. Anyway:

```
][FONT=Verdana]sudo parted -l[/FONT]

[FONT=Verdana]Típus: MXT-USB Storage Device (scsi)[/FONT]
[FONT=Verdana]/dev/sdb lemez: 7901MB[/FONT]
[FONT=Verdana]Szektorméret (logikai/fizikai): 512B/512B[/FONT]
[FONT=Verdana]Partíciós tábla: msdos[/FONT]
[FONT=Verdana]Lemezjelz&#337;k:[/FONT]


[FONT=Verdana]Szám Kezdet Vég Méret Típus Fájlrendszer Jelz&#337;k[/FONT]
[FONT=Verdana]1 4194kB 541MB 537MB primary fat16 boot, lba[/FONT]
[FONT=Verdana]2 541MB 7901MB 7360MB primary ext4[/FONT]


[COLOR=#000000][FONT=Verdana]lsblk -e 7 -o name,size,type,fstype,uuid,mountpoint

NAME SIZE TYPE FSTYPE UUID MOUNTPOINT

sdb 7,4G disk
&#9500;&#9472;sdb1 512M part vfat 64FD-6F75 /media/szoke/LIBREELEC
&#9492;&#9472;sdb2 6,9G part ext4 2e4302bf-e281-4f73-9b54-184939a469b1 /media/szoke/2e4302bf-e281-4f73-9b54-1[/FONT][/COLOR]
```[COLOR=#000000]


[/COLOR]

---

### Post by andrasszoke on 2022-11-17
Yes, anyway at least I tried, all apps said that it did it, and after refresh all the old same thing...

---

### Post by tea for one on 2022-11-17
This is my SD Card for libreelec:-
```
edited@edited:~$ sudo parted -l
[sudo] password for edited: 
Model: SD SL16G (sd/mmc)
Disk /dev/mmcblk0: 15.9GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR="#0000FF"]gpt[/COLOR]
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      4194kB  541MB   537MB   fat16        system   legacy_boot, msftdata
 2      541MB   15.9GB  15.4GB  ext4         storage

edited@edited-22-04:~$ 
```
Use gparted to create a new GPT partition table.
Any joy?

---

### Post by TheFu on 2022-11-18
> **andrasszoke said:**
> Yes, anyway at least I tried, all apps said that it did it, and after refresh all the old same thing...

Please post exact commands and when posting anything from a terminal, please use forum code-tags, so columns line up. Too hard to read otherwise.  Just edit the already posted stuff for code-tags, please.  That will keep the thread cleaner.

BTW, would be good if which storage is of interest were clearly pointed out ... or just remove the entire stanzas from the output for the drives that aren't of interest and say that.    "Booted from sdh, no issues with it, removed output from it."

---

