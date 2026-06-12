---
title: "Hibernating and then running a live CD - a bad idea?"
date: 2007-04-24
forum: General Help
---

### Post by peterx14 on 2007-04-24
Hi all,

I had a bunch of things running on my Ubuntu Edgy install, so I hibernated the machine. Then, I had the bright idea of testing out my newly downloaded Feisty CD - just to see how the desktop-effects work. So that worked, which was nice, and then I booted back into my hibernated Edgy.

All was well, but a few things were odd -- all the media players seemed much louder despite the volume levels being apparently the same. Then I closed Synaptic Package manager (it was open before I hibernated) and it complained about not being able to access a file or something. I closed Firefox but then I couldn't restart it; I figured maybe there was a Firefox process that had got stuck and needed manual killing (it sometimes happens to me) so I tried starting System Monitor, but that wouldn't start either. Then I realised that nothing would start. I already had a terminal open so I check dmesg and it *looked* like the journaling process for Ext3 had restarted and then remounted the drives as read-only.

So then I restarted the machine (it shutdown fine), and when it came up it complained about disk errors on the system volume and dropped me to the terminal and I had to manually fsck /dev/hda1 and hit Y to a load of repairs.

Anyway, there doesn't *appear* to be any damage, but I just wondered if the problem was caused by my hibernating and *then* booting a live-CD. I have heard that live-CDs will use a Linux swap partition if they find one, so I'm guessing that perhaps since I'd hibernated, my swap partition was "in use" and then the live-CD wrote over the top of it?

Any thoughts?

Peter.

---

### Post by hyperair on 2007-04-24
You're right about the swap file I reckon. Also, if you hibernate a system, never ever modify the disks that are mounted in the system. The last time I did that, the entries in my FAT file system (hibernated windows and used linux) screwed up, and everything in the disk was garbled. I had to use photorec to slowly dig out everything from the raw content of the disk.

---

