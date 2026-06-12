---
title: "Windows bootloader resets GRUB"
date: 2008-01-06
forum: General Help
---

### Post by Visti on 2008-01-06
Hi! I have an annoying problem with my bootloader. I have a few distros installed (OpenSUSE, Ubuntu and Elive, not that that matters) and my Windows XP. However, when I choose Windows from my GRUB Menu it boots into another bootloader (Like a chainboot thing) with two similar choices (Both boots into Windows as normal). 

Now this isn't a problem, except every time I boot Windows it resets it so that the chained bootloader with the two choices becomes the only one and I have to boot my OpenSUSE disc as a rescue, because it allows me to boot from any harddrive, not just the main one.. and then the next time I reboot, the GRUB Menu is back - that is, until I boot Windows and I have to do it all over if I want to enter one of my Linux systems..

What would a solution to this be? Putting GRUB somewhere else? I'm afraid to screw up my carefully arranged XP, though..

Any help would be greatly appreciated,
Visti

---

### Post by yellowbread on 2008-01-06
Could you please post the contents of the file /boot/grub/menu.lst?

---

### Post by archer282 on 2008-01-06
Have you tried reinstalling/reconfiguring grub?

Boot to your Live CD and follow the instructions found here.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html")


Beyond this... I don't think you'll get any answers until your post your grub.conf/menu.lst file...

---

