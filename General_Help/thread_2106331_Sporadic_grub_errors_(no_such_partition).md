---
title: "Sporadic grub errors (no such partition)"
date: 2013-01-18
forum: General Help
---

### Post by jwestbury on 2013-01-18
I'm running 12.04 LTS. I've got my drive set up as follows:

/dev/sda1: Windows reserved partition
/dev/sda2: Windows 7 Embedded Professional
/dev/sda5: Ubuntu 12.04 LTS
/dev/sda6: swap

I installed Windows first, and subsequently installed Ubuntu and grub.

Ubuntu will boot fine most times. However, on an all-too-regular basis, grub will throw an error at boot. The two errors I have received are "no such partition" and "unknown filesystem." If I reboot, the problem does not typically recur immediately, and it will take 3-4 more reboots before I see another error (and it could be either error; there does not seem to be any consistency in which error occurs when).

Any help would be appreciated!

*Edit:* When I get the "no such partition" error, **ls** shows:

(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)

---

### Post by oldfred on 2013-01-18
While it is more for boot issues, not what I think you have in some sort of file issue, post the BootInfo report just to see if it says anything unusual.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by jwestbury on 2013-01-21
[http://paste.ubuntu.com/1555699](http://paste.ubuntu.com/1555699)

A few additional notes:

This is a fresh install, so it isn't a grub file I've mucked about with at all. The same thing happens with a Debian minimal install, too, so I know it's not isolated to Ubuntu. It also happens with grub 1.98, packaged with Ubuntu 10.04 LTS in the form of an older TurnKey Linux release.

I've used the old TurnKey release extensively as part of a custom recovery partition for our customers, and have grub files tailored to this usage (splash screen, auto-boot into Windows unless a button is pressed, and a weird nested grub setup to circumvent a splash screen bug). They were working fine for about a year, then suddenly this error occurred. I assumed there had been a minor hardware change (our supplier hasn't been able to confirm that there's been a hardware change), thus the attempt to install fresh and start over with grub, but, obviously, that's been unsuccessful.

Anyway, the file above is the BootInfo report from the system I'm currently working with, so let me know if you see anything amiss.

---

### Post by oldfred on 2013-01-21
I do not see anything in BootInfo report.

Do you hibernate Windows? 
Have you run chkdsk on the Windows NTFS partitions recently?

Grub scans drive when booting and maybe not seeing NTFS drive causes an issue?

---

### Post by jwestbury on 2013-01-21
No hibernation, no. I'll try running a chkdsk, but I it's also a fresh Windows install, so it would seem odd to have a filesystem error, especially since this has happened on several machines.

---

### Post by jwestbury on 2013-01-21
chkdsk shows no problems on the NTFS partitions.

---

### Post by oldfred on 2013-01-21
Intermittent problems are the worst. I might also try a full e2fsck, regular fsck may just say no reported issues and not run.

       # From liveCD so everything is unmounted,swap off if necessary
# Change example shown with partition sdb1 to your partition(s)

#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by jwestbury on 2013-01-22
No errors found with e2fsck, unfortunately.

---

### Post by oldfred on 2013-01-22
After you have boot issue do log files show anything? You can use Log File Viewer and look at dmesg and see if the previous not current boot had any errors.

---

