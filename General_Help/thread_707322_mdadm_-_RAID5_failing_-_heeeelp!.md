---
title: "mdadm - RAID5 failing - heeeelp!"
date: 2008-02-25
forum: General Help
---

### Post by klausbreuer on 2008-02-25
Hi!

Whew - the third time the RAID is causing trouble this week... sigh.

Allow me to explain some history, it might have something to do with this.
I'm running Ubuntu (latest version) on a 500GB SATA HD. I added a second 500GB SATA for W2K (for playing games) as secondary drive. Thanks to GRUB, no problem.

By now I require XP for games (Tabula Rasa! ;) and had trouble. I switched the drives around in BIOS, didn't help. Only thing which worked was disconnecting Linux...
Found out that XP insists on being on the primary drive. Modified the GRUB menu, added it to the other drive, switched cables and - voila. GRUB came up, XP boots, Linux boots.

But: my mdadm RAID-5 failed. We're looking at 8x250Gb IDE drives, connected to two controllers. The last problem was with the ext3 system after a power failure - fsck worked it out fine.
This time, however, it's looking strange: apparently two drives have a bad partition table, and the 3rd one looks veeery suspicious (i.e.: also bad partition table). Thus I cannot start/access /dev/md0.

fdisk-l looks like this:

    $ sudo fdisk -l

    Disk /dev/sda: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x00000000

    Disk /dev/sda doesn't contain a valid partition table

    Disk /dev/sdb: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x00000000

    Disk /dev/sdb doesn't contain a valid partition table

    Disk /dev/sdc: 250.0 GB, 250059350016 bytes
    8 heads, 1 sectors/track, 61049646 cylinders
    Units = cylinders of 8 * 512 = 4096 bytes
    Disk identifier: 0x4caf4caf

       Device Boot      Start         End      Blocks   Id  System
    /dev/sdc1           16633       16882         995+  c7  Syrinx
    /dev/sdc2               1           1           0    0  Empty
    Partition 2 does not end on cylinder boundary.
    /dev/sdc3       268452089   268452338         995+  c7  Syrinx
    /dev/sdc4               1           1           0    0  Empty
    Partition 4 does not end on cylinder boundary.

    Disk /dev/sdd: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x32603263

       Device Boot      Start         End      Blocks   Id  System

    Disk /dev/sde: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x32603262

       Device Boot      Start         End      Blocks   Id  System

    Disk /dev/sdf: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x32603261

       Device Boot      Start         End      Blocks   Id  System

    Disk /dev/sdg: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x32603260

       Device Boot      Start         End      Blocks   Id  System

    Disk /dev/sdh: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x3260325f

       Device Boot      Start         End      Blocks   Id  System

    Disk /dev/sdi: 500.1 GB, 500107862016 bytes
    255 heads, 63 sectors/track, 60801 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x0003f1d1

       Device Boot      Start         End      Blocks   Id  System
    /dev/sdi1   *           1       12748   102398278+   7  HPFS/NTFS
    /dev/sdi2           12749       60801   385985722+   7  HPFS/NTFS

    Disk /dev/sdj: 500.1 GB, 500107862016 bytes
    255 heads, 63 sectors/track, 60801 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0x00011af2

       Device Boot      Start         End      Blocks   Id  System
    /dev/sdj1   *           1       60044   482303398+  83  Linux
    /dev/sdj2           60045       60801     6080602+   5  Extended
    /dev/sdj5           60045       60801     6080571   82  Linux swap / Solaris
      
I assume you don't want to see my entire dmseg, but the interesting bit is here:


    [   33.166851] ata7: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff90 irq 14
    [   33.166853] ata8: SATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff98 irq 15
    [   33.171100] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
    [   33.171109] sd 2:0:0:0: [sda] Write Protect is off
    [   33.171111] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
    [   33.171121] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.171150] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
    [   33.175994] sd 2:0:0:0: [sda] Write Protect is off
    [   33.175997] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
    [   33.176013] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.176016]  sda: unknown partition table
    [   33.190340] sd 2:0:0:0: [sda] Attached SCSI disk
    [   33.190376] sd 2:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
    [   33.190383] sd 2:0:1:0: [sdb] Write Protect is off
    [   33.190385] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
    [   33.190397] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.190427] sd 2:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
    [   33.190434] sd 2:0:1:0: [sdb] Write Protect is off
    [   33.190436] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
    [   33.190447] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.190450]  sdb: unknown partition table
    [   33.203378] sd 2:0:1:0: [sdb] Attached SCSI disk
    [   33.203534] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
    [   33.203542] sd 3:0:0:0: [sdc] Write Protect is off
    [   33.203544] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
    [   33.203560] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.203584] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
    [   33.203590] sd 3:0:0:0: [sdc] Write Protect is off
    [   33.203591] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
    [   33.203601] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.203602]  sdc: sdc1 sdc3
    [   33.220555]  sdc: p3 exceeds device capacity
    [   33.220589] sd 3:0:0:0: [sdc] Attached SCSI disk
    [   33.220618] sd 3:0:1:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
    [   33.220626] sd 3:0:1:0: [sdd] Write Protect is off
    [   33.220628] sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
    [   33.220639] sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.220664] sd 3:0:1:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
    [   33.220671] sd 3:0:1:0: [sdd] Write Protect is off
    [   33.220673] sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
    [   33.220684] sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.220686]  sdd:
    [   33.230178] sd 3:0:1:0: [sdd] Attached SCSI disk
    [   33.230341] sd 5:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
    [   33.230348] sd 5:0:0:0: [sde] Write Protect is off
    [   33.230350] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
    [   33.230359] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.230382] sd 5:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
    [   33.230388] sd 5:0:0:0: [sde] Write Protect is off
    [   33.230390] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
    [   33.230400] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.230401]  sde:
    [   33.237165] sd 5:0:0:0: [sde] Attached SCSI disk
    [   33.237195] sd 5:0:1:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
    [   33.237202] sd 5:0:1:0: [sdf] Write Protect is off
    [   33.237204] sd 5:0:1:0: [sdf] Mode Sense: 00 3a 00 00
    [   33.237215] sd 5:0:1:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.237241] sd 5:0:1:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
    [   33.237248] sd 5:0:1:0: [sdf] Write Protect is off
    [   33.237249] sd 5:0:1:0: [sdf] Mode Sense: 00 3a 00 00
    [   33.237261] sd 5:0:1:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.237263]  sdf:
    [   33.246181] sd 5:0:1:0: [sdf] Attached SCSI disk
    [   33.246351] sd 6:0:0:0: [sdg] 488397168 512-byte hardware sectors (250059 MB)
    [   33.246357] sd 6:0:0:0: [sdg] Write Protect is off
    [   33.246359] sd 6:0:0:0: [sdg] Mode Sense: 00 3a 00 00
    [   33.246369] sd 6:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.246391] sd 6:0:0:0: [sdg] 488397168 512-byte hardware sectors (250059 MB)
    [   33.246396] sd 6:0:0:0: [sdg] Write Protect is off
    [   33.246398] sd 6:0:0:0: [sdg] Mode Sense: 00 3a 00 00
    [   33.246408] sd 6:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.246409]  sdg:
    [   33.263598] sd 6:0:0:0: [sdg] Attached SCSI disk
    [   33.263629] sd 6:0:1:0: [sdh] 488397168 512-byte hardware sectors (250059 MB)
    [   33.263636] sd 6:0:1:0: [sdh] Write Protect is off
    [   33.263638] sd 6:0:1:0: [sdh] Mode Sense: 00 3a 00 00
    [   33.263649] sd 6:0:1:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.263675] sd 6:0:1:0: [sdh] 488397168 512-byte hardware sectors (250059 MB)
    [   33.263682] sd 6:0:1:0: [sdh] Write Protect is off
    [   33.263684] sd 6:0:1:0: [sdh] Mode Sense: 00 3a 00 00
    [   33.263695] sd 6:0:1:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [   33.263698]  sdh:
    [   33.280200] sd 6:0:1:0: [sdh] Attached SCSI disk
    [   33.285311] scsi 0:0:0:0: Attached scsi generic sg0 type 5
    [   33.285325] scsi 0:0:1:0: Attached scsi generic sg1 type 5
    [   33.285338] sd 2:0:0:0: Attached scsi generic sg2 type 0
    [   33.285349] sd 2:0:1:0: Attached scsi generic sg3 type 0
    [   33.285362] sd 3:0:0:0: Attached scsi generic sg4 type 0
    [   33.285373] sd 3:0:1:0: Attached scsi generic sg5 type 0
    [   33.285386] sd 5:0:0:0: Attached scsi generic sg6 type 0
    [   33.285398] sd 5:0:1:0: Attached scsi generic sg7 type 0
    [   33.285410] sd 6:0:0:0: Attached scsi generic sg8 type 0
    [   33.285424] sd 6:0:1:0: Attached scsi generic sg9 type 0
    [   33.328981] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001643596]
    [   33.345027] ata7.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
    [   33.345030] ata7.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
    [   33.353028] ata7.00: configured for UDMA/133
    [   33.382413] md: md0 stopped.
    [   33.402315] attempt to access beyond end of device
    [   33.402319] sdc: rw=0, want=2147618504, limit=488397168
    [   33.402322] Buffer I/O error on device sdc3, logical block 1792
    [   33.402325] attempt to access beyond end of device
    [   33.402327] sdc: rw=0, want=2147618505, limit=488397168
    [   33.402329] Buffer I/O error on device sdc3, logical block 1793
    [   33.402331] attempt to access beyond end of device
    [   33.402333] sdc: rw=0, want=2147618506, limit=488397168
    [   33.402335] Buffer I/O error on device sdc3, logical block 1794
    [   33.402338] attempt to access beyond end of device
    [   33.402340] sdc: rw=0, want=2147618507, limit=488397168
    [   33.402341] Buffer I/O error on device sdc3, logical block 1795
    [   33.402344] attempt to access beyond end of device
    [   33.402345] sdc: rw=0, want=2147618508, limit=488397168
    [   33.402347] Buffer I/O error on device sdc3, logical block 1796
    [   33.402349] attempt to access beyond end of device
    [   33.402351] sdc: rw=0, want=2147618509, limit=488397168
    [   33.402353] Buffer I/O error on device sdc3, logical block 1797
    [   33.402355] attempt to access beyond end of device
    [   33.402357] sdc: rw=0, want=2147618510, limit=488397168
    [   33.402359] Buffer I/O error on device sdc3, logical block 1798
    [   33.402361] attempt to access beyond end of device
    [   33.402363] sdc: rw=0, want=2147618511, limit=488397168
    [   33.402365] Buffer I/O error on device sdc3, logical block 1799
    [   33.402368] attempt to access beyond end of device
    [   33.402370] sdc: rw=0, want=2147618504, limit=488397168
    [   33.402372] Buffer I/O error on device sdc3, logical block 1792
    [   33.402374] attempt to access beyond end of device
    [   33.402376] sdc: rw=0, want=2147618505, limit=488397168
    [   33.402378] Buffer I/O error on device sdc3, logical block 1793
    [   33.402380] attempt to access beyond end of device
    [   33.402382] sdc: rw=0, want=2147618506, limit=488397168
    [   33.402384] attempt to access beyond end of device
    [   33.402386] sdc: rw=0, want=2147618507, limit=488397168
    [   33.402388] attempt to access beyond end of device
    [   33.402390] sdc: rw=0, want=2147618508, limit=488397168
    [   33.402392] attempt to access beyond end of device
    [   33.402394] sdc: rw=0, want=2147618509, limit=488397168
    [   33.402396] attempt to access beyond end of device
    [   33.402398] sdc: rw=0, want=2147618510, limit=488397168
    [   33.402400] attempt to access beyond end of device
    [   33.402402] sdc: rw=0, want=2147618511, limit=488397168
    [   33.448287] md: bind<sdb>
    [   33.448447] md: bind<sdh>
    [   33.448603] md: bind<sdf>
    [   33.448778] md: bind<sdd>
    [   33.448909] md: bind<sdc>
    [   33.449071] md: bind<sde>
    [   33.460699] md: md0 stopped.
    [   33.460704] md: unbind<sde>
    [   33.460707] md: export_rdev(sde)
    [   33.460718] md: unbind<sdc>
    [   33.460719] md: export_rdev(sdc)
    [   33.460725] md: unbind<sdd>
    [   33.460727] md: export_rdev(sdd)
    [   33.460733] md: unbind<sdf>
    [   33.460735] md: export_rdev(sdf)
    [   33.460741] md: unbind<sdh>
    [   33.460743] md: export_rdev(sdh)
    [   33.460756] md: unbind<sdb>
    [   33.460758] md: export_rdev(sdb)
    [   33.464782] md: bind<sda>
    [   33.464937] md: bind<sdb>
    [   33.465083] md: bind<sdg>
    [   33.465235] md: bind<sdh>
    [   33.465387] md: bind<sdf>
    [   33.465556] md: bind<sdd>
    [   33.465699] md: bind<sdc>
    [   33.465859] md: bind<sde>  

And later:

    [   40.990863] md: md0 stopped.
    [   40.990871] md: unbind<sde>
    [   40.990874] md: export_rdev(sde)
    [   40.990895] md: unbind<sdc>
    [   40.990897] md: export_rdev(sdc)
    [   40.990909] md: unbind<sdd>
    [   40.990911] md: export_rdev(sdd)
    [   40.990922] md: unbind<sdf>
    [   40.990924] md: export_rdev(sdf)
    [   40.990935] md: unbind<sdh>
    [   40.990937] md: export_rdev(sdh)
    [   40.990947] md: unbind<sdg>
    [   40.990949] md: export_rdev(sdg)
    [   40.990960] md: unbind<sdb>
    [   40.990962] md: export_rdev(sdb)
    [   40.990972] md: unbind<sda>
    [   40.990974] md: export_rdev(sda)
    [   41.059480] md: bind<sda>
    [   41.059635] md: bind<sdb>
    [   41.059780] md: bind<sdg>
    [   41.059931] md: bind<sdh>
    [   41.060084] md: bind<sdf>
    [   41.060253] md: bind<sdd>
    [   41.060392] md: bind<sdc>
    [   41.060555] md: bind<sde>
    [   41.097838] md: md0 stopped.
    [   41.097845] md: unbind<sde>
    [   41.097849] md: export_rdev(sde)
    [   41.097861] md: unbind<sdc>
    [   41.097863] md: export_rdev(sdc)
    [   41.097870] md: unbind<sdd>
    [   41.097872] md: export_rdev(sdd)
    [   41.097879] md: unbind<sdf>
    [   41.097881] md: export_rdev(sdf)
    [   41.097888] md: unbind<sdh>
    [   41.097890] md: export_rdev(sdh)
    [   41.097897] md: unbind<sdg>
    [   41.097898] md: export_rdev(sdg)
    [   41.097905] md: unbind<sdb>
    [   41.097907] md: export_rdev(sdb)
    [   41.097913] md: unbind<sda>
    [   41.097915] md: export_rdev(sda)
    [   41.110745] md: bind<sda>
    [   41.110899] md: bind<sdb>
    [   41.111045] md: bind<sdg>
    [   41.111196] md: bind<sdh>
    [   41.111347] md: bind<sdf>
    [   41.111517] md: bind<sdd>
    [   41.111664] md: bind<sdc>
    [   41.111822] md: bind<sde>  

mdatat is also not all that useful:

    $ cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
    md0 : inactive sde[0](S) sdc[7](S) sdd[6](S) sdf[5](S) sdh[4](S) sdg[3](S) sdb[2](S) sda[1](S)
          1953587200 blocks

    unused devices: <none>  

or:

    $ sudo mdadm --query --detail /dev/md0
    mdadm: Unknown keyword devices=/dev/sde,/dev/sda,/dev/sdb,/dev/sdg,/dev/sdh,/dev/sdf,/dev/sdd,/dev/sdc
    mdadm: md device /dev/md0 does not appear to be active.  

and, of course:

    $ sudo mdadm -R /dev/md0
    mdadm: Unknown keyword devices=/dev/sde,/dev/sda,/dev/sdb,/dev/sdg,/dev/sdh,/dev/sdf,/dev/sdd,/dev/sdc
    mdadm: failed to run array /dev/md0: Input/output error  

The message "Unknown keyword devices..." apparently doesn't mean all that much, it always comes up, even if everything is running well.

Hmm. Once a drive failed. How about trying to remove/re-insert /dev/sdc:

    $ sudo mdadm /dev/md0 --fail /dev/sdc
    mdadm: Unknown keyword devices=/dev/sde,/dev/sda,/dev/sdb,/dev/sdg,/dev/sdh,/dev/sdf,/dev/sdd,/dev/sdc
    mdadm: set device faulty failed for /dev/sdc:  No such device  

:(

Help! Does this mean, three drives failed simultaneously?
I'd be really grateful for every little hint/tip/leak - and will, of course, post the solution here...

Ciao,
Klaus

---

### Post by fjgaude on 2008-02-25
What does your /etc/mdadm/mdadm.comf file look like?

We'll get to the bottom of this somehow.

---

### Post by klausbreuer on 2008-02-25
Thanks for your fast response, fjgaude! Would be great :)

Oookay... looks like I should have looked at the conf file... I changed the line "devices=..." into "DEVICE ...":

$ cat mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE /dev/sd*
#DEVICE /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh
#devices=/dev/sde,/dev/sda,/dev/sdb,/dev/sdg,/dev/sdh,/dev/sdf,/dev/sdd,/dev/sdc
DEVICE /dev/sde /dev/sda /dev/sdb /dev/sdg /dev/sdh /dev/sdf /dev/sdd /dev/sdc

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
# old: ARRAY /dev/md0 level=raid5 num-devices=8 UUID=0ce38b42:cda216f1:d8c87cc8:ee4cf9d0
ARRAY /dev/md0 level=raid5 num-devices=8 UUID=0ce38b42:cda216f1:5c8ccd86:cfb0a564

# This file was auto-generated on Thu, 02 Aug 2007 23:09:18 +0200
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

Ummm... that was dumb of me, my apologies. Since I rarely saw the error and the array worked okay, I simply ignored it (not such a good idea, is it?).

This did, of course, change the mdadm query:

$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Sep  3 10:36:14 2005
     Raid Level : raid5
  Used Dev Size : 244198400 (232.89 GiB 250.06 GB)
   Raid Devices : 8
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Feb 25 10:53:04 2008
          State : active, degraded, Not Started
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : 0ce38b42:cda216f1:5c8ccd86:cfb0a564
         Events : 0.281522

    Number   Major   Minor   RaidDevice State
       0       8       64        0      active sync   /dev/sde
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       96        3      active sync   /dev/sdg
       4       8      112        4      active sync   /dev/sdh
       5       8       80        5      active sync   /dev/sdf
       6       0        0        6      removed
       7       0        0        7      removed

Starting it got the previous error, so why don't I, um, try to stop it and start again? Aaaah:

$ sudo mdadm -R /dev/md0
mdadm: failed to run array /dev/md0: Input/output error
klaus@GoLem:/etc/mdadm$ sudo mdadm -S /dev/md0
mdadm: stopped /dev/md0
klaus@GoLem:/etc/mdadm$ sudo mdadm -R /dev/md0
mdadm: failed to run array /dev/md0: Invalid argument

Still fails to start, but at least it now shows us more info... which, sadly, doesn't help me very much, though.

Ciao,
Klaus

---

### Post by fjgaude on 2008-02-25
Okay, we are getting somewhere.

Did you remove up to four of the drives from the array using the --remove or -r command?

When did the UUID change for the array from what it was initially to what you have it correctly now?

In the state the array is now, have you tried sudo mdadm --assemble -f /dev/md0?

I'm leaving the computer and will be back about three hours from now.

---

### Post by klausbreuer on 2008-02-25
I...I.. um... er... wow...

Look:

$ sudo mdadm --assemble -f /dev/md0
mdadm: forcing event count in /dev/sda(1) from 281514 upto 281522
mdadm: forcing event count in /dev/sdb(2) from 281514 upto 281522
mdadm: forcing event count in /dev/sdd(6) from 281514 upto 281522
mdadm: forcing event count in /dev/sdc(7) from 281514 upto 281522
mdadm: clearing FAULTY flag for device 1 in /dev/md0 for /dev/sda
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdb
mdadm: clearing FAULTY flag for device 6 in /dev/md0 for /dev/sdd
mdadm: clearing FAULTY flag for device 7 in /dev/md0 for /dev/sdc
mdadm: /dev/md0 has been started with 8 drives.
$ sudo mount /dev/md0 /media/raid/
$

And... it works. Works!
Holy cow, fjgaude, thanks a *LOT* ! :-D

Any checks I should perhaps run?

One thing's for sure: I'm getting an el-cheapo PC, move the RAID-5 into there, place it (sans keyboard or screen) into a quiet, cool cupboard, hook it up to my net and not touch it for a looong time, especially no reboots.

Aaaah, I'll be able to sleep peacefully tonight, joy! :)

Ciao,
Klaus

---

### Post by fjgaude on 2008-02-25
Before we leave let's do a:

```
sudo mdadm -D /dev/md0
```

And with things like you just did, i.e., force an assembly, it's a good idea to do a:

```
sudo watch cat /proc/mdstat
```

A CTRL-C will stop it, if you wish to move on, or if nothing is happening. Never do anything to an array until it is fully synced up. Although, you can use it to read and write data but run no commands on the array.

Also remember if the UUID of each drive is identical to that of the array, the array is likely to be in good health. You get that with an inquiry, -Q, on each individual drive.

So much to learn and remember about raid. I learn something new each day, really, and I've been at this for years, with mdadm alone for about a year.

Now, may the blessings be.

---

### Post by klausbreuer on 2008-02-26
I did an mdadm -D, and everything looks nice and good. :-)

Mind you, the array is still unhappy, and I have to force an assembly after each boot. Thus I'll put 400 Euros on the table for a second, very simply (and quiet) PC, which will run the array for me, be hooked up to the same router, and is never turned off.
An fsck is also coming up.

Thanks again!

Ciao,
Klaus

---

### Post by fjgaude on 2008-02-26
Let us know what the fsck looks like.

The normal fstab entry doesn't work. You have to force assembly. This is not good. Maybe there is a truly faulty drive in the array.

---

