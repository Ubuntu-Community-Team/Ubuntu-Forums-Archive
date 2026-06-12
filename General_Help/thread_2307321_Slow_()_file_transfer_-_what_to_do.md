---
title: "Slow (?) file transfer - what to do"
date: 2015-12-23
forum: General Help
---

### Post by zygomorph on 2015-12-23
I am copying files FROM a hard drive with Windows 7 on it (that's in an enclosure connected via USB--probably USB2) to my laptop. 

The laptop has Windows 7 on it right now, but I had trouble copying files within Windows so I booted the laptop using a flash drive with Ubuntu on it and am transferring the files that way. 

The laptop's hard drive is an SSD, newish, and presumably fine.  The hard drive in the enclosure is possibly not doing that well and is not an SSD. 

I'm transferring 80 gb of music. 30-40 minutes in, speeds have slowed to 16 MB/sec and keep dropping. Files are still being transferred, but it has continued to estimate that it will be another 40 minutes for a while now. 

Questions:

1) I'm just doing the copying via drag and drop.  If I hit the X button to cancel it now, will the files that have already been copied still be on the laptop? 

2) Is slowing to 16 MB/sec Really Bad News? That seems pretty slow, especially since one of the drives is an SSD, but I don't have a good sense. I decided to transfer my music files first, but if my hard drive is possibly on its very last legs, it makes more sense for me to stop copying the music and pull my documents off it first. (Which is how I should have done things to begin with.)

---

### Post by Vladlenin5000 on 2015-12-23
Hi and welcome.

1) Yes.

2) No, not at all. It doesn't matter if one is a SSD. The maximum file transfer rate will ALWAYS be that of the slower drive. Top it with a most likely failing drive in a (notably slower) USB adapter... I think you get the point.

---

### Post by leunam12 on 2015-12-24
I would do it from Linux using rsync and doing a dry run to see which files give me errors and I would delete those files or skip them. Maybe you can do the same with robocopy in Windows. Do some research about robocopy, it's very powerful.

---

