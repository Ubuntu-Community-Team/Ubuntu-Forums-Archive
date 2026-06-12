---
title: "Ubuntu won't boot. Getting error message."
date: 2015-02-09
forum: General Help
---

### Post by joey20 on 2015-02-09
So I've got a computer that I'm working on without an operating system. I've tried several times to boot with a CD or a USB w/ linux. However, no matter what version I try to install, I get the same error message. What does it mean, and how do I solve it? Any help will be much appreciated, I am at a lost. [ATTACH=CONFIG]259870[/ATTACH]

See attachment.

---

### Post by oldfred on 2015-02-09
this thread mentions this boot parameter
[http://ubuntuforums.org/showthread.php?t=1741556&page=4](http://ubuntuforums.org/showthread.php?t=1741556&page=4)

 And I would try again without quiet splash to see if you still get a kernel panic.
quiet splash acpi_osi = linux

You add parameter the same way as nomodeset:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

