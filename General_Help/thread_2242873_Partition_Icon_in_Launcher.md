---
title: "Partition Icon in Launcher"
date: 2014-09-04
forum: General Help
---

### Post by Quarkrad on 2014-09-04
Running 12.04 Unity - I have an encrypted partition that is shown in nautilus as 27GB Encrypted.  It is not mounted on boot so when I click on the (nautilus) icon it mounts and asks me for my Passphrase, as per the attached nautilus.png.  What I would like to do is have an icon in the launcher that brings up just the window to enter the passphrase - as per attachment encrypt2.png.  I am OK putting a new icon in the launcher but unsure what command I need that could launch encrypt2.png.  Any advice appreciated.

---

### Post by Quarkrad on 2014-09-05
The partiton I need to mount, that is called 27GB Encrypted, is /dev/sda7.  I have read a few sites and tried the following (I am a newbie re terminal commands):  

dad@dadubuntu:~$ sudo mkdir mount encrypt
dad@dadubuntu:~$ /dev/sda7 /mnt/mount encrypt ext4 defaults 0 0
bash: /dev/sda7: Permission denied
dad@dadubuntu:~$ 

unfortunately this did not work.

---

### Post by Quarkrad on 2014-09-05
To clarify what I'm trying to do - if I launch **Disk Utility** I get attached disk utility.png.  I can launch the window I want by clicking on the lower right option - Unlock Volume Disk Utility.

---

### Post by deadflowr on 2014-09-05
If it's a partition, doesn't it add a disk-like icon to the launcher?
It's usually added to the bottom of the launcher.
You can lock it to launcher.
That should keep it from disappearing.
Then whenever you need to open it, it should first ask for the password/passphrase.

Ohh, you might need to set the launcher to show mounted devices.
To do so, you would need ccsm, then go to the Ubuntu Unity Plugin, and then in there, go to Experimental.
Then set the option to always or only mounted for Show Devices.

---

### Post by Quarkrad on 2014-09-05
Thank you - that did it.  I also discovered one can do the same/similar thing using MyUnity.

---

