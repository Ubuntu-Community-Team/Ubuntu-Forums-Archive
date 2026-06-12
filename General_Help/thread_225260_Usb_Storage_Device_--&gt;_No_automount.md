---
title: "Usb Storage Device --&gt; No automount"
date: 2006-07-29
forum: General Help
---

### Post by ticool on 2006-07-29
Normally USB Storage Devices should appear as scsi device /dev/sdaX
but my Kubuntu Dapper is not willing to do it this way, it only recognises that there is a new usb device and that's all :(

I got absolutly no clue why my kubuntu doesn't act as it should.

Any Suggestions?

Tim

---

### Post by ticool on 2006-07-29
Thats what dmesg said about it 

```

Jul 29 18:37:58 ticool-desktop kernel: [4294849.314000] usb 3-2: USB disconnect, address 2
Jul 29 18:38:53 ticool-desktop kernel: [4294904.771000] usb 3-2: new high speed USB device using ehci_hcd and address 4

```

---

### Post by ticool on 2006-07-29
I checked out the newest kernel in the repositorys 2.6.15-26 even this one ( without restricted modules) didn't recognizes the player as well.

So thats seems not to be the case.

---

