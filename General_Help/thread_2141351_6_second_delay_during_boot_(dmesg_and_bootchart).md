---
title: "6 second delay during boot (dmesg and bootchart)"
date: 2013-05-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-05-02
dmesg output:
[http://pastebin.com/PzDEMW7m](http://pastebin.com/PzDEMW7m)
snip:
```

~$ cat -n /tmp/dmesg
...
   805    [    5.762379] hda_intel: Disabling MSI
   806    [    5.762385] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
   807    [    5.766081] usblp 2-1:1.1: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7711
   808    [    5.766099] usbcore: registered new interface driver usblp
   809    [    6.562885] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input12
   810    [    6.562950] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
   811    [    6.562993] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
   812    [    6.563036] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
   813    [   12.066644] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,discard
   814    [   12.789483] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
   815    [   12.873412] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
   816    [   13.130087] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
   817    [   13.229187] EXT4-fs (sdb4): mounted filesystem with ordered data mode. Opts: (null)
   818    [   13.395075] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
   819    [   13.504780] init: failsafe main process (1016) killed by TERM signal
...

```and why is line 813 no including [FONT=courier new]noatime[/FONT]?
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d842f936-1037-4cd8-96b1-b43e104b4bb0 /               ext4    errors=remount-ro,noatime,discard 0       1
# /home was on /dev/sdb2 during installation
UUID=b8362e2b-2cdb-40f4-a2a8-a9ed1207cb81 /home           ext4    defaults        0       2
# /mnt/iso was on /dev/sdb5 during installation
UUID=374c0218-12b0-4a8f-b142-51498594e564 /mnt/iso        ext4    defaults        0       2
# /mnt/virtual_box was on /dev/sdb4 during installation
UUID=b588fa58-21cf-4ddc-a55d-24e23cb00ec9 /mnt/virtual_box ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=3d1dd4e3-d423-4802-b52a-aa74d6fdc8bd /var            ext4    defaults        0       2
# /var/cache/apt/archives was on /dev/sdb3 during installation
UUID=335a0626-f095-4235-8115-a96fd0ac12ec /var/cache/apt/archives ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=edcffc51-e736-474e-b338-18182e372f87 none            swap    sw              0       0
# /tmp was moved to RAM after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777 0       0
# /root was moved to /home/root after installation
/home/root                                /root           bind    defaults,bind   0       0
# /media was moved to RAM after installation
tmpfs                                     /media          tmpfs   defaults,size=1M,mode=755 0       0
```
Boot chart:
[[IMG]http://i.imgur.com/lC5uXKRs.png[/IMG]]("http://i.imgur.com/lC5uXKR.png")

---

### Post by pqwoerituytrueiwoq on 2013-05-02
i found the issue, fsck takes about 3-4 time longer than it did on 10.04, how can i fix that?
[[IMG]http://i.imgur.com/gfEwzgRs.png[/IMG]]("http://i.imgur.com/gfEwzgR.png") old boot chat from 10.04 on the same system
[[IMG]http://i.imgur.com/n8iEKGel.png[/IMG]](http://i.imgur.com/n8iEKGe.png)

---

### Post by pqwoerituytrueiwoq on 2013-05-02
Ok, i removed a couple partition in fstab (everything in /mnt and /var/cache/apt/archives) and the total boot time was halved
Why are they adding so much time to my boot process?
[[img]http://www.zimagez.com/miniature/screenshot-05022013-112806pm.php[/img]](http://www.zimagez.com/zimage/screenshot-05022013-112806pm.php)

---

### Post by oldfred on 2013-05-02
I do not know details, but it looked like you mounted tmpfs twice, once to /tmp and once to /media?

I have not seen the /home/root being remounted like that, but I have never used bind. Is bind slower?

---

### Post by pqwoerituytrueiwoq on 2013-05-03
wait, you cant use multiple ram disks like that?
the media one is just to prevent folder clutter for if i have a guest user, every guest user whu uses a flash drive would get a /media/guest-XXXX/UUID folder, so i figured i would clean it on boot my making it a tiny ram disk

my issue seems to be tied to fsck and my HDD, is a GPT partition table just slow in BIOS mode instead of UEFI mode?

to my knowledge bind works like a symlink, just the file manager does not see it as a link

fsck does not check the tmpfs or bind stuff as the <pass> is 0 on them

it is like it runs a full check on every boot instead of every 30 mounts like it should

---

### Post by oldfred on 2013-05-03
I have gpt with BIOS and notice no difference that I can tell.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
how many partitions? it is like the 2 mnt partitions i made added 5 seconds to my boot time
i am trying a long format on one of the partitions (was still empty) we will see if fsck likes it more once it has had 0s written to it
This is after i disabled 3 of them in fstab
```
[    5.225696] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input12
[    5.225764] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
[    5.225808] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[    5.225850] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
[    6.244280] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[    6.648164] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    6.664365] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    6.732030] init: failsafe main process (947) killed by TERM signal
[    6.783474] type=1400 audit(1367550862.667:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1048 comm="apparmor_parser"
[    6.783791] type=1400 audit(1367550862.667:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1048 comm="apparmor_parser"
```

---

### Post by oldfred on 2013-05-03
I do know when I added the mounts of my NTFS data partitions that boot time increased on my SSD by 3-5 sec. And having a flash drive plugged in slows boot a lot. 

When I only had hard drives I did not notice difference as the time was about the same, but with SSD that same time becomes more noticeable since everything else is so fast.

I at one time had real slow mount of my XP NTFS partition, but XP still booted. I then ran chkdsk and it mounted quicker and XP even booted a bit faster, but still slow.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
i just formated the other partitions, having them in fstab still makes the system boot slow, it also does not appear that ureadahead is working [FONT=courier new]/var/lib/ureadahead[/FONT] is always empty, i just purged and reinstalled it
edit: this is without mounting the /mnt partitions
[http://pastebin.com/VJwgygUk](http://pastebin.com/VJwgygUk)
this is without the archives partition
```
3.999464] scsi 8:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    4.005719] scsi 8:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    4.005900] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    4.006054] sd 8:0:0:1: Attached scsi generic sg4 type 0
[    4.006166] sd 8:0:0:2: Attached scsi generic sg5 type 0
[    4.006384] sd 8:0:0:3: Attached scsi generic sg6 type 0
[    4.027609] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[    4.028359] sd 8:0:0:3: [sdf] Attached SCSI removable disk
[    4.029110] sd 8:0:0:1: [sdd] Attached SCSI removable disk
[    4.029856] sd 8:0:0:2: [sde] Attached SCSI removable disk
[    4.520825] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.641507] init: ureadahead main process (385) terminated with status 5
[    4.734937] Adding 16779888k swap on /dev/sdb6.  Priority:-1 extents:1 across:16779888k 
[    4.764074] udevd[479]: starting version 175
[    4.797970] lp: driver loaded but no devices found
[    4.799778] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[    4.816059] wmi: Mapper loaded
[    4.860145] MCE: In-kernel MCE decoding enabled.
[    4.868412] EDAC MC: Ver: 3.0.0
[    4.876828] AMD64 EDAC driver v3.4.0
[    4.876857] EDAC amd64: DRAM ECC disabled.
[    4.876865] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    4.876865]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    4.876865]  (Note that use of the override may cause unknown side effects.)
[    4.880159] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20130117/utaddress-251)
[    4.880165] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SMRG 2 (20130117/utaddress-251)
[    4.880168] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 3 (20130117/utaddress-251)
[    4.880172] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.885601] microcode: CPU0: patch_level=0x010000b6
```
The time added for a couple partitions is observed, i did not have this issue with a MBR partition table on ubuntu 10.04
I even set the pass number in fstab to 0 and it had no effect on boot time
As a workaround i am using /etc/rc.local to mount them, is there a better way to mount them?
```
if [ ! -d "/mnt/iso/lost+found" ];then
    mount -U 156f2dd4-0bfe-414c-95a8-080973d9bedc /mnt/iso
fi
if [ ! -d "/mnt/virtual_box/lost+found" ];then
    mount -U 03cc0da7-dc02-4f82-832a-805f8c2e6c4d /mnt/virtual_box
fi
if [ ! -d "/var/cache/apt/archiveslost+found" ];then
    mount -U 39fbf8c6-5d6f-49b2-8433-c06f58278d36 /var/cache/apt/archives
fi
```
i could make a script to parse /etc/fstab and mount lines starting with ## but it is not worth the time

---

