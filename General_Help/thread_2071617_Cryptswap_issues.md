---
title: "Cryptswap issues?"
date: 2012-10-15
forum: General Help
---

### Post by clonezonedude on 2012-10-15
Hi

Me again, and this time im super confused :/

Recently, I installed a batch of updates that my copy of ubuntu required me, but apparently something broke in the process, and now I am unable to re-enter my main computer OS

When I start ubuntu, it takes a while to load, and over time I get this mesage

```
Disk drive for Dev/Mapper/Cryptswap not redy yet or present. Press S to skip, M for...
```

IDK what I broke, but I had to install a second partition kubuntu to be able to use the computer, but I really need to access all my files for back up to be able to completely reformat the  machine and install a fresh ubuntu 12.10

I have googled left and right, north and south for this issue, but none of the solutions seem to work

Please help me 

Thanks in advance!!

---

### Post by clonezonedude on 2012-10-22
bump, help plz!!

---

### Post by clonezonedude on 2012-10-28
Hi

I posted this in another section, but it seems like those who visit it were unable to answer this question. I have googled this before, but nothing I try helps. Please help me if you can, I have very important information to recover :( 

I'm not upset, just really confused on whatever happened, I cant access in command line or anything :(

Recently, I installed a batch of updates that my copy of ubuntu required me, but apparently something broke in the process, and now I am unable to re-enter my main computer OS

When I start ubuntu, it takes a while to load, and over time I get this mesage

```
Disk drive for Dev/Mapper/Cryptswap not redy yet or present. Press S to skip, M for...
```

IDK what I broke, but I had to install a second partition kubuntu to be able to use the computer, but I really need to access all my files for back up to be able to completely reformat the  machine and install a fresh ubuntu 12.10

I have googled left and right, north and south for this issue, but none of the solutions seem to work

Please help me 

Thanks in advance!![

---

### Post by mardybear on 2012-10-28
Hi clonezonedude.

Do you have an Ubuntu liveCD? If so, set your computer's BIOS to boot from CD and then you can at least access your system to back-up/export your data.

Once your data is backed up you can try to fix your system.

If you press 'S' to skip, then your system boots normally and runs okay?

I have no personal experience with this issue but read there may be a cryptswap bug. The bug report seemed to indicate it may be an intermittent problem and the system may simply boot on it's own if left for a while. Alternatively, i've also read you can disable cryptswap. See links and quote:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086)

[http://askubuntu.com/questions/34519/how-to-disable-cryptswap](http://askubuntu.com/questions/34519/how-to-disable-cryptswap)

"If you remove/comment lines from /etc/crypttab and /etc/fstab, encrypted swap will not created on the next boot."

mardybear

---

### Post by oldos2er on 2012-10-28
Threads merged; please don't open more than one thread for each issue. If you would like your thread moved to a different forum, use the 'Report Abuse' button and ask staff to move it.

---

### Post by Bashing-om on 2012-10-28
clonezonedude; Hi ...
I expect this to be a rather straight forward fix.
1. Is the encryption deliberate ?: post output of terminal code:
```
cat /etc/crypttab
``` no out put if non existent (good)

2. Is there an encrypted partition ? 
```
sudo dmsetup status
```3. Is swap actually encrypted ?
```
sudo blkid | grep swap 
```4. The point of emphasis -> /etc/fstab: what is it mounting as ?
```
cat /etc/fstab
```I expect to edit /etc/fstab to effect the repair. Will advise with additional instructions
when I see the above results.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by pakopako on 2012-10-28
> **clonezonedude said:**
> Recently, I installed a batch of updates that my copy of ubuntu required me, but apparently something broke in the process, and now I am unable to re-enter my main computer OS
Have any of these posts allowed you to enter your main OS? (What *is* your main OS?)

As for the Cryptswap message, I wouldn't worry about that. The Cryptswap check is just a check and it unless you created one for yourself, it's message with no meaning. Following Bashing-om's post to make sure you don't have cryptswap enabled and you can remove the check easily.

How is your machine currently set up? (How many drives, partitions, and what OS is on each partition.)

---

### Post by daniroma on 2013-05-02
[**[COLOR=#000000]@ Bashing-om[/COLOR]**]("http://ubuntuforums.org/member.php?u=1111508")      

Here  is terminal code You requested:

daniel@daniel-desktop:~$ [B]cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/dm-0                               partition    3688444    0    -1[/B]
daniel@daniel-desktop:~$ [B]cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/dm-0                               partition    3688444    0    -1[/B]
daniel@daniel-desktop:~$ [B]sudo dmsetup status
cryptswap1: 0 7376896 crypt 
daniel@daniel-desktop:~$ sudo blkid | grep swap
/dev/mapper/cryptswap1: UUID="85b910e4-009d-4423-8094-e5c409bde7ac" TYPE="swap" [/B]
daniel@daniel-desktop:~$ [B]cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4bda7a62-198d-477c-be97-835148b6b59a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=62faa840-9bb0-4c2b-b5f5-7745ed8534df /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=07399af8-053e-4142-a591-466017884a66 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
[/B]

Is my swap partition activated / working properly or not?

Using Xubuntu 13.04

---

