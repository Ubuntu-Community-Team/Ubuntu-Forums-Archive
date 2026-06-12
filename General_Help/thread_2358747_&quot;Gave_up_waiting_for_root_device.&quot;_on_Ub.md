---
title: "&quot;Gave up waiting for root device.&quot; on Ubuntu 16.10 and 17.04"
date: 2017-04-16
forum: General Help
---

### Post by terminalone on 2017-04-16
Hello all,

I'm getting the following when I try to run Ubuntu after a fresh install. Tried ubuntu 16.10 or 17.04:

```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/<<uuid>> does not exist. Dropping to a shell!


```
Any hints? I tried searching StackOverflow and these forums. No luck, finally had to make this thread. :(


If I chroot then I get:
```
root@ubuntu:/# cat /proc/cmdline 
initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --- BOOT_IMAGE=/casper/vmlinuz.efi 
root@ubuntu:/# sudo blkid
sudo: unable to resolve host ubuntu: Connection refused
/dev/sda1: UUID="04f51618-f071-4f7d-9f6e-0d1f4f1cf5fd" TYPE="ext4" PARTUUID="26cd37c7-01"
/dev/sda5: UUID="0c8cc2e9-3a30-4632-92d6-80d309cc2f3d" TYPE="swap" PARTUUID="26cd37c7-05"
/dev/sdb1: LABEL="UNTITLED" UUID="7630-19FA" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
root@ubuntu:/# 


```

sudo fdisk -l gives me (my OS installed HDD is the 16 gb one, USB stick is 32gb):
```

Disk /dev/loop0: 1.4 GiB, 1536229376 bytes, 3000448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.9 GiB, 16013942784 bytes, 31277232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x26cd37c7

Device     Boot    Start      End  Sectors Size Id Type
/dev/sda1  *        2048 23001087 22999040  11G 83 Linux
/dev/sda2       23003134 31277055  8273922   4G  5 Extended
/dev/sda5       23003136 31277055  8273920   4G 82 Linux swap / Solaris


Disk /dev/sdb: 29.8 GiB, 32027705344 bytes, 62554112 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *        2 62554111 62554110 29.8G  b W95 FAT32
ubuntu@ubuntu:~$ 


```

In chroot other commands:
```

root@ubuntu:/# cat proc/cmdline 
initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --- BOOT_IMAGE=/casper/vmlinuz.efi 


```

```

root@ubuntu:/# cat /etc/default/grub 
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
root@ubuntu:/# 



```

[ATTACH=CONFIG]274597[/ATTACH]

---

### Post by deadflowr on 2017-04-17
The grub cmdline argument looks  normal.
I think you should look at the root device and uuid setting.
Use Boot-info and post the pastebin link it gives you at the end in this thread
Boot-info: [https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")
This should give us an idea of the relation of the partitions and grub.

---

### Post by terminalone on 2017-04-17
Thanks for the quick response! Here you go:[ http://paste2.org/FyLw4Fmj]("http://paste2.org/FyLw4Fmj")

---

### Post by terminalone on 2017-04-17
I also tried doing the following from the Ubuntu "Rescue / Try" disk:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu: Connection refused
Installing for i386-pc platform.
Installation finished. No error reported.
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu: Connection refused
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-22-generic
Found initrd image: /boot/initrd.img-4.8.0-22-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# 



```

---

### Post by terminalone on 2017-04-17
I just installed 14.04 and that went okay. What could this be? old hardware issue?

---

### Post by oldfred on 2017-04-17
I did not see anything wrong either.
Should not be a hardware issue, but sometimes there are regressions.

Was there some reason to use ext3. 
I thought I saw some discussion on discontinuing the ext3 driver and using only the ext4 driver for ext3 partitions. Did not know they were different drivers in first place and if they did change perhaps that has a regression?

---

### Post by terminalone on 2017-04-17
> **oldfred said:**
> I did not see anything wrong either.
Should not be a hardware issue, but sometimes there are regressions.

Was there some reason to use ext3. 
I thought I saw some discussion on discontinuing the ext3 driver and using only the ext4 driver for ext3 partitions. Did not know they were different drivers in first place and if they did change perhaps that has a regression?

I tried ext4 and ext3, the reason I went with ext3 in this one was because someone on AskUbuntu said that ext3 worked for them (thought it seems like a red herring). 

Currently I'm trying to do an update from 14.04 to 17.04, I will let you know how it goes. If there is anything I can still try to do provide the output of, please let me know. Also if somehow we can identify the regression that would also be great!

---

### Post by terminalone on 2017-04-19
[B]

[SIZE=4]The solution for me was to use a different USB stick to install Ubuntu.[/SIZE] 

 [/B]The one I had is 32GB, seems like it was causing issues. Switched to a 16GB USB Stick and stuff installed correctly

---

