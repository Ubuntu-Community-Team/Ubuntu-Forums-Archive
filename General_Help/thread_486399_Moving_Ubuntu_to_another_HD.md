---
title: "Moving Ubuntu to another HD"
date: 2007-06-28
forum: General Help
---

### Post by Tikitiki on 2007-06-28
Hello,

I current have Ubuntu installed onto my internal Hard drive. I'd like to know if there is a way to completely move ubuntu from my internal harddrive to my external usb harddrive.

Thanks,
Ryan

---

### Post by Keen101 on 2007-06-28
noob here myself, but the only easy way I can think of (if it works) is to copy the partitions via Gparted Live-CD.  Perhaps there is a better way, and if there is I am sure someone else will reply to you.


[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-8.iso?modtime=1182962209&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-8.iso?modtime=1182962209&big_mirror=0)



Good luck
-Keen101

---

### Post by aquavitae on 2007-06-28
I think the easiest would be to reinstall to the external, and copy your entire home directory across (for settings).  Also possible copy the /etc directory across for system settings.  You might be able to copy the entire disk using the command 'dd if=/dev/hda of=/dev/sda', obviously substituting the correct drive names: if=<disk-to-copy-from> of=<disk-to-copy-to>.  I'm not sure if that would work properly though with the boot manager.  I suppose you could do that then manually reinstall grub, but I think it would work out much more difficult and time-consuming than just reinstalling.

---

### Post by Keen101 on 2007-06-28
I think aquavitae might be correct. His idea seems like the way to go. Install Ubuntu fresh to the external, then copy you home directory.  (don't forget the hidden files if you want to copy your settings.)



-keen101

---

### Post by aquavitae on 2007-06-29
If you also copy /etc you'll keep system settings (e.g. startup scripts), but be careful with that - you might accidentally overwrite something in the new system which you shouldn't.

---

