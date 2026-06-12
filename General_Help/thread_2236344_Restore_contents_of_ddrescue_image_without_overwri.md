---
title: "Restore contents of ddrescue image without overwriting MBR, possible?"
date: 2014-07-26
forum: General Help
---

### Post by dilidon on 2014-07-26
Hi,
I have the following question but I lack a bit in knowledge. From what I understand it could be possible:

I have a dual boot setup (Ubuntu for everything and Win7 for audio/studio work). My hard-drive had a few bad sectors which affected specifically the ability of the W7 partition to boot up. Ubuntu was happy. So, as the SMART tests and also the manufacturer's Seatools say the drive is healthy with some bad sectors (the critical threshold has not been reached and it does not seem to be spreading, also no dying sounds from he drive) I decided to rescue what I could from the Win partition and "destructively erase" (as they happen to call it) the whole drive with the manufacturer's tools (which, as they suggest, may help relocate the bad blocks and leave us happy for a few more years)
.
My new 14.04 is happily up and running. However, I would like to recover the whole contents of the image of the Win7 disk to the 1st primary partition of the drive where a new useless Win7 sits (sp there is a woring bootable "slot" - other solutions did not work and this was recommended on some forums).
Why? Because a lot of work has gone into tweaking the system so that it would not have any hickups, no processes or drivers running to interfere with live recording, low latency etc - a very nutered setup unsuitable for other work - it also almost never connects to the web. So, ideally, it is not just a matter of reinstalling stuff and copying the files I work with. I would like the whole complex setup back.

Ddrescue rescued smth like 99% of the drive and there were errors reported in some audio banks, which is irrelevant at this point. One problem - previously the windows partition was partition #3. And I already tried to recover it to partition #2 before the clean install once, just for testing. I ended up with an unbootable Win system with files in place and the partition mountable through ubuntu, though.

I understand that if I could bytecopy the contents of the image file to the new Win partition *without* wiping out its bootup data this could actually work... May I be right?

Can we do that? How? I would assume I would have to tell dd to skip some 512 bytes in the beginning of the image, perhaps... Or is one just dreaming and should get ready for sleepless nights of reconfiguring? :)

---

### Post by sudodus on 2014-07-26
> **dilidon said:**
> ...

Ddrescue rescued smth like 99% of the drive and there were errors reported in some audio banks, which is irrelevant at this point. One problem - previously the windows partition was partition #3. And I already tried to recover it to partition #2 before the clean install once, just for testing. I ended up with an unbootable Win system with files in place and the partition mountable through ubuntu, though.

I understand that if I could bytecopy the contents of the image file to the new Win partition *without* wiping out its bootup data this could actually work... May I be right?

Yes, I think so. At least with a complete ddrescue backup it will work. It depends what is missing, and you seem confident it is nothing really important that is missing. I have used ddrescue, and I think it is a very good tool. The info page is also very good.

```
info ddrescue
```

> 
Can we do that? How? I would assume I would have to tell dd to skip some 512 bytes in the beginning of the image, perhaps... Or is one just dreaming and should get ready for sleepless nights of reconfiguring? :)

You simply reverse the backup or rescue process, clone from the cloned copy to the internal disk drive. You need not worry about the first 512 bytes.

But you must be ***very careful,*** so that you run the process in the correct direction.

Either make a separate backup of those bytes, and overwrite the MBR of the restored system, or use grub-install to install the bootloader again.

---

### Post by dilidon on 2014-07-26
> You simply reverse the backup or rescue process, clone from the cloned copy to the internal disk drive. You need not worry about the first 512 bytes.
But you must be ***very careful,*** so that you run the process in the correct direction.

Thanks. Meticulous is my middle name :) I actually tried that solution before the whole clean install and wiping the hard-drive game, but to no avail.
The partition image was nicely restored by dd and one was able to access the files via Ubuntu on it. So that got done. But - I never got it to boot again (bootable flags were there and grub had the correct SUID for the disk despite it having moved/changed if I remember correctly).

> Either make a separate backup of those bytes, and overwrite the MBR of the restored system, or use grub-install to install the bootloader again.

Second option, reinstalling grub, did not help during the previous efforts. It helped get back into Ubuntu, sure. Grub found the win partition as well but something about either restoring the partition to the wrong number (compared to the original order) or missing some booting information - I had already deleted the redundant 100 MB Win7 "System Reserved" partition wasting space that was previously #1, and I can hypothesize that the backed up partition did actually not contain the neccessary booting information as that may have been on that 100MB partition). So, all in all, I may actually be in a wrong forum as Ubuntu, dd and grub-install all are working but the booting problem follows after restoring the win partition :) I doubt any win gurus would help me in this one though if I mention Linux :D I thought I'd double check my thinking here as I thought there may have been some extra tricks not instantly visible from manuals.

But! I will try your solution of restoring it again the same way before and then restoring the MBR from a previous backup - that way of thinking did not occur to me before. That would only work, of course, assuming, that windows also stores some information there in addition to what grub does. There is something about the chainloader/windows loader... I haven't fully figured out yet where it lives, I think the answer, in the case the partitions have moved and changed in order and number, is there. I think after restoration win was looking for startup files in a "wrong place", which did not exist anymore.

Thank you.

---

### Post by sudodus on 2014-07-26
It seems to me that you were not restoring the drive, but partitions, and that you tried to put Windows to another place than it was originally. Am I right or wrong?

If the restore process is to work in the meaning that you really restore everything, you should restore the whole drive, provided that you backup up the whole drive.

And if you backup up some partition, you should restore that to the same partition as it was before (same partition number, same size and position on the drive).

Backing up and restoring a whole drive (in the linux meaning as whole mass storage device alias hard disk drive or solid state drive or USB pendrive) is much easier than backing up a partition and having to restore the infrastructure around it to get things the same afterwards. Linux may work anyway, but Windows is quite picky, if somethings was changed.

---

### Post by dilidon on 2014-07-27
Ok. Thank you for this extra explanation. Your assumption is correct. I only imaged the partition where bad sectors lived with ddrescue. And I tried to restore just that image. And to the dismay of windows, to another location in another order on the drive. The whole drive was 750G and I only had a 500G USB drive around so that was what I went with after reading manuals and tutorials. I did restore it to the same size partition but its number was wrong.

I will opt for rebuilding the tweaked win setup then from scratch as I did rescue 99% of the required data via this method. The latency tweaks were a tad more labor and testing intense but that's cool too. At least I'll get a clean system.

Thanks for your pointers! Esp. the way to think about the MBR backup for the future.

(If anyone should bump into this perhaps it will save someone time - I believe after such an invasive manouver the boot settings inside windows should also be changed, even if grub updates itself nicely. However w7 does not have a boot.ini file anymore as XP did that could be manually edited, so most forums recommend using EasyBCD software in this situation to edit what's needed but as I was unable to get a black screen with a blinking cursor I could not get to playing around with that thing in reasonable time. So I simply opted for a clean install with recovering data from the image manually). In any case, this is starting to look like a non-Ubuntu topic :)

---

