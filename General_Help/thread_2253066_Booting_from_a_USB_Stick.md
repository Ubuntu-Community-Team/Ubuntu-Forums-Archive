---
title: "Booting from a USB Stick"
date: 2014-11-17
forum: General Help
---

### Post by hop5uk on 2014-11-17
My Ubuntu 12.04 server will not boot. No one seems to know how to boot on to a live CD or by using the rescue mode and fix this problem so know i am desperate. If i plug a USB stick in and reinstall Ubuntu on the stick, can i boot onto it and  have access to 3 x Raid 5 arrays that i have for storage on the Server?

---

### Post by oldfred on 2014-11-17
Do not know server disk. I think it has its own repair mode.

But you can download the desktop version (best if same version of Ubuntu) which is also a live installer. But you will have to add RAID drivers to be able to mount your RAID as desktop version does not directly support RAID.

From live version download & run the summary report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lisati on 2014-11-17
The last time I installed a server from scratch, the installation disk didn't have a "live" mode..... :( As has already been suggested, using the live mode of a regular desktop installation disk might be an option.

---

### Post by hop5uk on 2014-11-17
I can easily boot to the live USB stick (desktop) and get into the terminal. I followed the boot-repair link that oldFred posted but i run into difficulties.My Operating system is on a pair of Raid 1 disks and the first thing that came up was "RAID detected. You may want to retry after installing the [mdadm] packages (sudo apt-get install-y-forcemdadm-no-install-recommends)". I typed this command and it allowed me to proceed. At this point i got an icon in the toolbar for the Raid 1 array as well as one of my Raid 5 arrays that i use for storage. It is important to note that these two arrays are connected via the SATA ports on the motherboard. I also have 2 more raid 5 arrays that are connected to an IBM m1015 controller card which i am desperate to get access to but cannot see now.
I continued waiting for the process to complete and then i got another pop up box which says "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be perfomed via tools such as Gparted. Then try again"
I managed to get install GParted butit wont really let me create anything and to be honest i am a little nervous to relly push it further.
I also used the boot-repair programme to create the url for diagnostics
It is [http://paste.ubuntu.com/8963156](http://paste.ubuntu.com/8963156)
I have a lot of personal files on this server and would really appreciate any help that you could offer. I don't think the boot problem is that serious, i just need someone who knows how to do it.
I

---

### Post by oldfred on 2014-11-17
Not sure where Boot-Repair is trying to install grub. 
If it is trying to install to the MBR of standard non-RAID drive and drive is gpt then you need the bios_grub partition. And you can create that with gparted.
But with RAID you cannot use gparted.

And Some with RAID do have a separate /boot partition or drive outside of the RAID and that is like a standard install. But others use the newer grub2 which has its own RAID drivers and can be inside the RAID.

Also if more than one drive, do not run autofix. That does try to install grub to every MBR which in most cases users do not want.

What drives do you boot from md1? Then grub should be reinstalled to that. You have to mount / & /boot md partitions if seperate and install grub to root of md drive not to MBR of hard drive unless you have boot outside of RAID.

---

### Post by hop5uk on 2014-11-18
The /proc/mdstat file currently contains the following:

[B]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sdg1[6] sdh1[7] sdi[5]
      8790402048 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [4/3] [UUUU]

md4 : active raid5 sdk1[1] sdj1[0] sdl1[3]
      3906762752 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [3/3] [UUU]

md1 : active raid1 sdb2[1] sda2[2]
      46864256 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdb1[1] sda1[2]
      15615872 blocks super 1.2 [2/2] [UU]

md3 : active raid5 sdf1[4] sde1[3] sdc1[0] sdd1[5]
      4395018240 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [4/4] [UUUU][/B]

You can see that the Raid array containing the operating system is on md0 and md1. I took a look at it on gparted and the first partion was the swap partion with the second set aside as linux autoraid. Don't know if this helps?
md2, md3 and md4 are Raid 5 arrays for storage.

---

### Post by oldfred on 2014-11-18
I do not know RAID, but you have to use mdadm and mount / (root) if md1 or md2 and /boot if md1 (if you have it) and install to md. I thought Boot-Repair gave you those as options. It still may default to a MBR but do not use that.
Gparted only shows the underlying partitions not the partitions inside the RAID.

---

