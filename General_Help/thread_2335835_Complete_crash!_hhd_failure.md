---
title: "Complete crash! hhd failure?"
date: 2016-09-01
forum: General Help
---

### Post by cee2 on 2016-09-01
got a whole page of errors that i took a pic of but have no way to get it off my phone to computer right now

says something about
error reading block 1819677648
run fsck manually

will post a pick soon

also tried reinstalling lts 16.04 but is took 3 hrs to save old files so i concluded it was stalled and aborted install

---

### Post by cee2 on 2016-09-01
i dont understand the pic upload function : (

---

### Post by ajgreeny on 2016-09-01
As the reinstall did not work it seems likely that your hard disk may have a fault and not be usable any more.

Where were you trying to save the old files; to a USB disk or if not, to where?

---

### Post by cee2 on 2016-09-01
i was doing a reinstall which was supposed to save the old files, it was only 6 month old install with very little files so a reinstall/save of files shouldnt have taken 2.5 hrs plus the first 1/2 or so of downloading files etc

---

### Post by ajgreeny on 2016-09-02
So was this a reinstall over a previous OS but specifically choosing not to format any of the partitions, or do you have a separate /home or /data partition which you chose not to format during the installation?

---

### Post by cee2 on 2016-09-02
yes it was a reinstall of  ubuntu 16.04lts over ubuntu 16.04 lts, which  used the whole 750 gig drive choosing to keep old 16.04 lts files and  data.
it did say one partition would have to be deleted or formatted but i assume it was just a swap partition

---

### Post by cee2 on 2016-09-02
ok so i hooked up this possibly/probably bad hdd to the computer in tandem with another ubuntu install i have
I can see the 1.5 tb drive in left panel but get an error saying unable to access 1.5tb volume

is there some way to fix it from this install without formatting it, i need my latest resume on that drive
if not would formatting it fix it?
here is exact error

Error mounting /dev/sdb1 at /media/curt/b467ba20-70e6-4da7-993d-b40f20d4785e: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/curt/b467ba20-70e6-4da7-993d-b40f20d4785e"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

---

### Post by cee2 on 2016-09-02
ran this but no idea if it tested my 120 gig drive running current OS or this 1.5 tb drive im trying to fix

it only took five minutes so maybe it wasnt the big drive?

curt@curt-GA-990XA-UD3:~$ sudo badblocks -sv /dev/sda
[sudo] password for curt: 
Checking blocks 0 to 117220823
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

---

### Post by cee2 on 2016-09-02
sudo badblocks -sv /dev/sdb1

running this now
it says it has 1.456 billion blocks to check, so is this likely the 1.5 tb drive?

---

