---
title: "no boot"
date: 2008-07-09
forum: General Help
---

### Post by AlanInVancouverBC on 2008-07-09
I dual-boot.
This morning I couldn't get past this line in the boot operation:
"ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!"
It actually stops a few lines later with this:
"[18.030690] usb1-2: configuartion #1 chosen from 1 choice"
but I don't think that means anything.

That's when I did the recovery-mode process.

In the normal boot option, I get to: (initramfs) _

*I'm guessing this is a consequence of defragging in XP.*

I still have the directories: ubuntu/disks/boot/grub and the following files in the grub folder:
menu.lst
menu.lst~
default
menu.lst.backup
device.map

---

### Post by rraj.be on 2008-07-09
Try this.It will fix the problem


Reboot and hit Esc when prompted to enter the boot menu.

 Hit 'e' to edit ubuntu. Next select the second line and hit 'e' again. 

Input 'irqpoll' towards the end of the bootline.

 Then hit 'enter' and then 'b' to boot.

---

### Post by AlanInVancouverBC on 2008-07-09
I'm unsure what you meant by "towards the end of the bootline". Also, when I get to my boot options in Linux, I have 4, plus 4 recovery choices that correspond to the 4 main.
They are numbered 16, 17, 18, and 19. I don't know why they are all there. When this page shows up, it seems to "default" to 18.

Anyway, I'm not sure what you mean by "at the boot menu". I get a screen to boot into XP or Ubuntu. I choose Ubuntu, when that opens, I get the 4 (plus 4) choices. Hitting ESC then does nothing. 

So I have entered "irqpoll" on all of the 4 options, without success.

BTW, thanks for your help.

---

