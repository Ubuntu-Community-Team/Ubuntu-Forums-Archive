---
title: "USB Drive Blinks Constantly on EXT4 Format"
date: 2012-12-21
forum: General Help
---

### Post by david.rahrer on 2012-12-21
This is an odd issue but I thought I would ask here before going to a bug report.  I've got a new WD Elements external USB 3.0 1TB drive (WDBPCK0010BBK).  I'm running Ubuntu Precise 64bit with 3.2.0-23-generic kernel.  It works fine, but when formatted as ext4, the drive light blinks constantly at approx 2x /sec even at idle.  This happens whether it's running through USB 3 or 2.  Any other format I've tried (NTFS, ext2, ext3) and the light is constant at idle, just as it should be.  

I'm wondering if anyone with more intricate knowledge of the Linux formats might be able to think of a reason the drive would register activity like that but only on ext4.  I'm guessing that this might end up being some sort of kernel bug, but it sure is damned specific.  I have other external USB 2.0 drives and all act as they should.  

The light also stops flashing and goes solid after the partition is unmounted.  I tried running it through an install of Ubuntu on a Vbox machine using Kernel 3.5.1 and the flashing continued, but in a pattern, 3 flashes followed by a pause and then 5 flashes, then over again.  I don't know if the Kernel caused that change or running it through Vbox, but either way something keeps the drive busy or at least makes it blink.  This drive is so small and quiet that I can't tell if it is actually working, but if I had to guess I would say no, the light is just flashing.

If need be I can format as ext3 and leave it at that, but I want to track this down.  The flashing of that rather bright LED makes me nauseas in short order.  I suppose I could put a piece of tape over it but that's not really helping the distro :)

Thanks for any thoughts on this.

---

### Post by hayesman on 2013-02-08
Hi I am having the same blinking issue too. Have you managed to make any progress?

---

### Post by david.rahrer on 2013-02-09
I came across some information (can't remember where now) that described why it was happening in ext4 formatted drives and that it could be fixed with a change to the firmware for the drive if the manufacturer cared to.  Since these drives technically aren't supported on Linux, I doubt that will happen anytime soon. I reformatted to ext3 and it is fine now.

I can't vouch for the reasons, only the solution. You can find quite a few complaints on Google using "excess hard drive activity with ext4" if you care to.

HTH, I should have finished this thread up before with the solution.

---

### Post by david.rahrer on 2013-02-09
I marked this thread solved though my solution is only a workaround. I hope that is ok.

---

