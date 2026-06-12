---
title: "Firewire Ipod on Gusty"
date: 2007-11-12
forum: General Help
---

### Post by nirv117 on 2007-11-12
I was using fiesty fawn previously, and my 20Gb gen 3 ipod worked fine.  I don't connect it very often.  I upgraded to Gusty, and when I tried to update my ipod it never seems to connect.  The ipod itself shows the do not disconnect screen like something is talking to it.  and reading through the kernel log it seems to see the device, but it never mounts it.

Anyone have any ideas or other places to look / read?

Below id the log output from kern.log

Nov 11 23:40:27 Raziel kernel: [  384.553589] ieee1394: Node changed: 1-01:1023 -> 1-00:1023
Nov 11 23:40:27 Raziel kernel: [  384.553601] ieee1394: Node suspended: ID:BUS[1-00:1023]  GUID[0
00a2700025c559d]
Nov 11 23:40:52 Raziel kernel: [  409.951609] ieee1394: Node resumed: ID:BUS[1-00:1023]  GUID[000
a2700025c559d]
Nov 11 23:40:52 Raziel kernel: [  409.951652] ieee1394: Node changed: 1-00:1023 -> 1-01:1023
Nov 11 23:40:52 Raziel kernel: [  409.952065] scsi3 : SBP-2 IEEE-1394
Nov 11 23:40:54 Raziel kernel: [  411.268752] ieee1394: sbp2: Logged into SBP-2 device
Nov 11 23:40:54 Raziel kernel: [  411.268818] ieee1394: sbp2: Node 1-00:1023: Max speed [S400] - 
Max payload [2048]
Nov 11 23:40:54 Raziel kernel: [  411.270831] scsi 3:0:0:0: Direct-Access-RBC Apple    iPod      
       1.53 PQ: 0 ANSI: 2
Nov 11 23:40:57 Raziel kernel: [  413.102014] sd 3:0:0:0: [sdc] Spinning up disk....ready
Nov 11 23:40:57 Raziel kernel: [  414.310394] sd 3:0:0:0: [sdc] 39063024 512-byte hardware sector
s (20000 MB)
Nov 11 23:40:57 Raziel kernel: [  414.312327] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enab
led
Nov 11 23:40:57 Raziel kernel: [  414.314165] sd 3:0:0:0: [sdc] Write cache: disabled, read cache
: enabled, doesn't support DPO or FUA
Nov 11 23:40:57 Raziel kernel: [  414.317255] sd 3:0:0:0: [sdc] 39063024 512-byte hardware sector
s (20000 MB)
Nov 11 23:40:57 Raziel kernel: [  414.319233] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enab
led
Nov 11 23:40:57 Raziel kernel: [  414.321000] sd 3:0:0:0: [sdc] Write cache: disabled, read cache
: enabled, doesn't support DPO or FUA
Nov 11 23:40:57 Raziel kernel: [  414.321008]  sdc: sdc1 sdc2
Nov 11 23:40:57 Raziel kernel: [  414.327583] sd 3:0:0:0: [sdc] Attached SCSI removable disk
Nov 11 23:40:57 Raziel kernel: [  414.327648] sd 3:0:0:0: Attached scsi generic sg3 type 14
Nov 11 23:48:25 Raziel kernel: [  861.940692] ieee1394: Node changed: 1-01:1023 -> 1-00:1023
Nov 11 23:48:25 Raziel kernel: [  861.940704] ieee1394: Node suspended: ID:BUS[1-00:1023]  GUID[0
00a2700025c559d]
Nov 11 23:50:18 Raziel kernel: [  975.060949] ieee1394: The root node is not cycle master capable
; selecting a new root node and resetting...
Nov 11 23:50:18 Raziel kernel: [  975.333133] ieee1394: Node resumed: ID:BUS[1-00:1023]  GUID[000
a2700025c559d]
Nov 11 23:50:18 Raziel kernel: [  975.333176] ieee1394: Node changed: 1-00:1023 -> 1-01:1023
Nov 11 23:50:18 Raziel kernel: [  975.334368] scsi4 : SBP-2 IEEE-1394
Nov 11 23:50:19 Raziel kernel: [  976.602860] ieee1394: sbp2: Logged into SBP-2 device
Nov 11 23:50:19 Raziel kernel: [  976.602920] ieee1394: sbp2: Node 1-00:1023: Max speed [S400] - 
Max payload [2048]
Nov 11 23:50:19 Raziel kernel: [  976.605439] scsi 4:0:0:0: Direct-Access-RBC Apple    iPod      
       1.53 PQ: 0 ANSI: 2

---

### Post by LaVache on 2007-11-15
Ran into this myself.  First time I plugged in the 3rd Gen iPod via firewire it wasn't automatically mounted by Gutsy even though the iPod screen showed "Do Not Disconnect".

I then chose not to heed Apple's advice and unplugged the ipod anyway, waited a second, and then plugged it back in -- this time Gutsy auto-mounted it.  It's worked ever since.

---

