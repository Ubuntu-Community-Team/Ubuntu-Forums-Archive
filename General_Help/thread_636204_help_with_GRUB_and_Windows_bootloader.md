---
title: "help with GRUB and Windows bootloader"
date: 2007-12-09
forum: General Help
---

### Post by 360freak on 2007-12-09
I currently have Ubuntu and Kubuntu installed on one hard drive, and Windows installed on another. I'm using GRUB bootloader. How do I set my computer to use windows bootloader on startup instead of GRUB? i need to take off linux for a little bit, and if i simply delete it, when i boot, i get a GRUB booting error at startup.

---

### Post by Nick11 on 2007-12-09
Is it Windows XP or Vista? If it is Vista go here and scroll to the last post:

[http://ubuntuforums.org/showthread.php?t=634306&highlight=nick11](http://ubuntuforums.org/showthread.php?t=634306&highlight=nick11)

Else you have to edit your boot.ini file in XP. You will see instructions in the middle of the thread posted above on how to do that.

---

### Post by uidb4056 on 2007-12-09
You can boot from your windows install media and choose 'recovery console' then you can run from the command line fixmbr (assuming your windows is XP).

This will restore the standard MBR for windows and let's you remove the linux without having boot troubles.

---

### Post by 360freak on 2007-12-10
thanks a bunch! i didnt know you had you use your install disc, i was trying to do it through command prompt. now i have another problem though...i just realized after doing that, that i need to get some music off of my ubunbtu partition. how do i either set it back to GRUB, or access my ubuntu files from windows?

---

### Post by erickramirez on 2007-12-10
Wow! That's a lot of Windows knowledge in a Linux forum.

In any case, I don't believe you'll be able to access your Linux files from Windows (unless you use Samba). For that reason, I created a separate FAT32 partition and save all my files in there so that both XP and Ubuntu can share my files.

Cheers,
Erick Ramirez
Melbourne, Australia

---

### Post by ronmarley1 on 2007-12-10
> **360freak said:**
> thanks a bunch! i didnt know you had you use your install disc, i was trying to do it through command prompt. now i have another problem though...i just realized after doing that, that i need to get some music off of my ubunbtu partition. how do i either set it back to GRUB, or access my ubuntu files from windows?

Take a look at the SuperGrubDisk.  You can download the iso here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Burn the iso and boot the CD.  You can then restore GRUB to boot into Linux.  Once you have copied your music, reboot with the SuperGrubDisk and it also has an option to restore the Windows bootloader.

---

### Post by 360freak on 2007-12-10
thanks!

---

### Post by froy02 on 2007-12-11
Probably easier to boot with live cd to copy your files.

---

### Post by Existentialist on 2007-12-11
You said windows was on a separate hard drive, so you might be able to go in to bios and set the drive with windows as the primary boot device.  If it already is then you installed grub to the mbr on the windows drive so you will want to follow the other posts to restore the windows boot loader.

---

