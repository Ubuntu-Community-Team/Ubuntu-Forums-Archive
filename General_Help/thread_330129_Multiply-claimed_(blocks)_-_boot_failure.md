---
title: "Multiply-claimed (blocks) - boot failure"
date: 2007-01-02
forum: General Help
---

### Post by Double_Supercool on 2007-01-02
Guys, I have recently run into a file system/boot error using Ubuntu Edgy.

Basically, while copying across a string of .tga files from a Windows drive to my linux drive (on XP) my computer crashed with a serious error.

This resulted in 5 .tga files acting very strangely (can't delete through windows, can't open etc).

Upon trying to reboot into linux I get the following message:

**/dev/hda3 contains a file system with errors, check forced**

fsck then runs and stops at 70% with the message:

**Duplicate or bad block in use!**

**/dev/hda3 contains a file system with errors, check forced**

fsck then runs and stops at 70%

Duplicate or bad block in use!

When I restart in safe made I get the following message:

[B]Multiply-claimed (blocks) in node 14073861:2814302
Multiply-claimed (blocks) in node 14073862:2814311
Multiply-claimed (blocks) in node 14073865:2814338
Multiply-claimed (blocks) in node 14073866:2814347
Multiply-claimed (blocks) in node 14073868:2814312

Unexpected inconsistency

5 multiply-claimed blocks[/B]

**/var/log/fsck/checkfs**

Then, the system attempts to start maintenance shell, however this acts VERY weirdly (sporadic keyboard input, not executing basic commands like listing etc)

I know exactly where these dud files are and which ones are dud, but I can't get to them!

Is there anyway to avoid fsck and get root from the boot loader so I can get to the files and delete them?  Keep in mind that I am very much a linux noobzorr!!11!1

As a last resort, how about a reformat?  I haven't really done that much work on ubuntu since installing, so it wouldn't be particularly painful and I have all my .tga's on my Win drives as well.  I would probably roll back to 6.06 for stability.

Sorry for not being able to provide the logs, but I don't know how to get 'em!

Thanks for any input

ETA: how do you run fsck from the boot loader onwards?  Looking at another thread there might be a solution in terms of running fscheck manually and mounting/unmounting drives, however, from the maintenace shell (which was acting strangely) I couldn't get it running.

---

### Post by Double_Supercool on 2007-01-02
Sounds like a reformat and installing 6.06 is what I will be doing tonight :(

---

