---
title: "usb flash"
date: 2015-11-16
forum: General Help
---

### Post by okkadiroglu on 2015-11-16
I have a 8GB usb flash device which I have been using for the past few years. Now, when I insert it into the usb port it does not mount as it used to do. I use Ubuntu 15.10. My other devices using the same port mount without any problem. Only for this device I can see it with lsusb

[SIZE=1]oyo@okk001:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 024: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 093a:2516 Pixart Imaging, Inc. 
Bus 006 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE]

but cannot see it with df

[SIZE=1]oyo@okk001:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             4028416         0   4028416   0% /dev
tmpfs             815696     81600    734096  11% /run
/dev/sda1      449728224 120555960 306304348  29% /
tmpfs            4078472     36616   4041856   1% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            4078472         0   4078472   0% /sys/fs/cgroup
tmpfs             815696         0    815696   0% /run/user/133
tmpfs             815696       148    815548   1% /run/user/1001
tmpfs             815696         0    815696   0% /run/user/135
[/SIZE]

For sudo parted -ls I get,

[SIZE=1]oyo@okk001:~$ sudo parted -ls
Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  468GB  468GB   primary  ext4            boot
 2      468GB   500GB  32.1GB  primary  linux-swap(v1)
[/SIZE]

For sudo lsblk -fm I get,

[SIZE=1]oyo@okk001:~$ sudo lsblk -fm
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                 sda    465.8G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         40e37511-c176-4e0f-9ec5-3978142e0c15 /          &#9500;&#9472;sda1 435.9G root  disk  brw-rw----
&#9492;&#9472;sda2 swap         334171ea-ad09-4dc2-a640-63b662e3f6e4 [SWAP]     &#9492;&#9472;sda2  29.9G root  disk  brw-rw----
sr0                                                                 sr0     1024M root  cdrom brw-rw----
[/SIZE]

How can I format this device?

Thanks and best regards

---

### Post by Bucky Ball on 2015-11-16
Please use code tags. See the last link in my signature.

To format, use 'Disks' in Ubuntu or Gparted if you have it installed (it can be installed from the Software Centre or Synaptics).

Take note: USB dongles don't last forever. Expect them to fail sooner or later, and that can vary depending on a number of factors. If you've been using heavily everyday for a few years, for instance, it's fairly wonderful it's still working at all. Just because it is picked up by lsusb, doesn't mean it is in 100% functional working order. :)

---

### Post by sudodus on 2015-11-16
You wrote
> I have a [COLOR="#FF0000"]8GB usb flash device[/COLOR] which I have been using for the past few years. Now, when I insert it into the usb port it does not mount as it used to do. I use Ubuntu 15.10. My other devices using the same port mount without any problem. Only for this device I can see it with lsusb
...
```
Bus 003 Device 024: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick [COLOR="#FF0000"](2GB)[/COLOR]
```


Are the red texts referring to the same pendrive? In that case the size is not recognized correctly.

What is more important, it is not seen as a mass storage device, '/dev/sdx', which means that the tools to format do not work.

You can ***try in another computer***. Sometimes one computer's hardware or firmware or drivers do not cooperate well with a pendrive, but it might work in another computer. If no luck in any computer, I think the pendrive is damaged beyond repair. See this link for more details,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

