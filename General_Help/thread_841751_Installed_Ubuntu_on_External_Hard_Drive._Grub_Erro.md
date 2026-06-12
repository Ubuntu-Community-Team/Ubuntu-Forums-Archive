---
title: "Installed Ubuntu on External Hard Drive. Grub Error 21. Can't uninstall?"
date: 2008-06-26
forum: General Help
---

### Post by moneyballs2 on 2008-06-26
Hi,

I've installed the latest version (Hardy Heron) or Ubuntu on an External Harddrive on my friend's Windows Vista computer.

If I try to boot the computer without the external hard drive I get a GRUB error 21 and can't run Vista. To Run Linux I also need to have the Ubuntu Live CD in my drive, otherwise I too get the GRUB error.

I want to completley uninstall Linux but can't. I am just wondering .... How can I uninstall Linux? and, How can I get rid of the Grub 21 error?

ps: I don't have access to a Windows Vista DVD to run Fdisk or Fixmbr.

All help greatly appreciated as I think I've broke my friend's computer!!

Cheers

---

### Post by moneyballs2 on 2008-06-26
oh yeah. Whilst I remember...

When I booted windows (with the external hard drive still in) it was not findable... Meaning I couldn't browse the files of the harddrive, and therefore I couldn't format it or anything like that. I'm unsure of what the letter of it was before installing Linux to it.

So if a fix requires me to know the drive location/letter It won't work :|

Cheers

---

### Post by cariboo on 2008-06-26
You should be able to delete the unreadable partion in the Vista disk management applet. The easiest way to fix the problem is to get a Vists install DVD.

Jim

---

### Post by moneyballs2 on 2008-06-26
> **cariboo907 said:**
> You should be able to delete the unreadable partion in the Vista disk management applet. The easiest way to fix the problem is to get a Vists install DVD.

Jim

Thanks. I will try that tomorrow.

So, by just deleating the unreadable harddrive from being read it should just therefore boot normally?

Or should I run Supergrub as well? Or run Supergrub instead?

(sorry, am really n00bie when it comes to Linux)

---

### Post by ajgreeny on 2008-06-26
> So, by just deleating the unreadable harddrive from being read it should just therefore boot normally?
No, it won't as you have no windows MBR to boot from, you have overwritten it with grub, so I suggest the following.

Supergrub should allow you to boot to either OS on your system, I think, and then you can try to sort out the problem of how it happened in the first place.

The reason is simply that when you now boot without the external disk attached, grub starts as it was put on the MBR of the internal disk in place of the vista bootloader.  However, grub simply points to a file on your ubuntu install, ie the /boot/grub/menu.lst file, and of course, if the external disk is missing, so is that file, hence the error 21.  If you can restore the vista MBR using supergrub, which I think is possible (no knowledge of vista, I'm afraid) you can then get around to reinstalling grub on to the external disk using the ubuntu live CD.  Then if you set your bios to boot first from the external, and second from the internal disks, all should be well; if the external is present grub will appear and give you the choice, if it's not attached the windows MBR will start vista.

I hope that helps, but come back again if you don't understand anything, or need more help.

---

### Post by moneyballs2 on 2008-06-26
ok. so I just run Supergrub and then my Vista should boot normally. I won't reinstall the linux again..

What about the problem of the hard drive not being found in windows? Will that be possible to format afterwards?

I think I've got it now. I will try that tomorrow. Thanks :) I'll update this topic if it works (and if it doesn't)

Cheers :)

---

