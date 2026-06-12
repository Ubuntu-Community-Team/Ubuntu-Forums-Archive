---
title: "Photoshop CS 2 in Edgy problems"
date: 2006-11-15
forum: General Help
---

### Post by EmperorSquirrels on 2006-11-15
I finally mounted my Windows drive and have access to all my old files (yay), but I'm stuck on this guide to install Photoshop on Ubuntu.

I followed this guide: [http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/]("http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/")

Whenever I try to run it (sudo wine photoshop) it gives me the following error which doesn't mean a thing to me:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/matt', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\photoshop.exe": Module not found

Any help is appreciated.

---

### Post by patrickthebold on 2006-11-15
Someone is going to unhelpfully tell you to just use the GIMP, so I will just get it out of the way first.

---

### Post by EmperorSquirrels on 2006-11-15
It took a friend eight years to convince me to move away from Windows. Guess how long it would take to get me off of Photoshop? I already know it almost in and out. I really don't want to try another program... Besides, I'm so close to emulating PS on Ubuntu I can taste it. I'm just at a block.

---

### Post by patrickthebold on 2006-11-15
Oh I know, I was just trying to warn you more or less.  Wine has always been voodoo for more.  I dunno why you need sudo, wine should be fine as a regular user.  try from the command line winecfg and if any of those options make any difference.  Also did you install PS with wine or are you trying to use wine on a preinstalled copy.  If its the latter I would suggest the former.

---

### Post by EmperorSquirrels on 2006-11-15
I did what that guide said - Copy the Adobe/Photoshop CS2 folder from my Windows drive and run it with Wine.

I just tried installing the setup through Wine, and got the same text:

> 
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/matt', starting in the Windows directory.
wine: cannot find '/media/windows/Documents and Settings/Matt/Desktop/Downloaded/Photoshop_CS2_tryout/Photoshop CS2/setup.exe'



---

