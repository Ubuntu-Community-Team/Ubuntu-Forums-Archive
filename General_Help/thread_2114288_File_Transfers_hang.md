---
title: "File Transfers hang"
date: 2013-02-09
forum: General Help
---

### Post by Synoc on 2013-02-09
ever since I upgraded to 12.04 (mint first now Vanilla Ubuntu), my file transfers, in this case to or from a USB drive (any USB stick not just one) the transfer locks up every few seconds and remains that way for over a minute at a time, I have looked this up and can't find any solution on the net. anyone know why this is happening? it make it impossible to estimate when a transfer will be done. a 6 gig folder takes 16 minutes it says... but I can't trust that if it keeps hanging. 

This is a brand new install.

---

### Post by Synoc on 2013-02-12
bump

---

### Post by tgalati4 on 2013-02-12
Open a terminal, post the output of:

```
dmesg | tail -50
```

---

### Post by Synoc on 2013-02-13
```

[   19.148909] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.753471] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   19.827739] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   20.213186] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   20.213189] vesafb: scrolling: redraw
[   20.213191] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.214823] vesafb: framebuffer at 0xfb000000, mapped to 0xffffc90012100000, using 1216k, total 1216k
[   20.215127] Console: switching to colour frame buffer device 80x30
[   20.215139] fb0: VESA VGA frame buffer device
[   22.136990] wlan0: authenticate with 74:44:01:46:07:1c (try 1)
[   22.138964] wlan0: authenticated
[   22.139176] wlan0: associate with 74:44:01:46:07:1c (try 1)
[   22.142735] wlan0: RX AssocResp from 74:44:01:46:07:1c (capab=0x411 status=0 aid=1)
[   22.142738] wlan0: associated
[   22.151467] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.952004] wlan0: no IPv6 routers present
[  118.888019] usb 2-4: new high-speed USB device number 4 using ehci_hcd
[  119.057963] Initializing USB Mass Storage driver...
[  119.058097] scsi6 : usb-storage 2-4:1.0
[  119.058166] usbcore: registered new interface driver usb-storage
[  119.058168] USB Mass Storage support registered.
[  119.090250] usbcore: registered new interface driver uas
[  120.056670] scsi 6:0:0:0: Direct-Access     PNY      USB 2.0 FD       8.02 PQ: 0 ANSI: 0 CCS
[  120.057357] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  120.058057] sd 6:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[  120.058525] sd 6:0:0:0: [sdb] Write Protect is off
[  120.058530] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  120.059369] sd 6:0:0:0: [sdb] No Caching mode page present
[  120.059373] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  120.062150] sd 6:0:0:0: [sdb] No Caching mode page present
[  120.062155] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  120.063667]  sdb: sdb1
[  120.066278] sd 6:0:0:0: [sdb] No Caching mode page present
[  120.066283] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  120.066287] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  269.312021] usb 2-1: new high-speed USB device number 5 using ehci_hcd
[  269.453702] scsi7 : usb-storage 2-1:1.0
[  270.453981] scsi 7:0:0:0: Direct-Access     CENTON                    8.07 PQ: 0 ANSI: 2
[  270.454788] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  270.458470] sd 7:0:0:0: [sdc] 15667200 512-byte logical blocks: (8.02 GB/7.47 GiB)
[  270.458967] sd 7:0:0:0: [sdc] Write Protect is off
[  270.458972] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  270.459467] sd 7:0:0:0: [sdc] No Caching mode page present
[  270.459471] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  270.462464] sd 7:0:0:0: [sdc] No Caching mode page present
[  270.462468] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  271.288119]  sdc: sdc1
[  271.290461] sd 7:0:0:0: [sdc] No Caching mode page present
[  271.290465] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  271.290468] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by tgalati4 on 2013-02-13
So you have a Centon 8GB flash drive that shows up correctly on a USB2.0 port.  You plugged the drive in at 270 seconds after boot.  Now try copying some files--whatever you are doing to cause this problem to happen--and run dmesg again to capture any errors.  I use a rule-of-thumb of 5 minutes/gigabyte.  So if you are copying 6GB, expect 30 minutes.  USB drives are convenient, but not fast.
After 30 minutes, check the file structure in nautilus--before unmounting/ejecting or pulling the drive.  This is important.  Pulling the drive beforehand will result in file corruption.

You can test the speed of the USB drive by:

```
sudo hdparm -tT /dev/sdc1
```

As I recall, USB2 has a maximum throughput of 40 Megabits/sec or 5 Megabytes/sec.  Therefore 6GB would take 20 minutes at maximum throughput.  So 30 minutes is not unreasonable.

---

### Post by HermanAB on 2013-02-13
There has been some regressions in the USB drivers.  Try using ionice with cp:
$ ionice -c 3 cp fromfile tofile

---

### Post by philinux on 2013-02-13
Most likely this ongoing and annoying bug.

Copying from usb to hard drive is fine. Other way slows to a crawl but does eventually finish. It seems to affect large files more.

---

### Post by Synoc on 2013-02-13
> **tgalati4 said:**
> So you have a Centon 8GB flash drive that shows up correctly on a USB2.0 port.  You plugged the drive in at 270 seconds after boot.  Now try copying some files--whatever you are doing to cause this problem to happen--and run dmesg again to capture any errors.  I use a rule-of-thumb of 5 minutes/gigabyte.  So if you are copying 6GB, expect 30 minutes.  USB drives are convenient, but not fast.
After 30 minutes, check the file structure in nautilus--before unmounting/ejecting or pulling the drive.  This is important.  Pulling the drive beforehand will result in file corruption.

You can test the speed of the USB drive by:

```
sudo hdparm -tT /dev/sdc1
```

As I recall, USB2 has a maximum throughput of 40 Megabits/sec or 5 Megabytes/sec.  Therefore 6GB would take 20 minutes at maximum throughput.  So 30 minutes is not unreasonable.

my post was after a large file transfer of 1 GB. it froze twice within the write. I will however run another. 

This is the output RIGHT before the write.
```

[  269.312021] usb 2-1: new high-speed USB device number 5 using ehci_hcd
[  269.453702] scsi7 : usb-storage 2-1:1.0
[  270.453981] scsi 7:0:0:0: Direct-Access     CENTON                    8.07 PQ: 0 ANSI: 2
[  270.454788] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  270.458470] sd 7:0:0:0: [sdc] 15667200 512-byte logical blocks: (8.02 GB/7.47 GiB)
[  270.458967] sd 7:0:0:0: [sdc] Write Protect is off
[  270.458972] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  270.459467] sd 7:0:0:0: [sdc] No Caching mode page present
[  270.459471] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  270.462464] sd 7:0:0:0: [sdc] No Caching mode page present
[  270.462468] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  271.288119]  sdc: sdc1
[  271.290461] sd 7:0:0:0: [sdc] No Caching mode page present
[  271.290465] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  271.290468] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[12194.922352] sdc: detected capacity change from 8021606400 to 0
[12200.211982] sdb: detected capacity change from 4022337024 to 0
[12203.389110] usb 2-1: USB disconnect, device number 5
[12227.203870] usb 2-4: USB disconnect, device number 4
[12259.871543] cfg80211: All devices are disconnected, going to restore regulatory settings
[12259.871551] cfg80211: Restoring regulatory settings
[12259.871556] cfg80211: Calling CRDA to update world regulatory domain
[12259.876671] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[12259.876676] cfg80211: World regulatory domain updated:
[12259.876679] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[12259.876683] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12259.876687] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12259.876690] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12259.876694] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12259.876698] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12261.067828] wlan0: authenticate with 74:44:01:46:07:1c (try 1)
[12261.069771] wlan0: authenticated
[12261.088964] wlan0: associate with 74:44:01:46:07:1c (try 1)
[12261.092506] wlan0: RX ReassocResp from 74:44:01:46:07:1c (capab=0x411 status=0 aid=1)
[12261.092508] wlan0: associated
[12498.160024] usb 2-1: new high-speed USB device number 6 using ehci_hcd
[12498.300335] scsi8 : usb-storage 2-1:1.0
[12499.302026] scsi 8:0:0:0: Direct-Access     CENTON                    8.07 PQ: 0 ANSI: 2
[12499.302778] sd 8:0:0:0: Attached scsi generic sg2 type 0
[12499.306067] sd 8:0:0:0: [sdb] 15667200 512-byte logical blocks: (8.02 GB/7.47 GiB)
[12499.306508] sd 8:0:0:0: [sdb] Write Protect is off
[12499.306512] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[12499.307016] sd 8:0:0:0: [sdb] No Caching mode page present
[12499.307021] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[12499.309758] sd 8:0:0:0: [sdb] No Caching mode page present
[12499.309763] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[12500.138658]  sdb: sdb1
[12500.141506] sd 8:0:0:0: [sdb] No Caching mode page present
[12500.141509] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[12500.141512] sd 8:0:0:0: [sdb] Attached SCSI removable disk

```

In the interim, while I perform a 3 GB write. to the drive. How do I check the file structure in nautilus? I always manually unmount the drive before pulling it, but I've never heard of checking the file structure after a write. Unless you mean if the file has not finished copying. Either way how do I use Nautilus to check the file structure

3.1 GB file transfer, average write speed 4-4.5 MB/sec. and just for annoyance, I did not notice a hang in the first GB. after that it's harder to notice: BTW the drive was removed and reinserted as sdb
```

[  269.312021] usb 2-1: new high-speed USB device number 5 using ehci_hcd
[  269.453702] scsi7 : usb-storage 2-1:1.0
[  270.453981] scsi 7:0:0:0: Direct-Access     CENTON                    8.07 PQ: 0 ANSI: 2
[  270.454788] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  270.458470] sd 7:0:0:0: [sdc] 15667200 512-byte logical blocks: (8.02 GB/7.47 GiB)
[  270.458967] sd 7:0:0:0: [sdc] Write Protect is off
[  270.458972] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  270.459467] sd 7:0:0:0: [sdc] No Caching mode page present
[  270.459471] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  270.462464] sd 7:0:0:0: [sdc] No Caching mode page present
[  270.462468] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  271.288119]  sdc: sdc1
[  271.290461] sd 7:0:0:0: [sdc] No Caching mode page present
[  271.290465] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  271.290468] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[12194.922352] sdc: detected capacity change from 8021606400 to 0
[12200.211982] sdb: detected capacity change from 4022337024 to 0
[12203.389110] usb 2-1: USB disconnect, device number 5
[12227.203870] usb 2-4: USB disconnect, device number 4
[12259.871543] cfg80211: All devices are disconnected, going to restore regulatory settings
[12259.871551] cfg80211: Restoring regulatory settings
[12259.871556] cfg80211: Calling CRDA to update world regulatory domain
[12259.876671] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[12259.876676] cfg80211: World regulatory domain updated:
[12259.876679] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[12259.876683] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12259.876687] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12259.876690] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12259.876694] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12259.876698] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12261.067828] wlan0: authenticate with 74:44:01:46:07:1c (try 1)
[12261.069771] wlan0: authenticated
[12261.088964] wlan0: associate with 74:44:01:46:07:1c (try 1)
[12261.092506] wlan0: RX ReassocResp from 74:44:01:46:07:1c (capab=0x411 status=0 aid=1)
[12261.092508] wlan0: associated
[12498.160024] usb 2-1: new high-speed USB device number 6 using ehci_hcd
[12498.300335] scsi8 : usb-storage 2-1:1.0
[12499.302026] scsi 8:0:0:0: Direct-Access     CENTON                    8.07 PQ: 0 ANSI: 2
[12499.302778] sd 8:0:0:0: Attached scsi generic sg2 type 0
[12499.306067] sd 8:0:0:0: [sdb] 15667200 512-byte logical blocks: (8.02 GB/7.47 GiB)
[12499.306508] sd 8:0:0:0: [sdb] Write Protect is off
[12499.306512] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[12499.307016] sd 8:0:0:0: [sdb] No Caching mode page present
[12499.307021] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[12499.309758] sd 8:0:0:0: [sdb] No Caching mode page present
[12499.309763] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[12500.138658]  sdb: sdb1
[12500.141506] sd 8:0:0:0: [sdb] No Caching mode page present
[12500.141509] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[12500.141512] sd 8:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by tgalati4 on 2013-02-13
You can use Nautilus to browse the USB after you think the file transfer is complete.  Go through the file structure of the USB and check the file sizes to ensure that the sizes match up.  I also run md5sum and check that on both the source file and the destination file--especially on large files like ISO's.

Try the ionice command suggested by HermanAB and pay attention to the total time it takes to copy your files using the time command:

```
time ionice -c3 sourcefile destinationfile
```

It looks like your throughput matches USB2 performance.  It could also be the USB flash drive controller that gets slower when over 50% of the drive is used.  It makes the wear-leveling algorithms work harder.

---

