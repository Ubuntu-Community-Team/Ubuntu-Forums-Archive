---
title: "Blank purple screen at startup, no grub menu"
date: 2017-04-03
forum: General Help
---

### Post by lysander6662 on 2017-04-03
One thing since my reinstall yesterday. Everything seems to be doing well, and all updates have been configured on 16.04.2. But when I start the comoputer I just see a blank purple screen for a couple of seconds, no grub menu. Is this an issue? After this it just boots to Ubuntu as normal. 

Should I be worried about this or is it OK? I've read around and some people say it's to do with nvidia cards, but I'm using ATI.

---

### Post by yancek on 2017-04-03
It's normal when Ubuntu is the only operating system on the computer.  If you want to access the menu, holding down the Shift key during boot should do it or repeatedly pressing the Esc key.  More details on this at the Ubuntu documentation site below.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by lysander6662 on 2017-04-03
Thank you for that. What if I wanted to show the grub menu by default on startup? These are the contents of the file

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by ajgreeny on 2017-04-03
I have a UEFI system with Xubuntu only installed and it was difficult to get the grub menu to show by pressing any key at boot so I edited my /etc/default/grub file to include the following contents, then ran **sudo update-grub** to allow the changes to take effect.
```
GRUB_DEFAULT=0
#Next line will make the countdown time show menu by default
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to 2 for 2 second delay
GRUB_HIDDEN_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="Xubuntu-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
This forced the grub menu to show for just two seconds, a delay which I was prepared to "suffer" in order to have the option to boot to an older kernel or troubleshoot if needs be.
I think this should work whether using UEFI or BIOS.

---

### Post by lysander6662 on 2017-04-03
Very nicely explained, though how do I edit it? Log in as root in the terminal?

---

### Post by vasa1 on 2017-04-03
> **lysander6662 said:**
> Very nicely explained, though how do I edit it? Log in as root in the terminal?

Avoid "log in as root", whatever that means. Use *sudo* to temporarily gain elevated privileges.

So, ```
sudo -H gedit /etc/default/grub
``` is what you'd run from a terminal.

---

### Post by lysander6662 on 2017-04-04
Thanks for that. I don't know what happened, but earlier I ran sudo apt update and it identified four grub updates. I ran them, rebooted, and now I get a 10 sec grub menu at startup. Maybe my OS read this thread.

---

### Post by ajgreeny on 2017-04-04
If you had already edited your /etc/default/grub file when the update of grub appeared you would have been notified that the file was in a modified state and you would have several options open to you, including to use the package's new, default version or to keep your modified version.

If you still have only the one OS on your machine you should not normally see the grub menu, so it would be interesting to see the content of that /etc/default/grub file now after the grub update.

---

### Post by lysander6662 on 2017-04-04
Sure, here's the full file:

```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

There is still, somehow, a Windows 7 loader. This is after a complete wipe and partition of the main SSD. Since there are two other NTFS hard drives linked maybe it sees those as being Windows-related?

sudo parted -l output

```
Model: ATA SAMSUNG HD160JJ (scsi)Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  106MB  105MB  primary   ntfs         boot
 2      107MB   160GB  160GB  extended               lba
 5      107MB   160GB  160GB  logical   ntfs




Model: ATA Hitachi HDP72503 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      8225kB  320GB  320GB  extended               lba
 5      8258kB  320GB  320GB  logical   ntfs




Model: ATA INTEL SSDSA2M080 (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  74.7GB  74.7GB  primary   ext4            boot
 2      74.7GB  80.0GB  5367MB  extended
 5      74.7GB  80.0GB  5367MB  logical   linux-swap(v1)

```

EDIT: I checked the grub menu, it says the W7 loader is sda1. GParted shows it's here on one of the other hard drives which is used for data storage:

[ATTACH=CONFIG]274425[/ATTACH]

---

### Post by ajgreeny on 2017-04-04
Well, I have no knowledge of Windows partitions any more having not run that OS for 12 years, and my last use of it was with XP all on a single NTFS partition, so I can't really help with removal of the Win7 bootloader, I'm afraid.

I assume from the /etc/default/grub file you show that you did not get round to editing your previous version's file, or that you chose to accept the new version from the package devs rather than keep your own modified version.

No matter really as it is, as you have now seen, a very easy task to edit it.
Be careful if you do so, however, as it could stop your boot completely if you got something totally screwed in the file.
See [https://ubuntuforums.org/showthread.php?t=1195275](https://ubuntuforums.org/showthread.php?t=1195275), [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and [http://ubuntuforums.org/showthread.php?p=12073029](http://ubuntuforums.org/showthread.php?p=12073029) for lots more info and grub configuration help.

---

### Post by lysander6662 on 2017-04-04
Thanks, I'll have a careful read through those. I'm not too bothered about the Windows bootloader. As far as I can tell from my scant reading on the matter, just deleting the partition would cause problems. I'm fine to leave it as is, it's not doing anything wrong.

---

