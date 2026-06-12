---
title: "Drive reseting properties on reboot"
date: 2007-01-20
forum: General Help
---

### Post by scorpionmonkey on 2007-01-20
I have a 4GB drive i installed ubuntu on, and later installed a 60 gb drive i wanted to use for extra storage. If I'm able to get access to it using the Disks dialog box (ive named it /storage), and freely copy and move files onto that drive. 

The problem comes when i try to reboot, the permissions or settings for that drive reset and then i have to manually re-add the drive again. Any idea whats going on? I'm using ubuntu 6.07.

---

### Post by cracker on 2007-01-20
I'm not sure how the Disks applet works, but you should check to see if it's in your fstab. Run this in a terminal and post the output:

sudo cat /etc/fstab

---

### Post by scorpionmonkey on 2007-01-21
looks like it only temporarily mounts the drive.... i added the drive to the fstab file and it works now.. thanks!

---

### Post by rianquinn on 2007-01-21
I had the same problem with Ubuntu. I noticed most of the settings that are done using the GUI don't actually work or are temporary. I eventually switched to Kubuntu which seems to work better except for Wireless configurations and Samba (which simply needs a complete overhaul). 

I would do things  using the terminal if your using Ubuntu

---

