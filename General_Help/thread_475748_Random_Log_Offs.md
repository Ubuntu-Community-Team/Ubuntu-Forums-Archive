---
title: "Random Log Offs"
date: 2007-06-16
forum: General Help
---

### Post by wjeasterday on 2007-06-16
HI,

I just installed 7.04 Feisty, and ran the update manager.  I am running a custom set-up, P4 2.4 GHz, 1 Gig of Ram, two 80 Gig HDs, ATI Raedon 8500 64 Mb, and a NetGear WG311T wireless card.  I have a problem with Feisty just randomly logging me off, and then I have to log back in.  I've read that it might be a power supply issue, but I was running WinXP with no problems before I installed Feisty.  I have also read that it might be a problem with the screensaver as well, but it only seems to restart if I'm working on it, so the screen saver never comes on.  I have noticed however that when it happens a screen is shown like when linux starts up listing the services and stuff that are being started and if they passed or not, and I noticed that is says something has failed (it is in bright red), but the screen disappears to quickly for me to read it. Please help!


WJE

---

### Post by Reugen on 2007-06-16
try dmesg in a terminal, since its not clear what the error is coming from thats probably the best place to look.  Paste sections of the output that have errors here.  you could also check your kdm and gdm logs for errors in /var/log/.  I also had a similar problem with a keyboard that had a stuck power button, but your not havng trouble in xp so thats doubtful here.
Hope that helps
 Reugen

---

### Post by wjeasterday on 2007-06-24
Sorry for the long delay!  It's been a busy week.  Anyways, this is the only thing from dmesg that seemed to show an error:
3, UDMA(100)
[   27.035307] hdb: cache flushes supported
[   27.035344]  hdb: hdb1
[   27.077834] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[   27.077846] Uniform CD-ROM driver Revision: 3.20
[   27.282765] usb 1-1: USB disconnect, address 2
[   27.525903] Attempting manual resume
[   27.525908] swsusp: Resume From Partition 254:1
[   27.525910] PM: Checking swsusp image.
[   27.526065] PM: Resume from disk failed.
[   27.535411] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   27.572464] kjournald starting.  Commit interval 5 seconds
[   27.572477] EXT3-fs: mounted filesystem with ordered data mode.
[   27.710981] usb 1-1: configuration #1 chosen from 1 choice
[   27.726961] input: USB Optical Mouse as /class/input/input3
[   27.726986] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:10.

Thanks!

WJE

---

