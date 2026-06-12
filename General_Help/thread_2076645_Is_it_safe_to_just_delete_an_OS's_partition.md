---
title: "Is it safe to just delete an OS's partition?"
date: 2012-10-26
forum: General Help
---

### Post by 25tom on 2012-10-26
I'm dual booting Ubuntu and Lubuntu;
My question is, how to remove Lubuntu while leaving my standard Ubuntu intact and able to boot?
I've looked at using os-uninstaller, but I can't find a download for it except as part of Ubuntu Secure Remix, which I don't want to have to download. Using apt-get to install os-uninstaller (after having added the repo as instructed at [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)) returned an 'unable to locate' error.
Can I just delete the partition containing Lubuntu or will this cause problems booting?
Thanks in advance for any help :)

---

### Post by grahammechanical on 2012-10-26
First of all you need to make sure that the Ubuntu grub menu is the one that controls to boot process.

Boot into Ubuntu and run these two commands:

```
sudo update-grub
```

and

```
sudo grub-install /dev/sda
```

If you only have one hard disk that second command will install the Grub of Ubuntu into the MBR of the hard disk (sda = first sata drive).

Now all you need to do is format the partition where Lubuntu resides and run

```
sudo update-grub
```

again. And you should have a grub boot menu with only Ubuntu in it. I am assuming that there are only these two operating systems on your computer.

Regards.

---

### Post by dino99 on 2012-10-26
formating the partition is the easiest/fastest way, but it needs to be done on an unmounted partition.
also grub will next be confused and you need : uninstall it then to reinstall it, so be ready with a livecd/usb to do it. (sudo grub-install /dev/sda)

---

### Post by dannyboy79 on 2012-10-26
> **25tom said:**
> I'm dual booting Ubuntu and Lubuntu;
My question is, how to remove Lubuntu while leaving my standard Ubuntu intact and able to boot?
I've looked at using os-uninstaller, but I can't find a download for it except as part of Ubuntu Secure Remix, which I don't want to have to download. Using apt-get to install os-uninstaller (after having added the repo as instructed at [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)) returned an 'unable to locate' error.
Can I just delete the partition containing Lubuntu or will this cause problems booting?
Thanks in advance for any help :)
Which versions of Ubuntu and Lubuntu are you using?
Then we need to know what your HDDs look like
what are the results of the commands?
this will show us all your plugged in hard disk drives and their partition setups
```
sudo fdisk -l
```

also show us the contents of /etc/default/grub file using this command (note, if you can't due to it being owned by root, use sudo -i (enter your users password) to temporarily gain root privilages.
```
cat /etc/default/grub
```

when done with above command, type
```
exit
```
so that you return to being your normal user and no longer have rot access.

Good luck

---

### Post by 25tom on 2012-10-27
sudo fdisk -l:
```
Disk /dev/sda: 50.0 GB, 50018393088 bytes
255 heads, 63 sectors/track, 6081 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be212

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5031    40408442+  83  Linux
/dev/sda2            5031        6082     8435713    5  Extended
/dev/sda5            6021        6082      489472   82  Linux swap / Solaris
/dev/sda6            5031        5960     7455744   83  Linux
/dev/sda7            5960        6020      488448   82  Linux swap / Solaris

Partition table entries are not in disk order
```

sudo cat /etc/default/grub:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

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

I ran those commands in Ubuntu in a terminal.
I have Ubuntu 11.04 and Lubuntu 11.10.

---

### Post by The Cog on 2012-10-27
grahammechanical is right.

After the first two commands he gives, you could either reformat the Lubuntu partition (if you wand to re-use it), or you could delete it with a partition editor such as gparted.

I don't see any point in having two swap partitions, so you might as well delete sda7 while you're at it. But check use the command
swapon -s
to see which one you are actually using.

---

### Post by 25tom on 2012-10-27
> **The Cog said:**
> grahammechanical is right.

After the first two commands he gives, you could either reformat the Lubuntu partition (if you wand to re-use it), or you could delete it with a partition editor such as gparted.

I don't see any point in having two swap partitions, so you might as well delete sda7 while you're at it. But check use the command
swapon -s
to see which one you are actually using.

OK, thanks for help! :) :)

---

