---
title: "Please help me mount a network share, I'm losing my mind!"
date: 2017-11-25
forum: General Help
---

### Post by c4naan on 2017-11-25
I'm pretty newb at linux environment and I'm trying to mount an NFS share from my NAS onto Lubuntu 14.04.1 on my [OpenHour Chameleon]("http://wiki.openhourlab.com/index.php/Open_Hour_Chameleon_SD_Card_Images")

All my searching tells me to edit my /etc/fstab file. However when I open that file it's blank and says "UNCONFIGURED FSTAB FOR BASE SYSTEM". I put the following line in there and saved it, but obviously nothing happens. 
> 
//192.168.0.5/volume1/Media /root/storage/SynologyNAS cifs username=XXXXX,password=XXXX


I tried to do the mount manually in SSH with this command

> sudo mount -t nfs 192.168.0.5:/volume1/Media /root/storage/SynologyNAS and I get the following error:

> sudo: unable to resolve host lubuntu
mount.nfs: No such device

Then I read about the gui User Mount Tool, so I installed that, and the field is pre filled (I assume it grabs the info from my empty fstab file) and I get the error:

> "mount: cant find /root/storage/SynologyNAS in /etc/fstab or /etc/mtab

What am I doing wrong (besides everything!) I have created the /storage/SynologyNAS/ folder in /root/ for the linkage. And I've had success in the past mounting the NAS folder into LibreELEC with an autostart.sh file. but I don't know where to put that here.

could someone help me please?:confused: :(

---

### Post by c4naan on 2017-11-29
a user on reddit helped me. I was unable to use sudo command due to an error in the /etc/hosts file. once I fixed that, I was able to use sudo commands. Installed cifs-utils and then was able to mount the share. 
full breakdown here - [http://forum.openhourlab.com/showthread.php?tid=1323](http://forum.openhourlab.com/showthread.php?tid=1323)

---

