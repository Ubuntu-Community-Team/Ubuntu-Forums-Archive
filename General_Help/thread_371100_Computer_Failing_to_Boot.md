---
title: "Computer Failing to Boot"
date: 2007-02-26
forum: General Help
---

### Post by calvinthomas on 2007-02-26
Hi, I have been using Edgy for quite a long time now (since a little before RC1) without any problems however today I have developed quite a serious problem.

My computer is failing to boot around about 4 in 5 times, I have managed to run a fsck manually (it failed auto and asked me to run it) so I typed fsck and it got all the way through fixing a few errors but the error is still there.

Booting up in single session mode (the only way I know to get a scrolling written output I get the following before it stalls, unfortunately I don't know what it means or how to fix it so I'm really hoping someone on here can help.

The error:
```

[17179610.356000] ide: failed opcode was: unknown
[17179610.356000] hda: dma_time_expiry: dma status == 0x20
[17179610.356000] hda: DMA timeout retry
[17179610.356000] hda: timeout waiting for DMAour
[17179610.356000] hda: status error: status = 0x58 {DriveReady SeekComplete DataRequest}
[17179610.356000] ide: failed opcode was: unknown
[17179610.356000] hda: drive not ready for command

```

Just to reiterate, I have been running Ubuntu (well actually Kubuntu, with XGL & Beryl) for a long time now with absolutely no problems. The only thing I've done over the last couple of days is install the Open Office Quickstarter 2 v1.01 and baskets, I've disabled oooqs2 incase that was the issue but its still causing the problem so I don't think its that.

If anymore info is needed please let me know and how to get hold of that info. Thankyou in advance for your assistance.

Calv

P.S. I'm using the latest kernel however the error is the same in the previous one also.

---

### Post by llamakc on 2007-02-26
You may have hardware problems. Could be the disk, the cable, the IDE channel on your mobo.

---

### Post by calvinthomas on 2007-02-26
Wouldn't that cause problems everytime? Further on the same harddisk although different partition [17179610.356000] I have Windows installed and that seems to boot fine

Calv

---

### Post by calvinthomas on 2007-02-26
It seems now, perhaps due to the fsck check that I can get in everytime if I go via single user mode but I can't get in if I try to get in normally, any ideas?

Calv

---

### Post by calvinthomas on 2007-02-28
bump, also the computer doesn't crash when I am in kubuntu at all. I have used it extensively while in (i.e. for about 5 hrs at a time with no problems) however as soon as I reboot I have the problems again.

Is it possible to reinstall all of the bootup stuff that goes with ubuntu but keep everything as it is? 

Calv

---

### Post by calvinthomas on 2007-03-03
Some further information, I managed to take out quiet info on bootup and its freezing at 'Kernel Events Manager' I searched for this on the boards but the only recommendations are that its a power problem which I'm certain its not or to try booting with noapic &/or nolapic. Unfortunately this doesn't help.

Starting to get a bit frustrated with this problem now and I don't fancy reinstalling everything (Thats what I installed Ubuntu to prevent!), if anyone can give me any suggestions that may help, please, please let me know

Calv

---

