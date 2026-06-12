---
title: "Uninstall Feisty"
date: 2007-03-08
forum: General Help
---

### Post by Knewguy on 2007-03-08
Recently, I installed Feisty 5 to check it out (because some here say to has been working really well then).

Presently, I notice it is creating problems with me streaming (Sirius) music through my Firefox browser and a few other issues.

Is there a way to uninstall Feisty and reinstall Edgy?

Thanks for the help.

---

### Post by etank on 2007-03-08
Did you do an upgrade or a fresh install? You may be able to edit the /etc/apt/sources.list file and replace feisty with edgy. I am not sure though if that would work.

I would also suggest submitting a bug report on the problem that you are having.

The easiest thing to do (unless you have a lot of time invested in it) is to do a fresh install of Edgy on the machine.

---

### Post by Knewguy on 2007-03-08
I did an upgrade with an Alternate Feisty CD.

I'd hate to do a fresh, reinstall of Edgy...because I'd lose all my settings/programs I have.

Also, presently I have 148 updates waiting in the Update Manager and I don't think they would help with the issues I'm having.

---

### Post by Cobikegeek on 2007-03-08
If you did a new install of feisty in the partition you previously used for edgy then you are facing a fresh install of edgy.

This tip won't help you now, but for those of us that like to play around and try different linux flavors a real timesaver is to obtain/download a good live cd recovery disk like Knoppix and use the partimage app to create an image file of your working linux install(s) before installing a new version of linux.  (on Knoppix partimage runs from the command line, using sudo partimage).  Partimage allows for compression and lets you set a maximum file size so you can span your image across multiple files to later burn them to cd's if need be.  Personally, I just set the destination file for my images to another partition and restore from there.

Then if you don't like or have problems with your new flavor of linux, just restore your last version from the image file to the partition you want to replace.  You need to run partimage from a live cd so the partition you are imaging isn't mounted.  It usually only takes 10 minutes or so to image a linux root partition and you'll have all your installed apps, settings and updates if you need to restore.  

for more info see: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Knewguy on 2007-03-09
I fixed my problem...no need to uninstall Feisty (...I'm still new to using Linux/Ubuntu)

I reinstalled codecs and the Firefox plug-in called MediaPlayerConnectivity (also, set VLC as the default player). Now, I have steaming audio from Sirius.

**Can anyone tell me how to get the song and artist info. from the streaming data?**

Thanks.

---

