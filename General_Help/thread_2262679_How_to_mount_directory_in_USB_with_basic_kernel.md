---
title: "How to mount directory in USB with basic kernel?"
date: 2015-01-26
forum: General Help
---

### Post by Ian.kz.ma on 2015-01-26
I'm testing a new board that has linux kernel on it and I need to mount a folder from a USB to an existing folder on the board. Google says I can do so using fdisk -l to see where my device is but I believe the kernel I have is so basic it does not have fdisk. Here are the contents of /sbin:

```
/sbin # ls
arp                init               modprobe           swapoff
bootchartd         insmod             pivot_root         swapon
freeramdisk        klogd              portmap            switch_root
fsck               ldconfig           poweroff           sysctl
getty              losetup            reboot             syslogd
halt               lsmod              rmmod              udevadm
hdparm             makedevs           route              udevd
hotplug            mdev               runlevel           udhcpc
hwclock            mke2fs             setconsole         vconfig
ifconfig           mkfs.ext2          sln
ifdown             mkswap             start-stop-daemon
ifup               modinfo            sulogin
/sbin #
```

Here is what happens when I plug the usb in:

```
[ 1770.010000] usb 1-1: new high-speed USB device number 4 using sigma-ehci
[ 1770.160000] usb 1-1: New USB device found, idVendor=1e3d, idProduct=2092
[ 1770.160000] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1770.170000] usb 1-1: Product: Flash Disk
[ 1770.170000] usb 1-1: Manufacturer: CBM
[ 1770.180000] usb 1-1: SerialNumber: 071012004084E806
[ 1770.180000] usb-storage 1-1:1.0: USB Mass Storage device detected
[ 1770.190000] scsi2 : usb-storage 1-1:1.0
[ 1771.190000] scsi 2:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[ 1771.190000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 1771.200000] sd 2:0:0:0: [sda] 4118528 512-byte logical blocks: (2.10 GB/1.96 GiB)
[ 1771.200000] sd 2:0:0:0: [sda] Write Protect is off
[ 1771.200000] sd 2:0:0:0: [sda] No Caching mode page present
[ 1771.200000] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 1771.200000] sd 2:0:0:0: [sda] No Caching mode page present
[ 1771.200000] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 1771.200000]  sda: sda1
[ 1771.200000] sd 2:0:0:0: [sda] No Caching mode page present
[ 1771.200000] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 1771.200000] sd 2:0:0:0: [sda] Attached SCSI removable disk
/opt #

```

A google search also told me my /dev folder should hold the location of my USB but im not sure which? judging from the above input I presumed "usbmon4" so I tried:
```
mount usbmon4 /opt
```
But it just says "mount failed: block device required".
Here is my /dev folder:
```
/dev # ls
adsp1                  mmcblk0p11             tty24
alarm                  mmcblk0p12             tty25
ashmem                 mmcblk0p13             tty26
audio                  mmcblk0p2              tty27
audio1                 mmcblk0p3              tty28
binder                 mmcblk0p4              tty29
block                  mmcblk0p5              tty3
bus                    mmcblk0p6              tty30
char                   mmcblk0p7              tty31
console                mmcblk0p8              tty32
cpu_dma_latency        mmcblk0p9              tty33
cuse                   mmcblk0rpmb            tty34
disk                   net                    tty35
dsp                    network_latency        tty36
dsp1                   network_throughput     tty37
fd                     null                   tty38
full                   ppp                    tty39
fuse                   psaux                  tty4
input                  ptmx                   tty40
kmem                   pts                    tty41
kmsg                   ram0                   tty42
log_events             ram1                   tty43
log_main               ram10                  tty44
log_radio              ram11                  tty45
log_system             ram12                  tty46
loop-control           ram13                  tty47
loop0                  ram14                  tty48
loop1                  ram15                  tty49
loop2                  ram2                   tty5
loop3                  ram3                   tty50
loop4                  ram4                   tty51
loop5                  ram5                   tty52
loop6                  ram6                   tty53
loop7                  ram7                   tty54
mapper                 ram8                   tty55
mem                    ram9                   tty56
mixer                  random                 tty57
mixer1                 sda                    tty58
mmcblk0                sda1                   tty59
mmcblk0.APP_A          sequencer              tty6
mmcblk0.APP_B          sequencer2             tty60
mmcblk0.App9           sg0                    tty61
mmcblk0.UbootEnv       snd                    tty62
mmcblk0.etc            stderr                 tty63
mmcblk0.etc_rw         stdin                  tty7
mmcblk0.mbootA         stdout                 tty8
mmcblk0.mbootB         tty                    tty9
mmcblk0.reserved       tty0                   ttyS0
mmcblk0.reserved_data  tty1                   ttyS1
mmcblk0.rw_data        tty10                  ttyS2
mmcblk0.systemA        tty11                  uhid
mmcblk0.systemB        tty12                  uinput
mmcblk0boot0           tty13                  urandom
mmcblk0boot0p1         tty14                  usbmon0
mmcblk0boot0p2         tty15                  usbmon1
mmcblk0boot0p3         tty16                  usbmon2
mmcblk0boot0p4         tty17                  usbmon3
mmcblk0boot1           tty18                  usbmon4
mmcblk0boot1p1         tty19                  vcs
mmcblk0boot1p2         tty2                   vcs1
mmcblk0boot1p3         tty20                  vcsa
mmcblk0boot1p4         tty21                  vcsa1
mmcblk0p1              tty22                  xt_qtaguid
mmcblk0p10             tty23                  zero
/dev #

```

Any ideas? Thanks in a advance~

---

