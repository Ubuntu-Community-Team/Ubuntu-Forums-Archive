---
title: "GRUB won't boot SATA drive containing XP"
date: 2005-05-10
forum: General Help
---

### Post by malacoda on 2005-05-10
Hi Folks,

By any chance has anyone had any luck getting GRUB to work on a system where Ubuntu is installed to on an IDE drive and WinXP is installed on a SATA?

Ub boots fine but GRUB gives an error if I choose XP.

I've tried remapping per other posts but it didn't do the trick.  I also followed the HOWTO on SATA support posted by jackmacokc but still no luck...

Any help would be _very much_ appreciated as I'd REALLY like to boot into either OS (at least until I'm totally weened off Windows) w/o having to change my BIOS boot order each time.

regards,
Malac

PS Please be gentle w/ any instructions you might be able to provide as I am quite a noob...

---

### Post by shakin on 2005-05-10
I don't have a solution, but I think the problem is that the SATA drivers aren't loaded until after the system is. Try this: add an fstab entry to mount your Windows drive on boot, then reboot and see if it works. I bet it won't, but if you then run 'sudo mount -a' it will mount fine, proving that your fstab entry is working.

I have the same issue here, but haven't looked for a solution yet.

---

### Post by iNs4ne on 2005-05-11
My XP boots fine from a SATA hard drive: 
grub just shows some garbage, and i need to press [ENTER] for it to continue...

this is working since a fresh heary install (on a 8GB ATA HDD)

btw, while booting my SATA partitions also don't get mounted, but no big problem there i guess :)

Sorry if i can't help, but that *should* just work i guess...

---

### Post by malacoda on 2005-05-11
Wish it were that easy but no luck.  I was hoping to keep XP on the faster drive since it's a bit of a cumbersome beast but I think I'll try moving it to the IDE drive and reinstalling Ubuntu onto the SATA... the hope being that the new primary SATA-linux 'default' drive will load trouble free and GRUB will be able to also recognize the secondary IDE drive w/o issue...

Malac

---

