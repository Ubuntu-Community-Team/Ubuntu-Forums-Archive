---
title: "Slow transfers, with a twist"
date: 2015-11-27
forum: General Help
---

### Post by Headcase_Fargone on 2015-11-27
Alright folks, I've been battling this one for almost a week now.  I've been to the IRC channel, I've posted on a few other subs.  This is going to be a bit long, but trust me it's an interesting problem for anyone that wants to read it all.

Media server is running Ubuntu 12.04 on an SSD with a four drive RAID5 array, on a gigabit LAN with a 100Mb WAN connection.  Until last weekend I typically would see 60-100MBps transfers over the LAN, and downloads on that box would consistently hit 10MBps.

Now, LAN transfers are capped at exactly 11.1MBps and WAN downloads (I've tried HTTP, FTP, and even Usenet) at exactly 1.1MBps.  I thought it was a bad router or switch, but it's not, as you'll see.

Another symptom (the strangest one) is that downloading on this box brings my router to its knees.  Pinging google.com from another desktop on the same LAN typically yields a 16ms ping.  When anything is downloading on this media server (at 1.1MBps), that ping on the other desktop jumps to 600-800ms.  Pings between other devices on the same LAN go from <1ms to >20ms.  My router's traffic manager shows nonsense readings while a download is running on this media server.  I watched the router report 32GB of data had been uploaded (in spikes) over a 30 second period while a download was running.

But wait, there's more.  I removed this box from the network entirely and tested transfer speeds internally.  Copying a large file from the array to the SSD yielded 8MBps, when typically that would be closer to 50MBps before.

This led me to removing all drives (OS SSD and four RAID HDDs) and installing Ubuntu 15.10 on a spare SSD I had lying around.  Transfers to and from that box with that installation work perfectly fine.  No network slowdown when downloading either.

I think I've ruled out any kind of hardware issue at this point.  I've even tried booting an older kernel and the issue persisted.  It has to be a software problem.  The only changes I've made to this box in years has been allowing the update manager to install updates on a regular basis and as I said above this just started last weekend (I first noticed it 2015-11-21).

Has anyone seen anything like this before?  I'm stumped.

---

