---
title: "Does the system mount what is in /etc/fstab in the order the lines are entered?"
date: 2015-10-26
forum: General Help
---

### Post by mikodo on 2015-10-26
Hello everyone.

*If the answer to the topic question is YES, you probably won't have to read anymore. I would appreciate a yes response if so, though.


I am trying to figure out how I will cryptosetup with LUKS partitions for my hard-drive except, the small UEFI boot partition on sda. In that drive I will want to install my Ubuntu OS on sda1 partition. My data partition will be on sda2 partition and my ~ will have a symbolic link to it.

Following [this guide]("https://www.debian-administration.org/article/469/How_to_set_up_an_encrypted_filesystem_in_several_easy_steps") as an example, though I will probably dm-crypt the whole drive at once, except for the UEFI boot partition, I will need to edit /etc/fstab to mount it at boot. I want to use a GPT partitions, (GUID), rather than LVM.

Something like this:

```
/dev/mapper/GUID=a.bunch.of.numbers.for.sda1 /mnt/GUID=.same.numbers.for.sda1 ext4 defaults 0 2 
```

I assume my / partition will automagically mount on sda1 after I tell ubiquity to install it there. I have no plans to have a swap partition.

Then do the same for sda2, something like this:

```
/dev/mapper/GUID=a.bunch.of.numbers.for.sda2 /mnt/GUID=.same.numbers.for.sda2 ext4 defaults 0 2 
```

Edit: I deleted the fstab entry that would mount sda2 a second time. Well duh! I don&#8217;t need to, because would be already mounted when it is un-encrypted.

Question:

If I have the edit to /etc/fstab in this order, upon booting the system will it mount the partitions in the order I have it listed?


Thank you.

---

### Post by TheFu on 2015-10-26
A few  months  ago, I attempted  to manually setup encryption on a 14.04 server and found that none  of the guides seemed to work. There were conflicting instructions, old instructions, and just wrong instructions. Manually mounting the encrypted partitions wasn't an issue, but getting grub, crypttab, and fstab and whatever pixie-dust working together to prompt for a passphrase a boot failed completely. Perhaps I'm just stupid.

In the end, backed up my system, did a fresh install with manual partitioning + encryption and had the installer handle everything. That has been working for months.  Added a HW device, yubikey, to unlocking the dm-crypt last week and all is still good.  dm-crypt has 8 different slots for different decrytion passphrases to gain access. Good for multi-user systems or alternative security devices to be used for decryption  pre-boot.

Perhaps seeing how it fits together will  help?
```
$ lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9500;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
    &#9492;&#9472;c720--vg-lv--Stuff (dm-3) 252:3    0    50G  0 lvm   /Stuff

```
sda2 is purely for alignment needs.

---

### Post by mikodo on 2015-10-26
> **TheFu said:**
> 
  placeholder

I've been up all night reading on this and it's 08:45 now. Though tired, the chart helps.

I thought ubiquity only installed dm-crypt on top to of the file system. Good to see it on sda5 below the lvm's, and to know you found it easy to do with ubiquity. I am still waiting for sometime around the 16.04 first point release to fresh install. But, I like to read and plan ahead.

Thank you.

---

### Post by mikodo on 2015-10-26
@TheFu.

While I have you here, can I use UEFI with GPT instead of LVM's on top of dm-crypt? Seems all guides suggest LVM's and I know you use use them. Is it a necessity or, is it possibly just what geeks like? That's a term of endearment by the by.

I've only used mbr UUID partitioning before.

Thank you again.

---

### Post by TheFu on 2015-10-26
Each partition would be encrypted separately. That means unlocking each separately.  LVM lets us have a single partition per physical disk to make that easier. LVs can be thought of a highly flexible partitions that can be resized (up/down) often without impacting a  running OS.  LVM is about flexibility.  It can be extremely complex, but it can be setup to be very simple too.

I use LVM on physical installs when it is easy. There are many reasons for LVM - snapshots, flexibility, resizing are just a few.

GPT doesn't matter. The installer switched my disk to msdos from GPT. That part wasn't my specific choice. It was GPT. Perhaps I missed a checkbox? I prefer GPT for many reasons. I'll probably backup/restore this system in a few weeks - going to a security conference and last year at  the same conference, my fully-patched ubuntu netbook was cracked during a CTF/KoTH competition by a competing team.

UEFI doesn't matter. I'm on a UEFI chromebook, but to boot a non-chromeos  OS, legacy boot is required on my hardware.

Good questions.

---

### Post by mikodo on 2015-10-26
I am going to wrap this up and mark the thread as solved. Solved because:

The responses of TheFu, told me I can do this with ubiquity on my next install. I don't have to do it all myself by cli pre or post install. With that, for now I don't need to worry about editing /etc/fstab if I let Ubiquity do it for me if, I must.

More importantly for me is, that from the responses, I have had many other questions answered. I will keep learning about LVM, dm-crypt, UEFI BIOS as Ubiquity uses syslinux as BIOS boot loader that attends to however things need to be set with UEFI, for booting upon install. 

Key for this thread is, with a little bit more learning, I should be able to have dm-crypt with LUKS on bare-metal before the partitions after the boot process and can *fumble through trial installs until I get it right if, need be. I can let the installer attend to setting up the mounting of partitions. (I did read about a way to use dm-crypt to encrypt the boot partition too, over in Arch but, maybe when I am a hundred years old, it will become more main-stream and, there will be easier documentation, on how to do this).

To know that, "dm-crypt has 8 different slots for different decrytion passphrases to gain access. Good  for multi-user systems or _alternative security devices to be used for  decryption  pre-boot_" has me thinking! But, that is not for discussion in this thread, either.

Thank you, TheFu.

Thank you, admin/mod for jailing my double post. I did have about twenty tabs open with my VPN internet connection, and things were slow.

---

### Post by TheFu on 2015-10-26
If you use a security device that can output a long-ish passphrase, be certain that more than that device is needed to unlock the disk -
* something you have (a yubikey?)
    +
* something you know (pre-pend a passphrase that isn't used anywhere else)

---

### Post by mikodo on 2015-10-26
Read it. Thank you.

---

