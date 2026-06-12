---
title: "Cloning two hard drives onto one hard drive"
date: 2014-03-05
forum: General Help
---

### Post by Chris62 on 2014-03-05
Hi,

My computer has two hard drives of fairly low capacity which are also quite old. One drive has 64-bit Ubuntu 13.10 installed and the other has 64-bit Windows 7 installed. The Windows drive is divided into C: and D:

 I want to replace both these 80 GB drives, which are getting full,  with a 1TB drive and clone the contents of the other  two drives onto it.
The new drive is not formatted and the first thing I would like to know is whether I should format and partition it before I do anything else. I had thought of having two 500GB partitions, one formatted NTFS and the other EXT4. I would then partition the NTFS partition into C: and D: I know that 'dd' will clone the Ubuntu partition but don't know if it will deal with Windows. The Windows drive has a partition called 'System Reserve; if 'dd' will clone the Windows drive, will it also copy this small "reserve" partition as well?

Could some kind person suggest the best way of going about this, please? I don't mind (too much) the idea of doing a clean install of Ubuntu but I do not want the hassle of trying to persuade Microsoft that I am not trying to pirate my copy of Windows 7 (that I bought) if I do a clean install of Windows 7.

I realise that this is an ideal opportunity to get shot of Windows, but unfortunately the computer is also used by a somewhat Luddite Windows lover who will not hear of getting rid of Windows, so it will have to stay

---

### Post by oldfred on 2014-03-05
I am not a fan of dd, but have seen some users use it. Then they resize the NTFS partitions. Better to use Windows as after a NTFS partition changes it needs chkdsk. Sometimes you cannot boot and need a Windows repairCD or flash drive to fix it.

  dcfldd  often better than dd
from caljohnsmith post #7
> I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Often drive vendors offer software with drive or you can download to do a image copy.

I would just do a new install of Ubuntu as that will (in effect) also do  a though houseclean system. You will want to copy /home, maybe some settings from /etc if you manually edited hardware settings and a list of installed apps.
      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by Chris62 on 2014-03-06
Many thanks for all that info. I will use Windows to transfer the Windows disc as you suggest. The "horror stories" that I have heard about dd when used by inexperienced people (like me) have put me off using it so I will do a clean install when Ubuntu 14.04 is available and copy /home to it.

Thanks again for your help

---

