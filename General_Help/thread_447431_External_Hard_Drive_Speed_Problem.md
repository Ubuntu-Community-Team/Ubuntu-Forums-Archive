---
title: "External Hard Drive Speed Problem"
date: 2007-05-18
forum: General Help
---

### Post by SpeakerForTheDead on 2007-05-18
Hey guys, I've searched the forums for this a couple times but so far haven't come up with anything helpful. In any case, I've made the switch from Windows to Ubuntu (Feisty) 100%, and now I want to move everything that I backed up off of an external drive (USB 2.0, NTFS), but it's running ridiculously slow. According to the drive's properties, it is being recognized as "Connection: USB 2.0 at 12 Mbps." Any help would be greatly appreciated.

Speaker

---

### Post by smoker on 2007-05-18
hi, is your drive self-powered, or relying on the usb for power also? have you tried another usb port? also, maybe disconnect anyother usb devices you can in case there is a conflict causing the slowdown,

best of luck

---

### Post by SpeakerForTheDead on 2007-05-18
Just tried what you suggested and no luck... the drive *is* self powered, so I can't imagine that's the problem. Somebody mentioned in another post that drives are mounted, by default, in 'sync' mode and that changing that solved their (similar) problem, but they were running Kubuntu and didn't have any instructions on how to change the setting under Gnome. Any ideas?

Speaker

---

### Post by smoker on 2007-05-18
hi, maybe the drive is at fault, or maybe there is a slowdown reading from an ntfs drive, i've no problems with my usb backup drive, but that is formatted fat32. afraid i can't' help with the 'sync' thing.

you can download 'drive fitness test' and make a bootable floppy or cd and it will check out your drive, from here: [http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)
you may have to enable legacy usb devices in your bios if an older motherboard before DFT will detect your drive.

best of luck

---

### Post by SpeakerForTheDead on 2007-05-18
Thanks for your help smoker... I think I'm going to suck it up and transfer everything off of the drive (slowly), and then reformat the drive to ext3 or Fat32 and hope that solves the problem.

---

