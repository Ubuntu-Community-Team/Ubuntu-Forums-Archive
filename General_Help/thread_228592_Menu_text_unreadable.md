---
title: "Menu text unreadable"
date: 2006-08-03
forum: General Help
---

### Post by chrisccoulson on 2006-08-03
After switching my machine on and applying updates this afternoon, the menu text in some applications has now been replaced by boxes. I've attached a screenshot to show what I mean.

So far, the applications affected appear to be Adobe Reader and the Openoffice quickstart button, and also the open and save file dialog box within every application on my system.

I'm running Ubuntu Dapper on an AMD64 machine with the 2.6.15-26-amd64-generic kernel and my system is fully up-to-date.

I'm not entirely sure what could be causing this problem. At first, I thought it was just Openoffice that was affected, so I tried a reinstall of all Openoffice components from Synaptic. This had no effect, and then I realised Acrobat was also affected, along with the open and save file dialog boxes on my system

My system is virtually unusable at the moment and I'm not really sure where to go from here.

EDIT: Problem fixed by downgrading ia32-libs-gtk. See [this]("http://www.ubuntuforums.org/showthread.php?t=228179") thread

---

