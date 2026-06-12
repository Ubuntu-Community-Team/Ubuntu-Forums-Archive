---
title: "Problems with using DVD -r diagnostic software (cdck)."
date: 2019-01-17
forum: General Help
---

### Post by Robert_Gaines on 2019-01-17
I am having problems with using cdck on Ubuntu Mate 18.04 64 bit. After I had upgraded my PC to 10GB of RAM, I noticed that after I had check the timing of a disc once, Ubuntu was storing the entire disc data onto my memory thus another cdck timing pass would just read the disc data from memory in a few seconds. While this feature is convenient in general use, it makes more timing passes impossible without unmounting the disc. My DVD Recorder often screws up the timing on the first pass because it starts out slow and speeds up returning an "unstable" result. I used to run two cdck timing passes back to back to help get a better timing measurements since the drive would not have time to slow back down again. I don't know if there are better timing programs out there. If I could just prevent Ubuntu from storing the disc data in memory to force it to read it from the disc either in a terminal command or a system setting, that would help a great deal. I don't know if using another DVD drive would help since cdck is really touchy. I tried doing the timing check on my USB DVD reader, but the drive crashes halfway through the disc. It might be defective. On my current internal DVD recorder, I often would start cdck, wait until the drive came up to speed, close the program, and restart it so the disc would be up to speed. I can't do that because it takes the data that was previously read off of memory first destroying the result. Verifying the disc data maybe good enough, but these are data archives.

---

### Post by oldrocker99 on 2019-01-18
A simple verification after burning should be all you need. I have burned a pile of data discs over the years, which I only verified after burning. All those disks are still fine.

---

### Post by #&amp;thj^% on 2019-01-18
+1 with oldrocker99
K3B used to have some good tools when I last used it.(Back in 2009)
But when the need arises i now use QPxtool:[http://qpxtool.sourceforge.net/](http://qpxtool.sourceforge.net/)
for a low-level check. -> with anything new, it has a slight learning curve to it.
You may already know this, to simply see if a drive can be read, you can use "dd". This will read in the contents of the CDROM and will ignore/discard the data (note that the CDROM device may have another name on your system):
[list]
 [*]dd if=/dev/sr0 of=/dev/null

It is also possible to compare this to an ISO image:

[*]dd if=/dev/sr0 | md5sum - /path/to/file.iso[/list]

This will print a checksum for the CD and for the ISO file. If the checksums match, the CD contents match the ISO image.

---

