---
title: "rsync slows and eventually stops then can’t reboot"
date: 2015-10-24
forum: General Help
---

### Post by Andrew_Welham on 2015-10-24
rsync slows and eventually stops then can’t reboot
 
I have an Ubuntu server 14.04 (fully patched)
One of its primary functions is file management, with a single no raided 8TB volume. (Read on before you complain about me not using raids).
Amongst the files are  10’s of millions of files approx. 40--50k each ordered into dated folders with up to approx. 5k files per folder.
These files plus a lot of average files including home videos, so some big ones as well are backed to to multiple locations.
1.        A secondary 8TB disk on the same server
2.       A number of small NAS devices on the lan network
3.       An offsite NAS across the internet
Syncing using Rsync to point 3 work well (slower but expected to be)
Syncing to the local NAS devices slows up over a few days to a crawl and goes so slow the server needs to be rebooted. But never goes very fast especially for the small files
Syncing to the 8TB disk after approx. can hour stops transferring data.
New attempts to log in to the server are intermittent, typically works on the 2[SUP]nd[/SUP] attempt, while the 1 attempt never returns with the password prompt.
Sync command dose not return
Can’t gracefully reboot, guess because the disk cache cannot be flushed, but I do have some control over the serve for example I can gracefully shutdown vbox.
I believe this is to do with the small files and caching. SO I have tried
1.       The no cache command before the rsync
2.       Having a secondary script which runs sync every 30 seconds, after about 1. Hours the scripts stopped running, after the sync attempts go to just over a minute to work
3.       I have now tried the sync option when mounting the devices.
My rsync command is
Rsync –aAXv /source /destination
All NAS devices are running using cifs
The two NAS devices on the local lan are encrypted using ecryptfs
The file system on both 8TB disks is ext4
None of the rsyncs have ever completed, except the one across the internet but that file system was already up to date. The others are backups from scratch.
Any ideas, it’s unusual for Linux to be so unstable.

---

### Post by Andrew_Welham on 2015-10-24
found the following my /sys/log/kern.log file around the time of errors
Oct 24 08:17:09 Hostname kernel: [ 6673.503148] sd 7:0:0:0: [sdb] uas_eh_abort_handler ffff880008e5fc80 tag 20, inflight: CMD OUT

the error uas_eh_abort_handler when googled discusses USBdisks which the 8Tb volumes are (USB3)
so i added 
```
options usb-storage quirks=Vendor_ID:Product_ID:u
```
to my

/etc/modprobe.d/ignore_uas.conf file

I'll see how it goes

---

### Post by Andrew_Welham on 2015-10-24
worked so well then i got the following any ideas ?
```

Oct 24 19:31:29 Hostname kernel: [ 5240.591107] sd 7:0:0:0: [sdb] uas_eh_abort_handler ffff8800478f7c80 tag 5, inflight: CMD OUT
Oct 24 19:31:32 Hostname kernel: [ 5243.590453] scsi host7: uas_eh_task_mgmt: ABORT TASK timed out
Oct 24 19:31:32 Hostname kernel: [ 5243.590465] sd 7:0:0:0: [sdb] uas_eh_abort_handler ffff8800478f7980 tag 6, inflight: CMD OUT
Oct 24 19:31:32 Hostname kernel: [ 5243.590468] scsi host7: uas_eh_task_mgmt: ABORT TASK: error already running a task
Oct 24 19:31:33 Hostname kernel: [ 5244.494960] sd 7:0:0:0: [sdb] abort completed
Oct 24 19:31:33 Hostname kernel: [ 5244.495085] sd 7:0:0:0: [sdb] abort completed
Oct 24 19:31:38 Hostname kernel: [ 5249.446365] sd 7:0:0:0: [sdb] uas_eh_abort_handler ffff8800478f6600 tag 12, inflight: done
Oct 24 19:31:38 Hostname kernel: [ 5249.446386] general protection fault: 0000 [#1] SMP
Oct 24 19:31:38 Hostname kernel: [ 5249.446419] Modules linked in: des_generic md4 pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) rfcomm bnep bluetooth 6lowpan_iphc nfsd auth_rpcgss nfs_acl nfs lockd sunrpc nls_utf8 cifs
fscache dm_crypt nls_iso8859_1 joydev keucr(C) snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi intel_rapl x86_pkg_temp_thermal intel
_powerclamp coretemp kvm_intel kvm crct10dif_pclmul snd_seq parport_pc crc32_pclmul snd_seq_device ghash_clmulni_intel ppdev snd_timer cryptd lp arc4 snd parport rt2800pci rt2800mmio rt2800lib rt2x00pci rt2x00mmio serio_raw rt2x00lib mac
80211 cfg80211 lpc_ich mei_me mei eeprom_93cx6 crc_ccitt soundcore shpchp mac_hid hid_generic usbhid hid uas usb_storage i915 video i2c_algo_bit psmouse drm_kms_helper ahci r8169 drm libahci mii
Oct 24 19:31:38 Hostname kernel: [ 5249.446904] CPU: 0 PID: 160 Comm: scsi_eh_7 Tainted: G         C OE 3.16.0-51-generic #69~14.04.1-Ubuntu
Oct 24 19:31:38 Hostname kernel: [ 5249.446952] Hardware name: Hewlett-Packard G5460uk/2ABF, BIOS 7.08 06/02/2011
Oct 24 19:31:38 Hostname kernel: [ 5249.446988] task: ffff8802336a28c0 ti: ffff88022fb4c000 task.ti: ffff88022fb4c000
Oct 24 19:31:38 Hostname kernel: [ 5249.447026] RIP: 0010:[<ffffffffc0337602>]  [<ffffffffc0337602>] uas_mark_cmd_dead+0x62/0xd0 [uas]
Oct 24 19:31:38 Hostname kernel: [ 5249.447078] RSP: 0018:ffff88022fb4fde8  EFLAGS: 00010086
Oct 24 19:31:38 Hostname kernel: [ 5249.447106] RAX: dead000000200200 RBX: ffff8800478f6718 RCX: dead000000100100
Oct 24 19:31:38 Hostname kernel: [ 5249.447142] RDX: ffff8800478f6738 RSI: ffff88023f40d418 RDI: 0000000000000046
Oct 24 19:31:38 Hostname kernel: [ 5249.447178] RBP: ffff88022fb4fe00 R08: 0000000000000086 R09: 000000000000047f
Oct 24 19:31:38 Hostname kernel: [ 5249.447214] R10: 0000000000000000 R11: ffff88022fb4f8de R12: ffff8800b4eb4848
Oct 24 19:31:38 Hostname kernel: [ 5249.447250] R13: 0000000000050000 R14: ffff8800478f6718 R15: ffff88022fb4fe58
Oct 24 19:31:38 Hostname kernel: [ 5249.447287] FS:  0000000000000000(0000) GS:ffff88023f400000(0000) knlGS:0000000000000000
Oct 24 19:31:38 Hostname kernel: [ 5249.447331] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 24 19:31:38 Hostname kernel: [ 5249.447360] CR2: 00007f4713015080 CR3: 0000000003c13000 CR4: 00000000000427f0
Oct 24 19:31:38 Hostname kernel: [ 5249.447396] Stack:
Oct 24 19:31:38 Hostname kernel: [ 5249.447407]  ffff8800b4eb4720 ffff8800b4eb4810 ffff8800478f6600 ffff88022fb4fe38
Oct 24 19:31:38 Hostname kernel: [ 5249.447448]  ffffffffc033a02e 0000000000000282 ffff8800478f6618 ffff88022fb4fe70
Oct 24 19:31:38 Hostname kernel: [ 5249.447488]  ffff8800478f6600 ffff88022fb4fe80 ffff88022fb4fec8 ffffffff8150b147
Oct 24 19:31:38 Hostname kernel: [ 5249.447529] Call Trace:
Oct 24 19:31:38 Hostname kernel: [ 5249.447548]  [<ffffffffc033a02e>] uas_eh_abort_handler+0x7e/0xed [uas]
Oct 24 19:31:38 Hostname kernel: [ 5249.447586]  [<ffffffff8150b147>] scsi_error_handler+0x567/0x850
Oct 24 19:31:38 Hostname kernel: [ 5249.447618]  [<ffffffff8150abe0>] ? scsi_eh_get_sense+0x2c0/0x2c0
Oct 24 19:31:38 Hostname kernel: [ 5249.447652]  [<ffffffff810915a2>] kthread+0xd2/0xf0
Oct 24 19:31:38 Hostname kernel: [ 5249.447679]  [<ffffffff810914d0>] ? kthread_create_on_node+0x1c0/0x1c0
Oct 24 19:31:38 Hostname kernel: [ 5249.447715]  [<ffffffff8176f2d8>] ret_from_fork+0x58/0x90
Oct 24 19:31:38 Hostname kernel: [ 5249.447745]  [<ffffffff810914d0>] ? kthread_create_on_node+0x1c0/0x1c0
Oct 24 19:31:38 Hostname kernel: [ 5249.447778] Code: 4d 8b 03 f6 c4 10 75 69 80 e4 bf 48 8b 4b 20 41 c1 e5 10 80 cc 10 44 89 6b 48 48 8d 53 20 89 03 48 8b 43 28 49 81 c4 28 01 00 00 <48> 89 41 08 48 89 08 49 8b 44 24 08 49 89 54 24 08 4
c 89 63 20
Oct 24 19:31:38 Hostname kernel: [ 5249.447934] RIP  [<ffffffffc0337602>] uas_mark_cmd_dead+0x62/0xd0 [uas]
Oct 24 19:31:38 Hostname kernel: [ 5249.447972]  RSP <ffff88022fb4fde8>
Oct 24 19:31:38 Hostname kernel: [ 5249.461286] ---[ end trace a66dbee6e7c12963 ]---
```

---

### Post by matt_symes on 2015-10-24
Hi

What do you have in the file

```
/etc/modprobe.d/ignore_uas.conf
```

Is your second post a typo ?

BTW please use code tags. I have efitdd your third post.

Kind regards

---

### Post by Andrew_Welham on 2015-10-25
Sorry the 2nd post was correct, but i cut and paste info from a web page which changed the background and foreground colours.
please find the contents of the ignore_uas.conf file, and i've also included a copy of lsusb, the two disks in question are are the "Seagate RSS LLC"
The kernel crashes only appear when i'm rsyncing between the two disks, not sure if that is an indication or the speed is so much faster.
I also looking to remove uas completly form the kernel, but not worked it out as yet



```

# lsusb
Bus 002 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 004: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 003: ID 045e:0773 Microsoft Corp.
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0bc2:ab34 Seagate RSS LLC
Bus 004 Device 002: ID 0bc2:ab34 Seagate RSS LLC
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
# more /etc/modprobe.d/ignore_uas.conf
options usb-storage quirks=0bc2:ab34
#

```

---

### Post by Andrew_Welham on 2015-10-25
just realised i missed the :u after the Product_ID
running again, seams slightly slower approx 20%, but no crashes so far.
Looking back this only occurred when copying between the two usb 3 disks, and not copying from one usb3  disk to a network location.
Is this potentially a bug in the linux Kernel and how / how do i report.

---

