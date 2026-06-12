---
title: "usb device (lplayer) not connecting"
date: 2008-07-07
forum: General Help
---

### Post by happyisland on 2008-07-07
Ok, I'm getting a weird error that I can't figure out. I hope someone out there in Ubuntuland has got an answer for me. Or at least something I can try...

Here's the deal:

1) I just bought an Iriver lplayer flash-based usb-connecting mp3 player. 
2) for the first few days I had it it worked as expected, connecting to my home computer (ubuntu 8.04) when plugged in to the usb port and allowing for the transferral of files. 
3) this morning it stopped working. Now when I plug it in the player says it's connected, but nothing happens on the computer.
4) I was thinking the player was to blame, especially since i tried it in two different computers (both running ubuntu) and had the same issue.
5) BUT, I just connected it to my little eee PC 900, which runs xandros linux, and the thing works fine! 
6) what the hell?

Any help on diagnosing and fixing this problem would be much appreciated.

Thanks in advance,
HI

---

### Post by happyisland on 2008-07-07
after some further tinkering I've found that when I plug in the music player an icon labeled "USB Drive" shows up in the "Computer" directory. When I unplug the player it disappears. For some reason it's not mounting though. Please help!

---

### Post by alxlabs on 2008-07-07
I had exactly same problem with my phone - I can see music/images etc but it does not mount the phone as usb drive and external flash card was not shown. I just mounted it manually :)

---

### Post by happyisland on 2008-07-08
Can you explain to me how you mounted it? When I right-click and select "mount" nothing happens. No error message, nothing.

---

### Post by happyisland on 2008-07-08
Sorry to bump this thread, but this problem is driving me CRAZY! It's funny because I just spent the entire weekend evangelizing to some apple enthusiasts about how great Ubuntu is, how open source is a must, etc, etc, and now I am experiencing one of those not-ready-for-the-desktop type ubuntu problems. I can't believe that xandros can handle my music player and ubuntu can't. I'm sure it's just like a USB setting I don't know about or something, but it's getting really frustrating that I can't figure it out. 
</rant>

---

### Post by SlCKB0Y on 2008-07-11
I am having the same problem, although mine has never mounted automatically. Maybe there was a software update which broke this in the last week?

This is what dmesg spits out when I connect it.

> [1335224.632585] usb 2-1: new high speed USB device using ehci_hcd and address 65
[1335231.469318] usb 2-1: new high speed USB device using ehci_hcd and address 66
[1335231.603800] usb 2-1: configuration #1 chosen from 1 choice
[1335231.633058] scsi1952 : SCSI emulation for USB Mass Storage devices
[1335231.633668] usb-storage: device found at 66
[1335231.633671] usb-storage: waiting for device to settle before scanning
[1335236.625209] usb-storage: device scan complete
[1335236.675490] scsi 1952:0:0:0: Direct-Access     iriver   Lplayer               PQ: 0 ANSI: 0 CCS
[1335236.683713] sd 1952:0:0:0: [sdb] 7737344 512-byte hardware sectors (3962 MB)
[1335236.685705] sd 1952:0:0:0: [sdb] Write Protect is off
[1335236.685709] sd 1952:0:0:0: [sdb] Mode Sense: 00 12 00 00
[1335236.685711] sd 1952:0:0:0: [sdb] Assuming drive cache: write through
[1335236.693699] sd 1952:0:0:0: [sdb] 7737344 512-byte hardware sectors (3962 MB)
[1335236.695688] sd 1952:0:0:0: [sdb] Write Protect is off
[1335236.695692] sd 1952:0:0:0: [sdb] Mode Sense: 00 12 00 00
[1335236.695694] sd 1952:0:0:0: [sdb] Assuming drive cache: write through
[1335236.695701]  sdb: unknown partition table
[1335236.703592] sd 1952:0:0:0: [sdb] Attached SCSI removable disk
[1335236.703641] sd 1952:0:0:0: Attached scsi generic sg2 type 0

I am however able to manually mount it using the usual commands so I can actually use it. After adding a line in /etc/fstab I can use a mount app in the gnome menu but I would prefer this drive to be automatically handled. 

So If anyone can help I too would be greatful, at least I know im not the only one having this problem.

---

### Post by eternalnewbee on 2008-07-11
Sometimes just rebooting the system helps; with usb drives, vcds and dvds...

---

### Post by SlCKB0Y on 2008-07-13
thanks for the advice but id rather sort this out in a proper, non windows way :)

Would we be warranted in filing a bug for this? And for what would we file it?

---

