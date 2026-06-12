---
title: "Safely editing GRUB loader"
date: 2007-01-11
forum: General Help
---

### Post by remick182 on 2007-01-11
I want to make sure that I edit my grub loader the correct way so as to not cause any conflicts.  From what I've read in the forums here and elsewhere on the internet, it doesn't seem to be too big of a deal to edit the */boot/grub/menu.lst* file.  It looks as though I can add a # in front of any of the lines I don't want to be displayed upon start up so I don't have to actually erase them out of my list altogether.  So it would look something like:

#title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.12-9-386 #root=UUID=5c7ff74a-2440-4049-b88f-21280768333f ro single
#initrd		/boot/initrd.img-2.6.12-9-386
#boot

#title		Ubuntu, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#boot

Am I correct in this assumption?

Also, I know that it's a good idea to back up any configuration file or list in case something gets AFU, but in the case of my GRUB loader, how would I replace it should something cause an error and keep it from loading correctly?  Or is that irreversible?

---

### Post by meng on 2007-01-11
It's always possible to boot using a LiveCD, then tinker around with config files on your Ubuntu partition, so you should still consider having backup configuration files before editing them.
One way of doing this is to use nano with the -B switch:
sudo nano -B /boot/grub/menu.lst

---

### Post by remick182 on 2007-01-11
That's a good point about the live CD...I hadn't thought of that.  I'll keep that in mind.  Thanks!

---

