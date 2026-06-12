---
title: "mounting RAID drives help please...urgent"
date: 2007-06-11
forum: General Help
---

### Post by (@rwy^ on 2007-06-11
Hi,

This is a long post but I have tried to make your lives easier by putting in as much detail as possible... I know it makes troubleshooting loads easier :).

My computer has an Adaptec 1220SA RAID card with two mirrored 250GB SATA II HDDs. It is all formated as 1 NTFS partition with Windows installed (no linux). However yesterday there was an error along the lines of "could not find an important system file therefore cant boot". I tried using the Windoze setup CD and using the "press r to repair" option, but that option was not there - it would only let me install to that drive.

At this point I booted Ubuntu from my flash drive to try and mount the drives to recover data before reinstalling Windoze. I tried using the commands

$sudo mkdir /mnt/hda/
$sudo mount /dev/hda /mnt/hda

however I was told there was no drive. I have narrowed this down to three possibilities:
1) I used the wrong command (unlikely)
2) I tried to mount the wrong drive (likely)
3) The Adaptec card needs drivers

Has anyone got any suggestions? I dont mind what really, anything that might work is worth a try! Even if I am doing something wrong on the Windoze CD :o!

I know this has been a long post, but thanks in advance for any help.

Carwyn

---

### Post by cantormath on 2007-06-11
```
:~$ cd /tmp/
:~$ mkdir whatever
:~$ sudo mount /dev/hda /tmp/whatever
:~$ cd /tmp/whatever

```make sure that you have the right partition.....hda, hda1...etc. 
```
:~$ sudo df -h 
```Show disks partitions sizes and types 
```
:~$ sudo fdisk -l 
```or
System>Administration>disks and take a look.....

---

### Post by (@rwy^ on 2007-06-11
thanks for replying, but having tried to mount /dev/hda I am still getting the "medium not found" message. Is this because the disk(s) are located elsewhere because of the RAID controller, or because there are RAID drivers for the PCI-e card that need installing before the array can be used?

Thanks,

Carwyn

---

### Post by smartboyathome on 2007-06-11
Please unplug your drive, plug it back in, and type this in a terminal and tell us what you get:

```

nano /var/log/messages

```

---

### Post by (@rwy^ on 2007-06-11
Thanks for replying. I have solved the issue by using a different XP install disk from antother computer which actually gave me the repair option. I used the bootcfg /repair command to repair the boot.ini file and it now seems to boot fine

Thanks,

Carwyn

---

