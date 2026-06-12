---
title: "Is possible create an partition for HOME being default for installation ?"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
Is possible create an partition being HOME where for any system installation look to that partition and configure the HOME folder to that partition ?
I wait create in a GPT disk first partition start, second the system and third the HOME partition for data and software backups.
Thanks for reply.

---

### Post by gdesilva on 2020-08-05
Certainly can but would need to use 'Something Else' option at installation time (of hack the /etc/fstab if you want to do it later on). Select the partition where you want the /home, select 'Use this partition' and indicate the mount point which will be /home in this case.

---

### Post by CelticWarrior on 2020-08-05
The installer defaults now to a single partition (root or "/") where /home is just a folder inside the root partition and swap no longer needs a separated partition because now Ubuntu uses a *swapfile *by default.

So, any deviation from this standard requires the users installing the system to select "something else" and create their own partitioning layout as explained above. Users must have solid knowledge about the requirements, MBR vs. GPT partitioning, partitions and file systems in general and how that applies to Ubuntu, otherwise expect problems.

---

### Post by oldfred on 2020-08-05
It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Or use gdisk which is in repository, now standard in newer installs:

New installs now use swap file, so swap partition not required. A few still like a 4GB swap partition, particularly if server or you have server software.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.
1. 30+ GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB or all (See below if 18.04 or later) Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
4. You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
5. No swap partition for 18.04 or later, it uses a swap file like this entry in fstab:
     /swapfile                                 none            swap    sw              0       0

For general UEFI install instructions, see link below in my signature.

---

### Post by aug7744 on 2020-08-13
Thanks very much :)

---

