---
title: "EFI Partition(s) on dual boot machines"
date: 2018-02-27
forum: General Help
---

### Post by rbmorse on 2018-02-27
I should know the answer to this, but I can't find a definitive answer with my search skills. 

Setting up a new machine.  Has two internal mass storage devices.  Windows X will go on /dev/sda.  Ubuntu 17.10.1 will go on /dev/sdb. Company policy (not mine) dictates that the machine have secure boot enabled and compatibility mode disabled. 

Windows will create an ESP on /dev/sda2 when it installs.  My question is, will GRUB detect and enumerate both O/S' if I create an appropriately sized, formatted, labeled and flagged ESP partition at /dev/sdb1 and tell the Ubuntu installer to install its boot files there? 

There's plenty of room in the Windows ESP, but I'd rather have Ubuntu keep everything on its own physical drive in case I decide to split them out later. 

If I had time I'd do the experiment just to see what happens, but today, unfortunately, real life intrudes but I have to get this machine going and out on the floor. 

As always, appreciate any thoughts or recommendations

---

### Post by dragonfly41 on 2018-02-27
To narrow your search go to "advanced search" at top of this page.
Set search profile ..
Keyword: UEFI
User: OldFred
and browse through posts.

---

### Post by oldfred on 2018-02-27
Ubuntu's grub only installs to ESP - efi system partition seen as sda. So typically it installs to Window's ESP.

You can either disconnect Windows drive or manually partition sdb with an ESP (default install does not add ESP to sdb) and then copy files from ESP to sdb. But many setting need changing to make that boot entry work.

Are you allowed to install Ubuntu?
You do need access to UEFI to change settings, and most companies lock that down (and should).

Install to sdb similar issues as install to external drive.
[https://ubuntuforums.org/showthread.php?t=2385802](https://ubuntuforums.org/showthread.php?t=2385802)

The only way I got Ubuntu to directly install to ESP on sdb was by disconnecting drive.
I have installed to USB flash drives & copied ESP files  to flash drive and with reconfiguration made that work.

---

### Post by rbmorse on 2018-02-27
Thanks, Fred.  A bit curious about the location of the ESP.  

I was just managed out of building this machine today...so I think I'll mark this as "solved" based upon the advice received so far.  If anything interesting develops when the powers that be actually allow me to set it up (earlier: "must be done TODAY!") I'll report back.

---

### Post by oldfred on 2018-02-27
I make an ESP & bios_grub as first two partitions on every new drive or large flash drive.
I use to use gpt with BIOS boot and needed bios_grub and then new system neeed ESP.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]

---

