---
title: "Media not found"
date: 2022-02-15
forum: General Help
---

### Post by sprx-77 on 2022-02-15
I am running ubuntu 20.4.  I installed it over windows, removing windows during the install.  It has been running fine for for several months now.  I decided to make a windows install disk as I was debating if I wanted to put windows back and have dual boot.  I ran etcher to burn the win iso to an SD card. Popped up with a warning that said something along the lines of needing to do this from a windows machine.  I got distracted (girlfriend or dog cant remember which) and think I dropped something on the keyboard.  In summary ubuntu wont boot.  I get checking media, no media found when I try to boot the machine.
[LIST]
[*] I can get to the setup screen (F7) 
[*] holding shift while booting does nothing, goes to check media... so sounds like no boot loader 
[*] i put in the ubuntu USB - I can boot to the USB and can see files on my hard drive 
[*] installed boot-repair, results of that: [https://paste.ubuntu.com/p/4Zrv96vzfx/](https://paste.ubuntu.com/p/4Zrv96vzfx/) 
[/LIST]

I am not sure why it is saying the following if **mmcblk1** is my USB
> The default repair of the Boot-Repair utility would reinstall the grub2 of
mmcblk1p2 into the MBR of mmcblk1.

in the blockers section it says:
> 
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

so in installed gparted and ran it

two drives are listed 
**dev/sda** - assuming this is my hard drive
**dev/mmcblk1** - and this is the USB

When I try to create a partition on **dev/sda** all options are greyed out except unmount and a few other information menu items
I tried to unmount and get
> 
[SIZE=3]**Could not unmount /dev/sda1**[/SIZE]
# unmount -v'/cdrom'
unmount: /cdrom: target is busy.

With the **/dev/sda** drive selected, under the** /dev/sda1** partition it lists
Partition: /dev/sda1
little key picture
Name: Main Data Partition
File System: fat32
Mount Point: /cdrom
Flags: boot, esp  (I think I added the boot flag)

I have looked through other posts on this topic, but this is getting above my knowledge base and worried I am going to f up my computer. I am not sure where to go from here.

---

### Post by tea for one on 2022-02-15
[COLOR="#0000FF"]Line 28[/COLOR] - OS#1:   Ubuntu 20.04.3 LTS on mmcblk1p2

/dev/sda is your usb device
/dev/mmcblk1 is your internal drive

Your installation is old style mbr not UEFI mode with ESP.

[COLOR="#0000FF"]Lines 236-237[/COLOR] - The default repair of the Boot-Repair utility would reinstall the grub2 of
mmcblk1p2 into the MBR of mmcblk1.

Have you tried the default repair?

---

### Post by sprx-77 on 2022-02-15
I have run boot-repair and clicked the button "Recommended Repair (repairs most frequent problems)" . It runs for a few seconds and then gives me the error "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."  Not sure if that is default repair.

---

### Post by Impavidus on 2022-02-16
Your system is installed on mmcblk1, so that's partition 1. There is no partition 0. sda is your live disk. Your /etc/fstab mentions an /boot/efi partition, but no such partition exists. The first 500MB of your drive are unallocated. Your live sessions runs in efi mode, your hard drive appears to use gpt partitioning and Windows only uses gpt with efi mode. So it looks like your system is in efi mode on a gpt partitioned drive, but you somehow lost your efi partition.

Maybe you can create a new efi partition and put the right UUID in your /etc/fstab to mount it, then maybe boot-repair sees how to fix it.

---

### Post by tea for one on 2022-02-16
[s][COLOR="#0000FF"]Line 250[/COLOR] - Final advice in case of suggested repair: [/s]
[s][COLOR="#0000FF"]Line 252[/COLOR] -The boot of your PC is in UEFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.[/s]

[s]Boot the USB in mbr mode and try the default repair.[/s]

You could also take this opportunity to start from scratch.
Back up your personal data.
Install Ubuntu in UEFI mode with GPT 
More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and [https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)
> **sprx-77 said:**
> I was debating if I wanted to put windows back and have dual boot

If you decide to install Windows 10, the Windows 10 install USB will automatically choose UEFI mode with GPT.

In essence, to dual boot Windows 10 and Ubuntu, it would be advisable to back up and start with a clean slate.

---

### Post by tea for one on 2022-02-16
> **Impavidus said:**
> Your system is installed on mmcblk1, so that's partition 1. There is no partition 0. sda is your live disk. Your /etc/fstab mentions an /boot/efi partition, but no such partition exists. The first 500MB of your drive are unallocated. Your live sessions runs in efi mode, your hard drive appears to use gpt partitioning and Windows only uses gpt with efi mode. So it looks like your system is in efi mode on a gpt partitioned drive, but you somehow lost your efi partition.

Maybe you can create a new efi partition and put the right UUID in your /etc/fstab to mount it, then maybe boot-repair sees how to fix it.

I think that Impavidus has spotted something which I did not notice.

[COLOR="#0000FF"]Line 54[/COLOR] - mmcblk1	: is-GPT,	no-BIOSboot,	has-noESP, 	not-usb,	mmc-disk, has-os,	no-wind,	1 sectors * 512 bytes
[COLOR="#0000FF"]Line 131 [/COLOR] - # /boot/efi was on /dev/mmcblk1p1 during installation

Did you modify your partition mmcblk1?

---

### Post by HermanAB on 2022-02-16
First, make a backup of your data.

---

### Post by sprx-77 on 2022-02-16
> **Impavidus said:**
> 
Maybe you can create a new efi partition and put the right UUID in your /etc/fstab to mount it, then maybe boot-repair sees how to fix it.
Can you explain what you mean by the right UUID and how I put that in my /etc/fstab?

---

### Post by sprx-77 on 2022-02-16
> **tea for one said:**
> I think that Impavidus has spotted something which I did not notice.

[COLOR=#0000FF]Line 54[/COLOR] - mmcblk1    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    mmc-disk, has-os,    no-wind,    1 sectors * 512 bytes
[COLOR=#0000FF]Line 131 [/COLOR] - # /boot/efi was on /dev/mmcblk1p1 during installation

Did you modify your partition mmcblk1?
no, not that I am aware of

---

### Post by sprx-77 on 2022-02-16
> **tea for one said:**
> 
 You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.[/s]

really do not want to start from scratch!

---

### Post by Impavidus on 2022-02-17
> **sprx-77 said:**
> Can you explain what you mean by the right UUID and how I put that in my /etc/fstab?

Once you have re-created an EFI partition (use the unallocated 500MB at the start of your drive, partition type FAT32), you find the UUID (universal unique identifier) of the filesystem in that partition. It's a code of two blocks of letters and digits. I think gparted (the tool you use for creating the partition) can tell you, or you can use```
sudo blkid
```

In your /etc/fstab of the installed system you can find the lines```
# /boot/efi was on /dev/mmcblk1p1 during installation
UUID=B860-35F7  /boot/efi       vfat    umask=0077      0       1
```
Replace the UUID in that file (currently B860-35F7) with the UUID of the new EFI partition. Maybe then boot-repair will recognise this as an efi install and reinstall the boot loader. Otherwise, you have to reinstall the bootloader manually, which is something I've never done, but it doesn't appear to be very hard.

There's nothing scary about starting from scratch, but I think this can be repaired.

---

### Post by sprx-77 on 2022-02-19
Process to far:



[LIST]
[*]used gparted to create a fat32 partition in the first unallocated 512 MiB partiion, named boot
[*]used gparted to add the boot flag (eps flag was automatically selected so I left it selected) to the newly created partition
[*]reran the boot-repair tool and clicked the default repair, it ran to completion
[LIST]
[*][https://paste.ubuntu.com/p/HXp2k38hv9/](https://paste.ubuntu.com/p/HXp2k38hv9/)
[/LIST]
[/LIST]


SHUTDOWN, removed Live USB
RESTART
computer locked on restart with


```

BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu6.4) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) [172.199182] watch dog: BUG: soft lockup - CPU#1 stuck for 160a! [systemd-udevd:157]
_
]
```


POWER OFF AND BACK ON, Ubuntu rebooted from hard drive things were running glithcy so I ran
```

sudo apt update

```
the following error was repeated multiple times during the update process
```

libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with ':options'

```


opened the iwlwifi.conf, contents:
```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
“options iwlwifi 11n_disable=1”

```
commented out the last line
```

#“options iwlwifi 11n_disable=1”

```


cycled through following a few times
```

REBOOT
sudo apt update
sudo apt upgrade

```
Things seem to be running well, I need to figure out what is up with the iwlwifi.conf file, but I think I can figure that out on my own.


Three things to finish up:

[LIST=1]
[*]Any thing I need to do with the initial errors on the reboot after boot-repair?
[*]There is an unallocated 1.00 MiB partition at the end mf my mmbcblk1 drive, Do I need to do anything?
[*]Is there anything in [https://paste.ubuntu.com/p/HXp2k38hv9/](https://paste.ubuntu.com/p/HXp2k38hv9/) that I need to adress?
[/LIST]

---

