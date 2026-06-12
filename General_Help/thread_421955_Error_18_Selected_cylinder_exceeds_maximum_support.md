---
title: "Error 18: Selected cylinder exceeds maximum supported by BIOS - After menu.lst change"
date: 2007-04-24
forum: General Help
---

### Post by Rhombuss on 2007-04-24
I just tried the solution for rebooting directly into Windows as described [here]("http://ubuntuforums.org/showthread.php?t=394967"). All I did was changed the default to "saved" and entered the grub report [x] command, and now it's having problems starting up Ubuntu.

I get this error message on all the non-recovery Ubuntu kernels:

**Error 18: Selected cylinder exceeds maximum supported by BIOS**

I've searched around and it usually is the result of some boot partition issue, however the only thing I changed was the "saved" in the menu.lst.  Consequently, I changed it back to the "defaultnum" and no dice, it still gives me this error.

Any help or insight is appreciated!

**UPDATE: Issue's been resolved.  Simply reinstalled grub using "grub-install /dev/hda" and it worked.  Still not sure where the error occurred.**

---

### Post by Rhombuss on 2007-04-24
Still searching...

---

### Post by pennyminstrel on 2007-10-26
Hi

I'm getting that same error message and I've been looking at various solutions people have found and this one seems pretty straightforward. However can somebody tell me how I would go about **'reinstalled grub using "grub-install /dev/hda" '**.

I hope I don't sound  too stupid asking this, and hopefully if somebody can help I'll have learnt something new.

Penny

---

### Post by Preserved Killick on 2007-10-26
Pennyminstrel wrote:

"I hope I don't sound too stupid asking this, and hopefully if somebody can help I'll have learnt something new."

Me, too.  I upgraded using Synaptic from Feisty to Gutsy.  When I rebooted, I got Error 18.  If reinstalling grub will work, what do I need to do?  I'm not dual-booting-- this machine has Ubuntu on the 1st hard drive and I mount the second HD for storage/backup.

Thanks!

-- Killick

---

### Post by SpanishFranks on 2007-11-13
Again here. I can't privide any fdisk info as all I get is a permanent 'press any key to continue'. 

Cheers

---

### Post by Preserved Killick on 2007-11-25
I kept getting Error 18 (and Error 17 and Error 15) with my install of Gutsy.  I even did a fresh install from cd and that didn't solve the problem.  what's worse is that this wouldn't happen on every boot-- just some of them.  I would often run fsck.

Eventually I decided I my boot hard drive must be in some kind of intermittent hardware failure.  I put in a new HD and reinstalled Gutsy.  This time all I got was the Intel motherboard splash screen, then a blinking cursor on an otherwise black screen.

I read a lot of various stuff online and decided to reinstall gutsy, but this time I would put /boot in it's own primary (I used 24MB) partition.  You have to use "manual' partitioning to do this.  The rest of the drive I partitioned as / and swap.

I have re-booted four times with no errors since then, so I *think* the problem was grub related-- that grub works better on a small partition.  Since I have little idea how this stuff really works, and I got my 'facts' from the interweb, you should be skeptical of my supposition.

Still, I put /boot into the first part of this disk on a small partition and now things are working.  As long as you've backed up your data, and you're not dual-booting another OS on the same drive, I can't see that trying my solution can hurt.

Killick

---

