---
title: "ubuntu 12.04 broke 2 USBflash drives help!"
date: 2013-07-02
forum: General Help
---

### Post by ande1010 on 2013-07-02
Well first a small description of what took me here:
I recently installed Ubuntu 12.04 LTS, (BTW I have used it in the past  so +/- a noob but have enough knowledge to be dangerous to my usb  drives!). FYI my Ubuntu system is a Dell optiplex 3010 and laptop with  win 7 is a Dell studio 14 

I been using several USB drives an wanted to bkp my system so I though  of clonezilla, having 2 old usb flash drive (sandisk cruzer mini 512mb)  that I had previously used in my win7 machine and other windows OS based  machines (win xp) I decided to use one of them to do a live USB for  clonezilla. 

So I inserted the usb on my ubuntu. Nautilus recognized it, and it had  two files which I decided to backup/copy them to a win7 pc so removed  the USB from ubuntu (through nautilus eject function). That went fine. 

Then put them on the win7 pc and it would see the drive but when  selecting it would say "please insert disk into removable"  so I could  not see any files. Then ejected the usb and put into the ubuntu. The the  USBflash would not show in nautilus, put it back on win7 to format and  could not so decided to use the other one I had same thing happened. 

So after messing TWO USB drives decided maybe I could fix them using  disk utilities from ubuntu. So put it back on my ubunut system and I  could see in disk utility tried formatting this but no luck and getting  the message: *"An error occured while performing an operation on "Generic USB flash Drive" (Generic USB flash Drive) The operation failed"*

And Details says:
*"Error creating partition table: helper exited with exit code 1: cannot open /dev/sdf: No medium found"*

Well figured out do it with gparted right? well open gparted and the  program cannot see the drive is not listed! well do command line right? I  did *"sudo gparted /dev/sdf*" 
and got: *"Error opening /dev/sdf No medium found"* 

**Then tried:**
[I]"sudo parted -l"
[/I]**Got this:**[I]
Model: ATA WDC WD360GD-00FL (scsi)
Disk /dev/sda: 37.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.8GB  32.8GB  primary   ext4            boot
 2      32.8GB  37.0GB  4191MB  extended
 5      32.8GB  37.0GB  4190MB  logical   linux-swap(v1)[/I]

**Then did this:**
[I]sudo fdisk -l
[/I]**Got this:**[I]
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f27d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    64114687    32056320   83  Linux
/dev/sda2        64116734    72302591     4092929    5  Extended
/dev/sda5        64118784    72302591     4091904   82  Linux swap / Solaris[/I]

**Tried this:**
*sudo blkid*
**Got this:**
[I]/dev/sda1: UUID="16d7d527-8066-4beb-ad29-29539a0fc8b6" TYPE="ext4" 
/dev/sda5: UUID="af0c3984-f19b-4d8c-b5e5-c1369fa7de05" TYPE="swap"
[/I]
[B]Tried this:
[/B]*df*
**Got this:**
[I]Filesystem           1K-blocks     Used Available Use% Mounted on
/dev/sda1             31552456 17109464  12840176  58% /
udev                   1961968       12   1961956   1% /dev
tmpfs                   789888      860    789028   1% /run
none                      5120        0      5120   0% /run/lock
none                   1974720      216   1974504   1% /run/shm
/home/user/.Private  31552456 17109464  12840176  58% /home/user[/I]

[B]Tried this:
[/B]*sudo parted -l*
**Got this:**
[I]Model: ATA WDC WD360GD-00FL (scsi)
Disk /dev/sda: 37.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.8GB  32.8GB  primary   ext4            boot
 2      32.8GB  37.0GB  4191MB  extended
 5      32.8GB  37.0GB  4190MB  logical   linux-swap(v1)[/I]


[B]Tried this:
[/B] *lsusb*
**Got this:**
[I]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
[COLOR=#0000ff]Bus 002 Device 009: ID 1043:8006 iCreate Technologies Corp. Flash Disk 32-256 MB < this is the drive![/COLOR]
Bus 002 Device 004: ID 0424:2412 Standard Microsystems Corp. 
Bus 002 Device 005: ID 046d:c077 Logitech, Inc. [/I]

**Tried looking at syslog when connecting USBthumb drive g****ot this:**
Jul  2 12:50:40 user-PC kernel: [15296.310255] usb 2-1.3: new full-speed USB device number 10 using ehci_hcd
Jul  2 12:50:40 user-PC kernel: [15296.404503] usb 2-1.3: New USB device found, idVendor=1043, idProduct=8006
Jul  2 12:50:40 user-PC kernel: [15296.404508] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jul  2 12:50:40 user-PC kernel: [15296.405020] scsi9 : usb-storage 2-1.3:1.0
Jul  2 12:50:40 user-PC mtp-probe: checking bus 2, device 10: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Jul  2 12:50:40 user-PC mtp-probe: bus: 2, device: 10 was not an MTP device
Jul  2 12:50:41 user-PC kernel: [15297.404099] scsi 9:0:0:0: Direct-Access     Generic  USB Flash Drive  1.04 PQ: 0 ANSI: 2
Jul  2 12:50:41 user-PC kernel: [15297.404880] sd 9:0:0:0: Attached scsi generic sg6 type 0
Jul  2 12:50:41 user-PC kernel: [15297.409565] sd 9:0:0:0: [sdf] Attached SCSI removable disk


[I]**Syslog when USB is ejected/stopped with disk utility at disconnect**:
Jul  2 12:51:17 [/I]user*-PC kernel: [15333.833385] usb 2-1.3: USB disconnect, device number 10*

**Tried looking at dmesg (**tail -f /var/log/dmesg)** g****ot this:**
[   21.168880] r8169 0000:02:00.0: eth0: link down
[   21.168889] r8169 0000:02:00.0: eth0: link down
[   21.169119] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.169403] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.171718] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   21.171931] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   21.172300] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   21.172753] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   21.172912] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   21.173064] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[B]
Tried this:
[/B]*sudo hdparm -r0 /dev/sdf*
**Got this:**
/dev/sdf:
 setting readonly to 0 (off)
 readonly      =  0 (off)

[B]Tried this:
[/B]*sudo dd if=/dev/zero of=/dev/sdf bs=1M*
**Got this:**
[I]dd: opening `/dev/sdf': No medium found
[/I]
**Tried installing testdisk again it could not see the drive**
**Tried this to mount so gparted could see usb drive with this:**
*sudo mount /dev/sdf -t vfat /mnt/usbflash0*
**Got this:**
*"mount: no medium found on /dev/sdf*"

**Tried this:**[I]
sudo fsck /dev/sdf[/I]
**Got this:**
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: No medium found while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

**On #ubuntu someone suggested the USBflash drive being sandisk  could have a cd partition so download U3 removal tool and tried this:**[I]
sudo u3-tool -u /dev/sdf[/I]
**Got this:**
*Error opening device: No medium found*

**Tried to format in win7 it won't let me saying same thing insert a disk! tried same U3 removal tool in win7 like this:**
u3-tool.exe -p 0 E[B] 
Win 7 says this:[/B]
u3_partition() failed: Failed reading device property 0x03: Header of property 0x0003 could not be read.

**Tried this:**[I]
sudo udisks --mount /dev/sdf[/I]
**Got this:**
*Mount failed: Error mounting: mount: no medium found on /dev/sdf*

**Tried this:**[I]
sudo parted /dev/sdf unit s print[/I]
**Got this:**
*Error: Error opening /dev/sdf: No medium found* 

Now other USB drives appear to be fine just happened with this Sandisk  Cruzer mini 512mb, so if no one can help at least beware ubuntu will  mess this USBflash drives! I searched and searched but nothing helps I  see some others have had similar issues without resolution or they have  problems with config which I do not think is my case but maybe it is  well thank you for any help you throw my way!

---

### Post by ande1010 on 2013-07-02
btw my mtab is:
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/home/user/.Private /home/user ecryptfs ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=b********,ecryptfs_fnek_sig=b***********
gvfs-fuse-daemon /home/user/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=user 0 0
/dev/sdf /media/84D3-5BFD vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0

---

