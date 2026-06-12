---
title: "Accidently formatted drive, rec. a way to view disk."
date: 2012-11-18
forum: General Help
---

### Post by Cornova on 2012-11-18
I installed Lubuntu on a really old laptop. I liked the simplicity so much that I decided I wanted to use it on my dual boot desktop (Mint/XP). I backed up all the important stuff from Mint on external drives and intended to wipe Mint with DBAN and do a fresh install of Lubuntu.

Unfortunately, I clicked the "automatic" setting in DBAN and it immediately began formatting both hard drives. I caught it in less than .1% in, but that was enough to make both drives unbootable. I went ahead and completely wiped the Mint drive (using manual setting) hoping I could browse the XP disk and pull off the few audio books and games I had left of importance.

I was unable to browse the XP disk in Lubuntu as it wasn't recognized, however I could see it under the Accessories>Disks application. Under there I did a quick reformat thing (FAT), which appears to basically just name the drive and tell it that it can now be completely written over (rather than actually having been wiped). I can view the disk but there is no data.

My quesion is, because nearly all the data is presumably still on the drive, is there a way that I can view this data and copy anything I want from it? All the crucial stuff was on the external drives, so this isn't a life or death thing, but it would be nice to take a few things off it before I really wipe it.

---

### Post by raja.genupula on 2012-11-18
read this please [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Mark Phelps on 2012-11-18
There is no data being seen on the XP disk because when you reformatted it, you overwrote the partition table -- thus now, all the old file and folder entries are gone.

In my experience, Windows utilities are best at recovering windows filesystems and Linux utilities are best at recovering Linux filesystems.

To see if the XP disk files are recoverable, you will need to connect that drive to a Windows PC, download and install RecoverMyFiles (from Runtime Software), run that in the deepest discovery mode -- and see what it finds.

IF it finds the files and folders you want to recover, you will have to go online and purchase a license.

Your data -- your money -- your choice.

---

### Post by Cornova on 2012-11-18
> **Mark Phelps said:**
> Your data -- your money -- your choice.

Yeah, it looks like it's not worth the trouble. The Linux stuff raja.genupula posted doesn't seem to work (thanks for posting it though). Thankfully I only used it for one program and a game, one of which I discovered works decent enough in Wine.

This may turn out to be a good thing since I kept XP around as a sort of crutch, and am now forced to learn Linux alternatives.

---

### Post by coldraven on 2012-11-18
You could try booting up with Parted Magic and run Testdisk. You would need to do some research first as it is quite powerful and complicated.
Some tips here:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Or run PhotoRec and get it to only search for the file types you need, otherwise it will find thousands of images and image fragments.

---

