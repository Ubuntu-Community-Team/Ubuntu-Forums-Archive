---
title: "Virtuala Box: Need Optical Disk??"
date: 2015-10-25
forum: General Help
---

### Post by Kurt_Alan on 2015-10-25
For me, installing and running vmplayer has always been smooth as butter and Virtual Box has always been a bumpy road. 

Until now, that I've hit a brick wall with vmplayer in Ubuntu MATE 14.04 (runs great on identical machine) and have to troubleshoot error messages.

As a workaround to troubleshooting these error messages (Ha! They are locked in /tmp, another problem) I am trying again with Virtual Box.

I installed Virtual Box from the repositories, no problem. I created my virtual OS's with Win10 and Ubuntu 15.10 (WW), allotted RAM and disc space, fixed.

But when I want to start either VM, I am asked for an optical disc (not present).

What the hell? I just created a virtual hard disk. Why won't these OS's run?? Feeling real stupid . . .

---

### Post by TheFu on 2015-10-25
Did you remember to connect the installation media, usually an ISO file, to  the CDROM/DVD device inside the VM settings?

Also, be careful if you have multiple hypervisors installed on the same system, at the same time. Conflicts, you know.

---

### Post by mystics on 2015-10-25
I'm guessing this is the dialogue that appears when you first select a newly created virtual machine? In that case, you need either a physical drive (which I'm guessing you don't have?) or an ISO. At the bottom of the dialogue, you should see a couple of buttons. One of these is a drop-down menu, and the other is a folder. Click on the folder, and it should take you to the default location that Virtual Box looks for ISOs. You can, of course, look for the ISO elsewhere, but I think Virtual Box complains if you ever move it.

 If you don't have an ISO, you'll need to download one. Virtual Box doesn't provide them for you to my knowledge.

---

