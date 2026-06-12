---
title: "Laptop will not boot"
date: 2015-02-08
forum: General Help
---

### Post by toneykg on 2015-02-08
Hi 
Sorry to bother you guys, i have a paper due monday and while its done
laptop that was working fine now will not boot
I do not dual boot, solely run ubuntu 14.04

i get the screen listing installs and recovery loads
i can select them but nothing happens

have been reading thru grub posts but having tried most i get errors

sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.


tried installing boot repair that also failed
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

download failed, so unable to run
 
Not an expert and not making any headway on this
HELP!!

I will be online reading as you post so i can get this resolved asap

---

### Post by ajgreeny on 2015-02-08
In emergency you can always get the paper you need off the non-booting machine by using a live DVD/USB and copying it to another flash drive, or if this is appropriate by simply printing it from the live system, if you have a printer you can install to the live system.

Unfortunately, without more detailed info or a boot-repair report, it is very difficult to guess what has gone wrong.  Have you tried booting to an earlier kernel than your most recent version? There have been cases where the 3.13.0-45 is causing problems of one sort or another, so if you haven't already done so, go to Advanced or whatever it is called in the grub menu, and there you should get the option to boot to an earlier kernel version; it may or may not work but is worth a try.

---

### Post by toneykg on 2015-02-09
As stated i get grub menu and have tried selecting other listed ver, no joy
if only i could just copy the paper but can access info as live cd does recognize drive 
tried install Boot repair but it will not install
Unable to locate package
also have some errors on download Not Found [IP: 91.189.92.200 80]

connecting via wireless via live cd
any suggestions?

---

### Post by toneykg on 2015-02-09
Tried to load via netboot, no luck
i did however manage to load 14.04.1 to usb and boot from that
if i reload 14.04.1 will it merge with 14.04.2 or load as 2 separate bootable versions?
was hoping 14.04.01 would repair 14.04.2 but it looks like it will load as separate version instead of repairing 14.04.2
So do ihave to wait until official release of 14.04.2 in order to attempt fix of current loaded 14.04.2

Still unable to access 1404.02 build
Error mounting /dev/sda2 at /media/ubuntu/ad97bb82-c61c-4035-b56a-80d8f189e54c: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/ubuntu/ad97bb82-c61c-4035-b56a-80d8f189e54c"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Suggestions on to get it working again? after much "thats the best excuse you can come up with" i got an extension to friday
so i have a couple of days to fig this out
Was really hoping the usb ver would repair installed ver but it reads like it will install alongside it vs fixing it due ver diff usb 14.04.1, installed 14.04.2

HELP

TIA
Kim

---

### Post by Gvarelov on 2015-02-09
So if I understood correctly, you get the GRUB menu? If so, get to the GRUB command line by pressing "c" at the GRUB menu and list all env variables by issuing the "set" command. Take notice of values for prefix and root. Then, list all the devices that GRUB recognizes at boot time by issuing command "ls". This will list, among other things, partitioning as seen by GRUB- this is the key, GRUB's view may differ from OS's view. Partitions would probably be listed as (hd0,msdos1) and (hd0,msdos5) if you set up LVM at install time. And then, the magic:
```
set root=the_value_you_got_from_running_the_set_command
set prefix=the_value_you got_from_running_the_set_command
insmod normal
normal

```
after which you should be booting into the default menu entry that GRUB was set to boot into at install time.

---

### Post by Gvarelov on 2015-02-09
If this solves your problem, this is a one- time solution. Permanent solution would be to reinstall GRUB, but this time in the MBR and not on a partition, as I suspect is the case.

---

### Post by toneykg on 2015-02-09
ok finally got boot repair to work, so it boots again
but why does it always bring up grub screen now?
and i have an issue with ext 4 being to far into drive as reported by boot repair
but it is working
so how do i lose to grub screen on boot and fix partion issue?
not an expert thou i do have gparted, just dont want to make things worst
thnx for help thus far
how would i get boot repair to install grub in MBR  vs partition?

---

### Post by Gvarelov on 2015-02-10
> **toneykg said:**
> ok finally got boot repair to work, so it boots again
but why does it always bring up grub screen now?
and i have an issue with ext 4 being to far into drive as reported by boot repair
but it is working
so how do i lose to grub screen on boot and fix partion issue?
not an expert thou i do have gparted, just dont want to make things worst
thnx for help thus far
how would i get boot repair to install grub in MBR  vs partition?
What do you mean by "GRUB screen"? Is it a list of kernels that it waits for you to choose to boot? Is it grub prompt that is waiting for your commands?
Oh you definitely need to install GRUB into MBR if you have multiboot. When GRUB is on a partition, it is a subject of OS's manipulation with data blocks and it isn't something you have control over. By moving GRUB onto MBR, it is out of reach of the OS, so all the information about files that GRUB needs to read is intact and correct. So at the terminal prompt, issue:
```
sudo grub-install /dev/sda
```
which installs GRUB in the MBR.
Alternatively, you'd like to try using UUID's for filepaths critical to GRUB, but that requires digging through GRUB2 official documentation. Which isn't bad but it is something I am not willing to do now...
P.S. This is I think 3rd or 4th topic I've seen on GRUB and boot problems on this forum only today, and I hope (but doubt) that Ubuntu developers are reading this forum. The fact that this many users are having a hard time with booting tells you that there's something rotten within the code that is distributed around.

---

### Post by oldfred on 2015-02-10
It seems first question should be how to do backups. If your data is at all important you should have a good backup procedure. Hard drives fail, systems fail, users make mistakes and backups are often only recourse. At least copy most important data to DVD and flash drives on a regular basis.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

If you only have one install & grub menu keeps appearing it says there are other issues.

The far from start of drive issue is only for some BIOS, usually older or sometimes USB boot drives where a boot file may be beyond the first 137GB of drive. Often better to have a smaller / (root) of 25GB and then separate /home or /mnt/data partition.

Post link to the Summary report from Boot-Repair.

---

