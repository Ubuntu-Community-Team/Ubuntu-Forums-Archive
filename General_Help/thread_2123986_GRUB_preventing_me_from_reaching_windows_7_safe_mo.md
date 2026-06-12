---
title: "GRUB preventing me from reaching windows 7 safe mode"
date: 2013-03-09
forum: General Help
---

### Post by nate7 on 2013-03-09
Hi, I've just recently install ubuntu alongside windows 7. I have one problem, I can't reach safe mode when i choose windows 7 in the GRUB menu, and spam F8. If anyone could try to help me reach safe mode it would be great. I was thinking if i could add a safe mode option in the GRUB menu? If that's possible. 

Thanks!

---

### Post by fantab on 2013-03-09
It is not an issue with Grub. Try tapping on F8 as soon as you select Win7 to boot from Grub, keep tapping until you reach 'Safe Mode'. It should boot into safe mode. If you miss, try again.

I don't know if you could add 'Safe Mode' to Grub. My guess is we can't.

---

### Post by nate7 on 2013-03-09
I've tried 6 times, Spamming the heck out of that button, Never worked. It worked last night though.

---

### Post by fantab on 2013-03-09
Yes, Windows does that sometimes when we try to get into safe mode... there is nothing more we can do, I guess. Try to search the www or Windows7 forums... Or wait for someone with more hang of what is going on.

And be gentle with that button... it should work.

---

### Post by oldfred on 2013-03-09
Others have posted that from grub to Windows is very quick, so the window to click f8 is tiny. Or you have to almost click at at the same time.

If you get into Windows best to just make a repairCD or Flash drive.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Larkspur on 2013-03-09
> **nate7 said:**
> Hi, I've just recently install ubuntu alongside windows 7. I have one problem, I can't reach safe mode when i choose windows 7 in the GRUB menu, and spam F8. If anyone could try to help me reach safe mode it would be great. I was thinking if i could add a safe mode option in the GRUB menu? If that's possible.   Thanks!  I don't know about a safe mode option for GRUB, but here's how I boot into safe mode using Vista:  
1. In Windows 7, run System Configuration. 
2. On the Boot tab, select safe mode.  You'll be asked if you want to reboot. 
3. When you do, select Windows again on the GRUB menu 
4. Unless something terrible has happened, Windows will now be in safe mode.  5. 

To return to normal, just run System Configuration again and deselect safe mode.

---

