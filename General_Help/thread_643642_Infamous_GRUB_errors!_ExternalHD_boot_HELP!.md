---
title: "Infamous GRUB errors! ExternalHD boot HELP!"
date: 2007-12-18
forum: General Help
---

### Post by Tredici on 2007-12-18
Okay, I have been reading through a lot of information about the several errors I am receiving.

First a little background on what I wish to do. I have my internal HD on my laptop partitioned for XP and a separate for Media. I have an external HD that I wish to boot Ubuntu, I used to have 6.10 but my installation was buggy and I installed it several month ago never getting to try much out. I followed the instructions to install Ubuntu back onto my External HD, it went through and seemed to do everything fine until it booted.

[B]#1. With no external HD attached booting from the internal HD I get:
        Error 21

#2. With external HD attached booting from the internal HD I get:
       Error 17

#3. With the external HD attatched booting from the external HD I get:
       Dual Boot Screen, when I press Ubuntu 
          Error 17
       Dual Boot Screen, when I press Windows XP Media Center
          Error 13[/B]


I now run the livecd... and terminal

I type the command: _sudo fdisk -l _: receive the following information
[B]--Device Boot
/dev/sda1... *                            (Is my XP drives)
/dev/sda2...
/dev/sda3...

Device Boot
/dev/sdb1                                (Is my media part in XP)

Device Boot
/dev/sdc1...*                       (Linux)
/dev/sdc2...                         (Extended)
/dev/sdc5...                         (Linux swap / Solaris)[/B]

I now type _sudo grub_ at terminal to get the grub shell, _find /boot/grub/stage1_
    Gives me _(hd2,0)_ which is I believe where my Ubuntu OS is stored

Next I type _sudo gedit /boot/grub/menu.lst_ in the terminal to open the grub menu, however when it opens there is no content inside! I do not know if I am doing this completely wrong or what? Any and all help would be great, I am a newbie so please post good steps for me to follow. I would not like to lose any of my XP information, just want to be able to boot to XP when I want to, and Ubuntu from an external so I can learn more about Linux systems! 

Another thing, my boot order now is set back to default, at the time of installing it I believe my USB HD was first in boot order, then Internal HD. So now it is, _1)USB Floppy 2)CD/DVD ROM 3)Notebook HD 4) USB diskette on key 5)USB HD 6)Network Adapter_

Once again, any and all help/walk-throughs would be great!

*Edit, I have been reading through the GRUB manual and it looks as if I should set up the grub on my hardisk... hd2,0 for the MBR, the only thing I am worried about is getting XP to boot properly as well, so I have not run this command.

---

### Post by Mark_in_Hollywood on 2007-12-18
In googleing for the keywords: grub errors, I came across this:

Gentoo Grub Error Collection
[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

This is all the help I can offer you. I have Error 15 and 17 to deal with.

---

### Post by logos34 on 2007-12-18
to restore windows bootloader:

-->  Use [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

OR

boot frm XP install cd and enter recovery console.  Type **fixmbr** at the prompt (for c: drive).

Ubuntu:

for # 3) above, highlight the ubuntu kernel, then hit 'e' key to edit, 'e' again on the 'root' line and change to (hd0,0).  The 'find' command may return (hd2,0), but the minute you change the bios to boot directly to the usb drive it becomes (hd0).  If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

*The reason the you're getting a blank menu.lst on the live cd is that you have the path wrong (and root has to be mounted).  Mount root partition by clicking on it in Places>computer, then do

sudo gedit **/media/disk/**boot/grub/menu.lst

---

### Post by adrian15 on 2007-12-18
I suppose you will need to edit your usbpendrive menu.lst so that hd1 becomes hd0 because when you boot from the pendrive, the pendrive becomes hd0!

There is a guide that might help you.

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.")

adrian15

---

