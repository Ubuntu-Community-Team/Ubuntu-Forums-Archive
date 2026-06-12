---
title: "Error when accessing encrypted drive"
date: 2014-05-09
forum: General Help
---

### Post by darthpbal on 2014-05-09
I have some files that I'm trying to access on an SD card going through a USB adapter and I've encrypted it earlier. I've been able to access it in the past, but after I've installed my newest version of Ubuntu (14.04) I've been getting this error. I can see the drive to mount it, but when I try to enter the password it won't let me access it. I know when I was trying to copy some stuff over to the drive before, it may have had some power issues on account it was an SD card going through a USB adapter, which I've been reading have some power issues. It's possible that the card was messed up from inconsistent power going to it, but it's like to make sure what this error code means.

If it turns out that the drive's data isn't salvageable, is it possible to restore data from a backed up drive from 12.04? The drive I was doing regular back ups was on a 12.04 machine, and I'm not sure what exactly would be getting restored if I try to get that data back in my now 14.04 machine.

Here is the error:
Error unlocking /dev/sdb1: Error spawning command-line `cryptsetup luksOpen "/dev/sdb1" "luks-cbd937db-4af1-46b6-bce8-5eb993159c90" ': Failed to execute child process "cryptsetup" (No such file or directory) (g-exec-error-quark, 8)

---

### Post by Bharath on 2014-05-14
I have same issue.... pls help....

---

### Post by temenchat on 2015-04-07
Same problem with me, solved by installing crypsetup

$ sudo apt-get install cryptsetup

---

