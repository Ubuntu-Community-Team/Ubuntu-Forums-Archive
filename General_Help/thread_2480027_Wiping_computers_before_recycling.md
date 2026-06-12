---
title: "Wiping computers before recycling"
date: 2022-10-16
forum: General Help
---

### Post by greenleader2 on 2022-10-16
Hi all,

I’ve used Ubuntu or the flavours for years now on older machines, but now with the lack of i386 support going forward, and some of these clunkers barely starting up, I was going to drop a few PCs and an old MacBook off at a recycling centre.  I am pretty much a desktop user, so my tech skills are limited.  I was going to use the shred command and use the -z option to zero the drive after shredding. Then maybe reinstall lubuntu on the computers and just encrypt the drives as well (thought I read somewhere that encrypting afterwards is useful if overwriting and zeroing failed on corrupted sectors, but I have no idea if that’s true). Anything I’m missing?  If anyone has any suggestions it would be helpful.

Also if this is the wrong section of the forum, apologies in advance. Wasn’t sure if this was general-related or security-related.

Thanks

---

### Post by QIII on 2022-10-16
By mounting Darik's Boot and Nuke on boot up, you can do a US DoD/State Department level wipe, but it does take a while.

Or you count mount an installation disk and use dd on the hard drive.  

Or you could take the disk to a local wrecking yard and as the operator of the magnetic scrap lifter to pick your drive up with the head for 10 seconds or so.  That would surely degauss it.  It might also do electronic damage, but oh well.

My choice would be DBAN

---

### Post by HermanAB on 2022-10-16
There is a secure erase function built into the device controller of every disk drive for the last 30 years or so. It can be run with the hdparm command.

---

### Post by QIII on 2022-10-20
The one thing that would cause me to shy away from hdparm is something you mentioned:  it is written into the controller.  Who writes the firmware for drives?  (We are talking mechanical drives here.  SSDs are a different matter, and I take it from the OP that these are old, presumably mechanical, devices)

One misgiving with DBAN is that it does not touch the HPA.  However, it does do a thorough job on the rest of the device.  It is noteworthy that the US NSA does not support secure erase on mechanical drives.  But they also suggest physically destroying the devices and securing new ones.

You want to get rid of data.  The risk of rootkits in the HPA is a very good reason for those who receive used machines to buy new data storage devices.  But that's up to them.

The only really good non-destructive method is degaussing.  With a strong enough magnet, you may even wreck the firmware and the permanent magnets.  Blow torching the drive to slag is not a bad option if you go the destructive route.  I use them for target practice and then break out the torch.  But wear a proper respirator.

Mind you, I'm not trying to contradict HermanAB.  Just giving you my opinion.

---

### Post by aug7744 on 2022-10-20
You can try
[https://www.hdat2.com/download.html](https://www.hdat2.com/download.html)
Have an option to wipe disk.
First remove all yours files and partitions and run HDAT2.
Is an simple and fast software without command lines.

---

### Post by ActionParsnip on 2022-10-20
Another way is to destroy the disk with a hammer and replace. Disks are pretty cheap now and a new internal storage will last longer than an older one.

---

### Post by HermanAB on 2022-10-20
The drive controller firmware can micro step the servo and delete the whole surface including space between tracks, and faulty sectors.  The only method better than that is to use the disk for target shooting.

---

### Post by ne29914 on 2022-10-20
I just remove the disk(s) physically and whack them with a large hammer.

---

