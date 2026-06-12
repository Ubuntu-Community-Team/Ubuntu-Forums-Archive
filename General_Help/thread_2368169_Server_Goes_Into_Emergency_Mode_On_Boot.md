---
title: "Server Goes Into Emergency Mode On Boot"
date: 2017-08-07
forum: General Help
---

### Post by scambro on 2017-08-07
I have a problem that I'm having a heck of a time troubleshooting.  I have a server when I boot it up, sometimes goes into maintenance/ emergency mode.  I can reliably stop it from doing so by commenting out my sata mount points.  But if I wait for the server to come up, then uncomment those and do sudo mount -a, they mount just fine.  

When I run sudo blkid, I get this:
```
/dev/sda1: UUID="27a06382-c55f-4777-b277-98d06d441371" TYPE="ext4" PARTUUID="a1609c89-01"
/dev/sdb1: UUID="2213b4fd-7190-4b2b-8caf-5bfc00ece31f" TYPE="ext4" PARTUUID="a50ffb38-d4c6-4414-ba22-4cfb0c36ba45"
/dev/sdc1: UUID="82134702-8c47-4404-b456-b8e789889a97" TYPE="ext4" PARTUUID="620990be-54f1-4b21-8b58-fb11f0e7d248"
```

My fstab looks like this:

```
# / was on /dev/sdb1 during installation
UUID=27a06382-c55f-4777-b277-98d06d441371 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0

# SATA Devices
#UUID=82134702-8c47-4404-b456-b8e789889a97   /media/serv02bay02  ext4   errors=remount-ro    0    1
#UUID=2213b4fd-7190-4b2b-8caf-5bfc00ece31f   /media/serv02bay03  ext4   errors=remount-ro    0    1
```

When I watch it boot up, I can see the message that says "A start job is running for ...ece31f" and then it rotates to show "...89a97."  So I know it's complaining about these two, but I have no idea why.  I should also say, sometimes I've booted it up with those entries in my fstab and not had an issue.  At this point I'm at a loss as to what's wrong with this.  I've had to reboot it remotely before and simply commented these lines out, waited for it to come back, and manually mounted, but that's not right obviously.

Any ideas what I should check?  Thanks!

---

### Post by scambro on 2017-08-07
A followup, in journalctl --boot=-1 (for a failed boot), I see this, but it also doesn't give me much detail as to why this is happening...

```

Aug 07 17:44:25 serv02 kernel: sd 2:0:0:0: Attached scsi generic sg1 type 0
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: Attached scsi generic sg2 type 0
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: Attached scsi generic sg3 type 0
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: [sdb] physical block alignment offset: 4096
Aug 07 17:44:25 serv02 kernel: sd 2:0:0:0: [sda] 937703088 512-byte logical blocks: (480 GB/447 GiB)
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: [sdb] 4096-byte physical blocks
Aug 07 17:44:25 serv02 kernel: sd 2:0:0:0: [sda] Write Protect is off
Aug 07 17:44:25 serv02 kernel: sd 2:0:0:0: [sda] Mode Sense: 7f 00 00 08
Aug 07 17:44:25 serv02 kernel: sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: [sdc] physical block alignment offset: 4096
Aug 07 17:44:25 serv02 kernel: random: fast init done
Aug 07 17:44:25 serv02 kernel:  sda: sda1
Aug 07 17:44:25 serv02 kernel: sd 2:0:0:0: [sda] Attached SCSI disk
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: [sdb] Write Protect is off
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: [sdb] Mode Sense: 7f 00 00 08
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: [sdc] 4096-byte physical blocks
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: [sdc] Write Protect is off
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: [sdc] Mode Sense: 7f 00 00 08
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 07 17:44:25 serv02 kernel:  sdb: sdb1
Aug 07 17:44:25 serv02 kernel: sd 2:0:1:0: [sdb] Attached SCSI disk
Aug 07 17:44:25 serv02 kernel:  sdc: sdc1
Aug 07 17:44:25 serv02 kernel: sd 2:0:2:0: [sdc] Attached SCSI disk
Aug 07 17:44:25 serv02 kernel: EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 07 17:44:25 serv02 kernel: ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 07 17:44:25 serv02 kernel: ERST: NVRAM ERST Log Address Range not implemented yet.

```
...
```

Aug 07 17:45:24 serv02 systemd[1]: Received SIGRTMIN+20 from PID 692 (plymouthd).
Aug 07 17:45:54 serv02 systemd[1]: dev-disk-by\x2duuid-2213b4fd\x2d7190\x2d4b2b\x2d8caf\x2d5bfc00ece31f.device: Job dev-disk-by\x2duuid-2213b4fd\x2d7190\x2d4b2b\x2d8caf\x2d5bfc00ece31f.device/start timed out.
Aug 07 17:45:54 serv02 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-2213b4fd\x2d7190\x2d4b2b\x2d8caf\x2d5bfc00ece31f.device.
Aug 07 17:45:54 serv02 systemd[1]: Dependency failed for /media/serv02bay03.
Aug 07 17:45:54 serv02 systemd[1]: Dependency failed for Local File Systems.
Aug 07 17:45:54 serv02 systemd[1]: local-fs.target: Job local-fs.target/start failed with result 'dependency'.
Aug 07 17:45:54 serv02 systemd[1]: local-fs.target: Triggering OnFailure= dependencies.
Aug 07 17:45:54 serv02 systemd[1]: media-serv02bay03.mount: Job media-serv02bay03.mount/start failed with result 'dependency'.
Aug 07 17:45:54 serv02 systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/2213b4fd-7190-4b2b-8caf-5bfc00ece31f.
Aug 07 17:45:54 serv02 systemd[1]: systemd-fsck@dev-disk-by\x2duuid-2213b4fd\x2d7190\x2d4b2b\x2d8caf\x2d5bfc00ece31f.service: Job systemd-fsck@dev-disk-by\x2duuid-2213b4fd\x2d7190\x2d4b2b\x2d8caf\x2d5bfc00ece31f.ser
Aug 07 17:45:54 serv02 systemd[1]: dev-disk-by\x2duuid-2213b4fd\x2d7190\x2d4b2b\x2d8caf\x2d5bfc00ece31f.device: Job dev-disk-by\x2duuid-2213b4fd\x2d7190\x2d4b2b\x2d8caf\x2d5bfc00ece31f.device/start failed with resul
Aug 07 17:45:54 serv02 systemd[1]: dev-disk-by\x2duuid-82134702\x2d8c47\x2d4404\x2db456\x2db8e789889a97.device: Job dev-disk-by\x2duuid-82134702\x2d8c47\x2d4404\x2db456\x2db8e789889a97.device/start timed out.
Aug 07 17:45:54 serv02 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-82134702\x2d8c47\x2d4404\x2db456\x2db8e789889a97.device.
Aug 07 17:45:54 serv02 systemd[1]: Dependency failed for /media/serv02bay02.
Aug 07 17:45:54 serv02 systemd[1]: media-serv02bay02.mount: Job media-serv02bay02.mount/start failed with result 'dependency'.
Aug 07 17:45:54 serv02 systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/82134702-8c47-4404-b456-b8e789889a97.
Aug 07 17:45:54 serv02 systemd[1]: systemd-fsck@dev-disk-by\x2duuid-82134702\x2d8c47\x2d4404\x2db456\x2db8e789889a97.service: Job systemd-fsck@dev-disk-by\x2duuid-82134702\x2d8c47\x2d4404\x2db456\x2db8e789889a97.ser
Aug 07 17:45:54 serv02 systemd[1]: dev-disk-by\x2duuid-82134702\x2d8c47\x2d4404\x2db456\x2db8e789889a97.device: Job dev-disk-by\x2duuid-82134702\x2d8c47\x2d4404\x2db456\x2db8e789889a97.device/start failed with resul

```

---

### Post by scambro on 2017-08-08
Would love to get some input here if possible.  I found a few other instances of this when searching through Google.  Some people got around it by not mounting in fstab, but instead configuring the auto-mounts later.  I'd rather not do that because I don't want one server that has a "different" configuration.  I'd rather know why my mounts are failing on boot and be able to fix it.

Thanks!

---

