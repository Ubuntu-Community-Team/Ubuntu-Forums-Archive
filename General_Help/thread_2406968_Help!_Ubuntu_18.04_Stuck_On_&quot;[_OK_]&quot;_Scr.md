---
title: "Help! Ubuntu 18.04 Stuck On &quot;[ OK ]&quot; Screen"
date: 2018-11-28
forum: General Help
---

### Post by vincentreynard on 2018-11-28
Hi! I have started to use Ubuntu as my second OS (via dual boot) since 5 months ago. I use it mainly to learn terminal, some python, and many more. But today something wrong happened to my Ubuntu for some reason, here is what happened:

I cut a folder filled with some arduino and python file from my flash disk to Documents directory, everything went fine. Then, a friend of mine asked for the file I have just cut into my ubuntu, so I copied that folder to my flash disk, ejected it, and pulled out the flash disk. Here is the first strange thing that happened, my friend's PC (Windows 10) could not find the folder, so I tried to copy it again using the same method as before, but this time, I pulled and plugged my flash disk back to see if the folder is still there, but it vanished! I was sure the folder was pasted properly into my flash disk (I checked it’s contents). So ejected my flash disk and tried to find solution online (I could not find anything though). I plugged my flash disk back in, but this time my ubuntu could not detect it! I restarted my computer and logged in again, but unfortunately my Ubuntu is stuck on this screen with numerous lines started with "[ OK ]" word. I powered off my laptop and tried to boot Ubuntu again, but the same thing happened.

I felt very devastated as there are many precious files in Documents directory that I really need. Does anyone know how to fix this? Or maybe know how to retrieve the files in Documents directory?

I attached the image if you guys need a reference, by the way sorry for my bad English, hope you guys can understand

---

### Post by oldfred on 2018-11-28
What format is flash drive?
Windows does not read Linux formats.
Windows fast startup will lock all NTFS partitions with hibernation flag. So your friends system may have locked it. Linux can open it in read only mode, but hibernation flag has to be removed to write.

Forcing system down, can corrupt system, particularly if in the middle of a process. And writes to flash drives may say done, but my flash drive flickers (writing) for a minute or two more. Only safe to remove once drive is done writing. So that may have corrupted flash drive by removing too soon.

You may need fsck on your ext4 partitions and from Windows chkdsk on any NTFS partitions.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[URL="http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274"]http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274

[/URL]
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

[URL="http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274"]
[/URL]

---

