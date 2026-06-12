---
title: "Attempt to revive a dead iPod. SBP2 Timeouts"
date: 2008-02-28
forum: General Help
---

### Post by llano on 2008-02-28
Hey all,

I'm beginning my attempts to revive my now 2-years dead iPod. 3rd Generation regular iPod from back when everything was in black and white. It suffered the classic boot-loop with harddrive failure (folder error icon). To me this means that the only problem is with the harddrive probably having some corrupt sectors on it. Having recently gotten into linux I figure that this problem is solveable because, well, linux seems to be able to do everything better than windows in all my experiences thus far.

My plan is to (from some blog I read a year ago that I can't find now) mount my iPod, repartition and format taking into consideration where bad sectors are, throw necessary firmware/files onto the iPod, and resurrect my old buddy.

2 questions for the community.

1. SBP2 is timing out when trying to connect to the iPod. 

```
[1122705.335352] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[1122705.607123] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[1122781.516046] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[1122782.634969] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[1122782.907277] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a27000264cc87]
[1122782.907903] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[1122783.052387] scsi4 : SBP-2 IEEE-1394
[1122804.034896] ieee1394: sbp2: Error logging into SBP-2 device - timed out
[1122804.034985] sbp2: probe of 000a27000264cc87-0 failed with error -16
[1122804.035004] ieee1394: Failed to create unit 000a27000264cc87-0
[1123675.227351] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[1123675.227388] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a27000264cc87]
[1123699.892255] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[1123773.227580] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[1123774.346520] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[1123774.618746] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000a27000264cc87]
[1123774.618795] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
```

Is there another method to force a connection to the iPod? It's trying to connect on scsi4, but the output of my /proc/scsi/sci only shows my SATA harddrive, no iPod. It did find the guid, vendor_id, etc, as it is listed in /sys/bus/ieee1394/devices

2. Granted that I am able to eventually connect to the iPod. Is there a way to check sector by sector for corrupt portions, and then write them out when I fdisk/mkfs?

Cheers,
llano.

---

