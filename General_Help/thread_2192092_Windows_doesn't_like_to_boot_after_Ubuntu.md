---
title: "Windows doesn't like to boot after Ubuntu"
date: 2013-12-05
forum: General Help
---

### Post by mikeebean on 2013-12-05
I dual boot Ubuntu 12.04 with Windows on my laptop. Originally the laptop came with Vista, but I've since installed Windows 7 over it. Both versions of Windows had the same issue.

I can shutdown Windows and reboot into it without issue. However, after I use Ubuntu, I always have trouble getting back into Windows.

I select Windows 7 from Grub, and Windows begins to boot with the normal animated logo, but then it fails and goes back to Grub. I have to go through this process two or three times before Windows will boot all the way. (Sometimes I select Sartup Repair to kick-start it.)

Can anyone suggest a solution to this issue? Thank you!

Michael

---

### Post by electrohandyman501 on 2013-12-05
I can't say as I remember how I did it to mine, my install is chainloaded, I have 2 boot screens. I'm booting win7 and 12.10 Ubuntu as a dual boot setup.
My 1st screen is a windows(mbr) boot options with linux.
My 2nd boot screen is the Grub boot screen.

So when I boot windows it hasn't been thru the Grub menu yet.

---

### Post by oldfred on 2013-12-05
Is Windows hibernated? That almost always causes similar issues as Windows does not want to come out of hibernation from a grub menu boot. 

But grub menu boot is really the same as a boot from MBR, so issue may be more with Windows not closing correctly?

---

### Post by Impavidus on 2013-12-06
Do you access the Windows C partition from Ubuntu? That may sometimes cause issues, although usually not with exactly your symptoms.

---

### Post by codenine75a on 2013-12-06
Use an emergency boot disk and restore your boot partition.  This may wipe your ubuntu set up.  I always made the Windows higher priority because of the applications that i used to use.

---

### Post by jeremy1701 on 2013-12-06
I'm not sure what you mean by kick-start... What exactly happens when you select Startup Repair? Does Windows just boot normally, do you get error messages, or maybe the "Start Windows Normally" screen?

---

### Post by mikeebean on 2014-03-16
So sorry I never came back to this! Since the problem seemed to be Windows-related instead of caused by Ubuntu, I posted over at Bleeping Computer, solved the problem with EasyBCD and it slipped my mind to come back here. I hope it's ok to put a link to my post over there in case anyone else is having a similar issue:

[www.bleepingcomputer.com/forums/t/520501/dual-booting-issues-ubuntuwindows-7/]("http://www.bleepingcomputer.com/forums/t/520501/dual-booting-issues-ubuntuwindows-7/")

---

