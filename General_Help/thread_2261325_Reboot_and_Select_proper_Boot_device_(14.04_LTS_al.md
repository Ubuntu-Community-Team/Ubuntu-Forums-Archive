---
title: "Reboot and Select proper Boot device (14.04 LTS already successfully installed)"
date: 2015-01-18
forum: General Help
---

### Post by jefflawshe on 2015-01-18
I have Ubuntu 14.04 LTS and it's been working fine for months. Today I was updating Handbrake to rip a DVD and restarted my system in the middle of trying to get the DVD to eject. On reboot, I received the message "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key..." I removed all media, closed up the DVD drive, and tried to reboot several times, still with no luck.

I created a live boot-repair-disk USB stick and it said it fixed errors, but on restart I still received the same message. Here is the report from boot-repair-disk:

[http://paste.ubuntu.com/9773283/](http://paste.ubuntu.com/9773283/)

Any suggestions would be much appreciated. I can find my way around the Ubuntu GUI and terminal with detailed instructions, but I'm in over my head with this kind of a problem.

Thank you!

-Jeff Lawshe

---

### Post by oldfred on 2015-01-18
If system hangs always remember the elephants to try to get a normal shutdown, or go into top to find process and kill process having issue.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)

Your summary report shows no boot files or Linux partition with fstab. Not sure if because it could not mount it or if other issues. But you have gpt partitioning, and no efi partition for UEFI boot nor a bios_grub partition for BIOS boot. You have to have one or the other depending on how you boot from a gpt drive.

      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

     
    
Post this:
 sudo apt-get install gdisk
sudo gdisk /dev/sda -l
sudo gdisk /dev/sdb -l

---

### Post by jefflawshe on 2015-01-18
Thank you so much! I will absolutely use RSEIUB next time. 

Here are the results of the gdisk commands:

[FONT=lucida console]ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdisk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo gdisk /dev/sda -l
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7D3A3E32-D1A4-4D65-A73A-94D98C563EAD
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 586056557 sectors (279.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5242478591   2.4 TiB     0700  
   2      5242478592      5274478591   15.3 GiB    8200  
ubuntu@ubuntu:~$ sudo gdisk /dev/sdb -l
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F8BDC94B-8DFD-11E2-B2A8-002590139F16
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      1953523711   931.5 GiB   0700  Basic data partition
ubuntu@ubuntu:~$  [/FONT]

---

### Post by oldfred on 2015-01-19
I thought maybe backup gpt might not match primary and you could recover something.

But you do not have a bootable Linux partition nor any boot files. Or it seems a couple of partitions are missing. There is a bit of space at the end of sda, was it fully partitioned?
If so you can see if testdisk shows any missing partitions. If you changed partitions, it shows all versions, so best if you know your partition layout to recover the correct set of partitions.

       [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by jefflawshe on 2015-01-20
Just wanted to thank you again for responding to this OldFred, and I'm sorry I'm not a person with the kind of patience your generosity deserves. I have my data on CrashPlan, so I've decided to take the nuclear option and do a fresh install. Again, thank you.

---

### Post by oldfred on 2015-01-20
Always best to have good backups.
 :)

---

