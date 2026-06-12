---
title: "Live CD if cant boot from cd drive; how?"
date: 2005-05-21
forum: General Help
---

### Post by trashman on 2005-05-21
Couldn't find anything about this in the forums so sorry if this question has been answered before.  I'm unable to set my bios to boot from the cd drive.  Is there any way to start Live CD from a dos prompt, or whatever?  I'm running win98.  Thanks.

---

### Post by stevenyu on 2005-05-21
nope

---

### Post by camote on 2005-05-28
[QUOTE=trashman]Couldn't find anything about this in the forums so sorry if this question has been answered before.  I'm unable to set my bios to boot from the cd drive.  Is there any way to start Live CD from a dos prompt, or whatever?  I'm running win98.  Thanks.[/QUOTE]
 I am in a similar situation, where I have lost my BIOS password. I tried booting with a startup disk and installing CD-ROM drivers, but am not sure what to do at the prompt. I am sure there is some way to get the Live CD to load. Would it not work in a similar way if the computer was indeed booting from the CD drive?

---

### Post by grim42 on 2005-05-30
camote -- have you tried resetting your BIOS Password?

Most motherboards have a "clear CMOS" jumper that should do the trick. Otherwise unplug battery on motherboard for a few minutes. Make sure power is disconnected when you try this!

If you want to boot from DOS look into using LOADLIN.

---

### Post by gnix_oag on 2005-06-27
can i boot from hd  iso ,  no cdrom

---

### Post by champ_rock on 2005-06-28
hey man
try a great program called smart boot manager......... 
write it using rawrite to a floppy and boot directly from cd....

this link has been discussed clearly in 
[http://ubuntuforums.org/showthread.php?t=43994](http://ubuntuforums.org/showthread.php?t=43994)

---

### Post by linuxrobot on 2005-06-28
On my pc (NEC) with Windows 98, you press "F2" during the first screen that appears during bootup.  It opens the BIOS Setup.  On my pc (when I press F2) it shows the pc seeing the mouse, keyboard, USB ports,and CD-Rom drive.  Then it enters Setup which is a blue, black & white menu.  Use the right arrow key and go over to the tab that says either Boot, or BIOS.  Go down until you see the lines: "1st boot device, 2nd boot device, etc."  There are 4 boot devices listed: Removable Device (floppy), Hard Drive, CD-ROM, & Network Boot.  Select each boot device and use the dash key (in between the +&= and the )&0 keys), to move that item down the list, keep aranging them till the CD-Rom drive is the first boot device.   Then go to the "Exit" tab, and exit saving changes.  The computer will restart and the LIVE CD demo should run.  Remember to change all of the boot devices back to default when you're done, or Windows will try to boot from every CD you have in the CD drive when you reboot.
Well, that's what I did... 
**LinuxRobot**  :)

---

