---
title: "grub2 on sda AND sda1? Why?"
date: 2020-04-16
forum: General Help
---

### Post by GhX6GZMB on 2020-04-16
After a bare-metal install with 19.10, sudo update, sudo upgrade, prompts me to install grub-pc on both sda and sda1. What's this?

Thank You.

---

### Post by yancek on 2020-04-16
Do you have a GPT drive?  Is your install UEFI or Legacy?  Posting the output of either or both:  sudo parted -l  OR  sudo fdisk -l should give that information.

---

### Post by grahammechanical on 2020-04-16
Just a small point. The commands should be

```

sudo apt update
sudo apt upgrade

```

When you installed Ubuntu was grub installed? It usually is by default but if we do a manual install into a partition of our choice we have to choose where we want grub installed to. If I am remembering things correctly.

The update - upgrade commands may be programed to to update grub and if it is not in the package list it might be what is causing this message.

Regards.

---

### Post by GhX6GZMB on 2020-04-17
Thank you both.
The laptop is 100% BIOS/legacy. the output from fstab -l is

```
macro@macro-pc:~$ sudo fdisk -l
Disk /dev/sda: 223,58 GiB, 240057409536 bytes, 468862128 sectors
Disk model: KINGSTON SUV5002
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x7e408a68

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048  61442047  61440000  29,3G 83 Linux
/dev/sda2        61442048 456273919 394831872 188,3G 83 Linux
/dev/sda3       456273920 468857024  12583105     6G 82 Linux swap / Solaris
macro@macro-pc:~$ 

```

output from lsblk is:

```
macro@macro-pc:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223,6G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0 188,3G  0 part /home
&#9492;&#9472;sda3   8:3    0     6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
macro@macro-pc:~$ 

```

GPT or MBR? I honestly don't know.

BTW: yes of course it's sudo apt for the update/upgrade commands. I was a bit too fast when posting :)

Thank You.

---

### Post by oldfred on 2020-04-17
You never install grub to PBR - partition boot sector of a partition. Ok, almost never, and then grub will complain that it has to use blocklists. And systems only boots from MBR of a drive like sda, not directly from PBR, so you have to have another way to boot if attempting to install to a partition.

> Attempting to install GRUB to a partition PBR instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force


Where are you getting info that you need to install to both MBR & sda1's PBR?
Or is it just showing that as an option.

---

### Post by ajgreeny on 2020-04-17
***Disklabel type: dos*** means that your machine is using MBR formatting, not GPT.

To give us as much info as possible please show the full output of commands ```
sudo apt upgrade
sudo apt upgrade
``` which hopefully will explain more about your comment of the upgrade wanting to install grub-pc to both /dev/sda and /dev/sda1, which doesn't make a great deal of sense to me; perhaps you misinterpreted the output you saw.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by dragonfly41 on 2020-04-17
[COLOR=#000000]> GPT or MBR? I honestly don't know.

Here is a simple test command to establish if partition table is mbr/gpt

[/COLOR]```
sudo [COLOR=#242729][FONT=Consolas]parted /dev/sda print | grep Table[/FONT][/COLOR]
```[COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][found in answers here]("https://superuser.com/questions/1133040/unable-to-boot-into-windows-10-with-refind-solved").
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by GhX6GZMB on 2020-04-17
OK, as I said to start with, it's an install on a bare machine.
I've now done a reinstall from zero. The Linux installer suggests MBR on /dev/sda which makes sense. GPT is not available.

So, I have a laptop with BIOS/Legacy and MBR on /dev/sda

I'll now try update/upgrade, but I need to install screen grab first.

'til later :)

---

### Post by GhX6GZMB on 2020-04-17
Sudo apt update done, sudo apt upgrade started. During upgrade, this window pops up. What is it?

```
 The grub-pc package is being upgraded. This menu allows you to select which devices you'd like grub-install to be automatically run   &#9474;  
  &#9474; for, if any.                                                                                                                          &#9474;  
  &#9474;                                                                                                                                       &#9474;  
  &#9474; Running grub-install automatically is recommended in most situations, to prevent the installed GRUB core image from getting out of    &#9474;  
  &#9474; sync with GRUB modules or grub.cfg.                                                                                                   &#9474;  
  &#9474;                                                                                                                                       &#9474;  
  &#9474; If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.        &#9474;  
  &#9474;                                                                                                                                       &#9474;  
  &#9474; Note: it is possible to install GRUB to partition boot records as well, and some appropriate partitions are offered here. However,    &#9474;  
  &#9474; this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.                      &#9474;  
  &#9474;                                                                                                                                       &#9474;  
  &#9474; GRUB install devices:                                                                                                                 &#9474;  
  &#9474;                                                                                                                                       &#9474;  
  &#9474;    [ ] /dev/sda (240057 MB; KINGSTON_SUV500240G)                                                                                      &#9474;  
  &#9474;    [ ] - /dev/sda1 (31457 MB; /)                                                                                                      &#9474;  
  &#9474;    [ ] /dev/sdb (30752 MB; Ultra_Fit)                                                                                                 &#9474;  
  &#9474;                                                                                                                                       &#9474;  
  &#9474;                                                                                                                                       &#9474;  
  &#9474;                                                                <Ok>  
```

---

### Post by Bashing-om on 2020-04-17
ml9104; Hello -

In your use case choose the 1st option:
> 
/dev/sda (240057 MB; KINGSTON_SUV500240G)


[INDENT]my bit to help
[/INDENT]

---

### Post by GhX6GZMB on 2020-04-17
Yes, that's what I did.
But this popup is new, although I use the same .iso DVD for installing. Odd.

---

### Post by Bashing-om on 2020-04-17
ml9104;

Well, the install of the current grub is different than what the old install held. The installer just making sure of your desire for where to place the boot code.

[INDENT]smart
[/INDENT]

---

