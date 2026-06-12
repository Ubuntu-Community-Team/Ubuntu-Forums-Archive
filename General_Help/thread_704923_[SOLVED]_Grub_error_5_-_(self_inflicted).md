---
title: "[SOLVED] Grub error 5 - (self inflicted?)"
date: 2008-02-22
forum: General Help
---

### Post by TravMan63 on 2008-02-22
I have a triple boot system - UbuntuCE, SAM and elive.  A few months ago - I may have edited something to keep it from booting...

Is it possible to cause Grub error 5 (supposed to be a partition error).
I have read that if the controller <> the drive device (not sure what that means) - that could cause problems -- I did disable drives in BIOS (secondary controller - (optical drives - which - somehow the distros find the drives anyway) - perhaps that is an issue

I booted into DSL (live cd) - ran fdisk -lu

it appears all my partitions are there (about 8) - eight!

the active partition is an empty fat partition - if GRUB is trying to boot that - I would think I would receive a file not found error...

the output of fdisk is like

partition 1 * name size
etc
etc
etc - some of the sizes have a '+' by them ---- is that a bad thing?

also - my boot partition is hda5  - all the OS's boot from that partition.

What do I need to check to get this system back up?

TIA for your insight!

(have also tried super grub disk - but it errors out with a :(  )

---

### Post by TravMan63 on 2008-02-23
This was indeed a self inflicted error - yet - I cannot now cause it to repeat.

And, unfortunately I do not have the complete (6 steps - the 1st 5 did not work, but were they part of the...) solution?

It was indeed - in the BIOS settings (Award BIOS AX6B+)

I had the standard BIOS settings for the drive to AUTO - when set to user, it boots.  (read more...)
(later it would boot with AUTO set, and 0's for the sector/heads etc..)

*******************
I went to the HD auto detect menu (in BIOS) - and selected 'normal' (although the other 2 settings also allowed a boot).  (This was the last step performed - so I'm contributing this as the 'fix' for this problem).
*******************

Enabling or disabling the secondary IDE controller made no difference (in my last posting - even though this is disabled - the OS's see it - and allow useage).

I have been able to create the error 'no boot disk' (disabling the primary IDE) - but I cannot recreate the grub error.

---

