---
title: "Ipod Mount problems"
date: 2007-05-28
forum: General Help
---

### Post by Muntted on 2007-05-28
I am having problems having my ipod mount.

I did a fresh install of ubuntu, updated everything and installed amarok.

With amorok closed I connected and disconnected the ipod three times and everything was working. Then I opened up amarok and it was working in there. I disconnected it and tried reconnecting it and all of a sudden the ipod will not mount.

I have done some questioning in the IRC forum and have not been able to fix it.

---

### Post by shanike on 2007-05-28
i believe i had similar problem, this is how i solved it:
open up computer> right click on your ipod > properties > volume and drive tabs:
delete any mount options here. eject your ipod. reconnect. now it should work ok.
:D

---

### Post by Muntted on 2007-05-28
> **shanike said:**
> i believe i had similar problem, this is how i solved it:
open up computer> right click on your ipod > properties > volume and drive tabs:
delete any mount options here. eject your ipod. reconnect. now it should work ok.
:D

Thats the thing, Nothing even shows up in computer or on the desktop

---

### Post by Muntted on 2007-05-28
when doing a 'dmesg' command the following shows up, so it is still being reckognised by the system.
[I]
[ 3675.100000] sd 7:0:0:0: Attached scsi removable disk sde
[ 3675.100000] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 3707.168000] usb 2-9: USB disconnect, address 5
[ 5546.632000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 5546.632000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a270002a3b292]
[ 5593.444000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000a270002a3b292]
[ 5593.444000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 5593.444000] scsi8 : SBP-2 IEEE-1394
[ 5593.444000] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x8 (firmware_revision 0x0a2700, vendor_id 0x000a27, model_id 0x000021)
[ 5594.452000] ieee1394: sbp2: Logged into SBP-2 device
[ 5594.452000] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 5594.456000] scsi 8:0:0:0: Direct-Access-RBC Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5594.476000] sdd: Spinning up disk.......ready
[ 5598.556000] SCSI device sdd: 39063023 512-byte hdwr sectors (20000 MB)
[ 5598.560000] sdd: Write Protect is off
[ 5598.560000] sdd: Mode Sense: 04 00 00 00
[ 5598.564000] SCSI device sdd: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 5598.568000] SCSI device sdd: 39063023 512-byte hdwr sectors (20000 MB)
[ 5598.572000] sdd: Write Protect is off
[ 5598.572000] sdd: Mode Sense: 04 00 00 00
[ 5598.572000] SCSI device sdd: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 5598.572000]  sdd: sdd1 sdd2
[ 5598.636000] sd 8:0:0:0: Attached scsi removable disk sdd
[ 5598.636000] sd 8:0:0:0: Attached scsi generic sg3 type 14
[/I]

---

### Post by strabes on 2007-05-28
what happens if you do this?

```
sudo mkdir /media/ipod && sudo mount /dev/sdd1 /media/ipod
```

---

### Post by Muntted on 2007-05-28
> **strabes said:**
> what happens if you do this?

```
sudo mkdir /media/ipod && sudo mount /dev/sdd1 /media/ipod
```

"you must specify the filesystem type"

if I mount /dev/sdd2

it mounts but not not completely correctly. The names for everything is jibberish however I can see the data that is there.

amarok still does not want to know about it.

---

