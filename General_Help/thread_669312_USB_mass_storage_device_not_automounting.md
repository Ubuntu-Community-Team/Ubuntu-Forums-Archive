---
title: "USB mass storage device not automounting"
date: 2008-01-16
forum: General Help
---

### Post by fjf on 2008-01-16
I am using an ebook reader (cybook gen3) that shows as a usb mass storage device in windows xp.  In ubuntu 7.10 it does not automount and I dunno how to do it.  Definitely, the dmesg changes after plugging it are:

[ 156.414141] usb 7-6: new high speed USB device using ehci_hcd and address 5
[ 156.713842] usb 7-6: new high speed USB device using ehci_hcd and address 6
[ 157.389166] usb 7-6: new high speed USB device using ehci_hcd and address 9
[ 158.063492] usb 7-6: new high speed USB device using ehci_hcd and address 12
[ 158.922672] usb 7-6: new high speed USB device using ehci_hcd and address 16
[ 159.222334] usb 7-6: new high speed USB device using ehci_hcd and address 17
[ 159.709845] usb 7-6: new high speed USB device using ehci_hcd and address 19
[ 160.197357] usb 7-6: new high speed USB device using ehci_hcd and address 21
[ 160.497059] usb 7-6: new high speed USB device using ehci_hcd and address 22
[ 160.985569] usb 7-6: new high speed USB device using ehci_hcd and address 24
[ 161.284272] usb 7-6: new high speed USB device using ehci_hcd and address 25

I am not using a hub, and the problem persists after using any usb connection in my computer.

lsmod output:

Module Size Used by
ipv6 267780 12
xt_limit 3584 8
xt_tcpudp 4096 20
ipt_LOG 7296 8
ipt_MASQUERADE 4608 0
ipt_TOS 3200 0
ipt_REJECT 5632 1
nf_conntrack_irc 7576 0
nf_conntrack_ftp 10144 0
xt_state 3328 6
af_packet 23812 2
binfmt_misc 12808 1
rfcomm 41744 2
l2cap 25728 11 rfcomm
bluetooth 60132 4 rfcomm,l2cap
vboxdrv 60592 0
ppdev 10372 0
acpi_cpufreq 10796 0
cpufreq_userspace 5284 0
cpufreq_ondemand 9740 2
cpufreq_powersave 2688 0
cpufreq_conservative 8712 0
cpufreq_stats 7104 0
freq_table 5536 3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video 19728 0
output 4736 1 video
bay 6912 0
dock 11280 1 bay
container 5632 0
sbs 14984 0
sbshc 7680 1 sbs
ac 6916 0
battery 14084 0
power_supply 9988 3 sbs,ac,battery
sbp2 24072 0
parport_pc 36260 0
lp 12324 0
parport 37832 3 ppdev,parport_pc,lp
snd_hda_intel 295328 1
snd_pcm_oss 42624 0
snd_mixer_oss 17536 1 snd_pcm_oss
snd_pcm 80644 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 33280 0
snd_seq_midi 9472 0
snd_rawmidi 25600 1 snd_seq_midi
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
lmpcm_usb 7168 0
snd_seq 53104 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 24324 2 snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
serio_raw 7940 0
iTCO_wdt 13092 0
usblp 15872 0
evdev 13056 3
psmouse 40208 0
pcspkr 4224 0
iTCO_vendor_support 4868 1 iTCO_wdt
snd 55172 11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_de vice
nvidia 6223184 34
soundcore 8800 1 snd
snd_page_alloc 11272 2 snd_hda_intel,snd_pcm
i2c_core 24832 1 nvidia
shpchp 34452 0
pci_hotplug 30880 1 shpchp
intel_agp 25364 0
agpgart 34760 2 nvidia,intel_agp
button 9232 0
iptable_nat 8324 0
nf_nat 20396 2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4 18824 8 iptable_nat
nf_conntrack 66496 7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,x t_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle 3712 0
iptable_filter 3840 1
ip_tables 14820 3 iptable_nat,iptable_mangle,iptable_filter
x_tables 16132 9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS, ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3 136840 2
jbd 48404 1 ext3
mbcache 9600 1 ext3
sg 36880 0
sr_mod 17956 0
sd_mod 30592 5
cdrom 37408 1 sr_mod
usbhid 31744 0
hid 38528 1 usbhid
r8169 32772 0
ahci 28292 4
ohci1394 33584 0
ieee1394 93752 2 sbp2,ohci1394
libata 156400 1 ahci
scsi_mod 151308 5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd 37004 0
uhci_hcd 27024 0
usbcore 145644 6 lmpcm_usb,usblp,usbhid,ehci_hcd,uhci_hcd
thermal 16796 0
processor 36872 2 acpi_cpufreq,thermal
fan 5380 0
fuse 50580 3

If I use my flash usb drive, it automounts fine and dmesg says:

[ 544.957645] usb 7-6: configuration #1 chosen from 1 choice
[ 545.036153] usbcore: registered new interface driver libusual
[ 545.041264] Initializing USB Mass Storage driver...
[ 545.041314] scsi6 : SCSI emulation for USB Mass Storage devices
[ 545.041358] usbcore: registered new interface driver usb-storage
[ 545.041361] USB Mass Storage support registered.
[ 545.041424] usb-storage: device found at 123
[ 545.041426] usb-storage: waiting for device to settle before scanning
[ 550.031746] usb-storage: device scan complete
[ 550.032252] scsi 6:0:0:0: Direct-Access Generic USB Flash Drive 1.00 PQ: 0 ANSI: 2
[ 550.036980] sd 6:0:0:0: [sdb] 16384001 512-byte hardware sectors (8389 MB)
[ 550.037479] sd 6:0:0:0: [sdb] Write Protect is off
[ 550.037482] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 550.037484] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 550.039603] sd 6:0:0:0: [sdb] 16384001 512-byte hardware sectors (8389 MB)
[ 550.040100] sd 6:0:0:0: [sdb] Write Protect is off
[ 550.040103] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 550.040105] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 550.040107] sdb: unknown partition table
[ 550.046512] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 550.046544] sd 6:0:0:0: Attached scsi generic sg2 type 0

Any ideas?.  Thanks!

---

### Post by geraldm on 2008-01-16
Could you post the parts of the file /proc/bus/usb/devices for this device, please?
That would provide endpoint information.

Gerald

---

### Post by fjf on 2008-01-16
The file is empty.

---

### Post by fjf on 2008-01-16
bump

---

### Post by fjf on 2008-01-17
Bump?

---

### Post by fjf on 2008-01-17
bumpy!

---

### Post by fjf on 2008-01-18
Bump

---

### Post by compwiz18 on 2008-01-18
Patience is a virtue :)

What does ```
mkdir /tmp/ebook
sudo mount /dev/sdb1
ls /tmp/ebook
```give you?

If that works, you'll be able to access your ebook's contents in /tmp/ebook

---

### Post by fjf on 2008-01-18
I try to be patient; I know this is no MS ;).  I get:

mount: cannot find /dev/sdb1 in /etc/fstab or /etc/mtab

Should I add a line in /etc/fstab?.  This file now is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0e474f28-7489-484e-b5d8-a0d132223983 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=e74a50a7-d765-4854-a7ba-aa8b294bfcc8 /home           ext3    defaults        0       2
# /dev/sda1
# /dev/sda3
UUID=22b9954a-ce44-413d-9014-de2e6e387358 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Generated by Automatix
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions

In /etc/mtab I have:

/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-2-generic/volatile tmpfs rw 0 0
/dev/sda4 /home ext3 rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

---

### Post by geraldm on 2008-01-18
compwiz18 posted a mount command, but should not that be
sudo mount -t auto /dev/sdb1 /tmp/ebook
?

Gerald

---

### Post by compwiz18 on 2008-01-18
> **geraldm said:**
> compwiz18 posted a mount command, but should not that be
sudo mount -t auto /dev/sdb1 /tmp/ebook
?

Gerald
I never use the -t auto option... usually mount device point works.

At any rate, fjf, if you run these commands immediately after plugging in the reader, what do you get?```
ls /dev/sd*
ls -ahl /dev/disk/by-uuid
dmesg | tail
```

---

### Post by fjf on 2008-01-19
Thanks.  I get:

mount: the special device /dev/sdb1 does not exist

---

### Post by compwiz18 on 2008-01-19
Alright - can you run the commands in my above post?

Thanks :KS

---

### Post by fjf on 2008-01-19
to ls /dev/sd*  I get: /dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4

to ls -ahl /dev/disk/by-uuid  I get:  total 0
drwxr-xr-x 2 root root 120 2008-01-19 15:53 .
drwxr-xr-x 5 root root 100 2008-01-19 15:15 ..
lrwxrwxrwx 1 root root  10 2008-01-19 15:15 0e474f28-7489-484e-b5d8-a0d132223983 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-01-19 15:15 22b9954a-ce44-413d-9014-de2e6e387358 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-01-19 15:15 8A38B70638B6F075 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-01-19 15:15 e74a50a7-d765-4854-a7ba-aa8b294bfcc8 -> ../../sda4

to dmesg | tail  I get:  [15237.283736] usb 7-5: new high speed USB device using ehci_hcd and address 125
[15237.583429] usb 7-5: new high speed USB device using ehci_hcd and address 126
[15238.258738] usb 7-5: new high speed USB device using ehci_hcd and address 3
[15241.190048] usb 7-5: new high speed USB device using ehci_hcd and address 18
[15242.994901] usb 7-5: new high speed USB device using ehci_hcd and address 27
[15244.232637] usb 7-5: new high speed USB device using ehci_hcd and address 33
[15244.903989] usb 7-5: new high speed USB device using ehci_hcd and address 36
[15245.955876] usb 7-5: new high speed USB device using ehci_hcd and address 41
[15246.442396] usb 7-5: new high speed USB device using ehci_hcd and address 43
[15247.306497] usb 7-5: new high speed USB device using ehci_hcd and address 47

---

