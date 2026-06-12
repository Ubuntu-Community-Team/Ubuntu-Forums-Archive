---
title: "Installing Ubuntu Server 14 - Is this normal?"
date: 2015-01-08
forum: General Help
---

### Post by sim085 on 2015-01-08
Hello, I am installing Ubuntu 14 Server Edition. I am not sure if this is normal. From the screen after I select the keyboard layout to the screen where I insert host name there is a gap of around 15 minutes! The drive does not seem even to be doing anything during this time! Is this normal!?

---

### Post by ajgreeny on 2015-01-08
That is not normal at all.  I can install a full desktop from booting the DVD/USB to rebooting the fully installed new OS in less than 15 mins.

Did you check the md5sum of the .iso file from the hashes at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by sim085 on 2015-01-08
I am downloading Ubuntu server 14.4.1 amd64 again and trying to install again. At the moment after finishing installation PC will not boot so I guess their might be an issue with the disk I used.

> **ajgreeny said:**
> That is not normal at all.  I can install a full desktop from booting the DVD/USB to rebooting the fully installed new OS in less than 15 mins.

Did you check the md5sum of the .iso file from the hashes at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by sim085 on 2015-01-08
Did another CD, checked CD, tried to install and same thing. It stops for around 10 to 15 minutes after I set the keyboard layout. Is there a known issue with server edition. When I installed the desktop edition I did not have such issue!

> **ajgreeny said:**
> That is not normal at all.  I can install a full desktop from booting the DVD/USB to rebooting the fully installed new OS in less than 15 mins.

Did you check the md5sum of the .iso file from the hashes at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by ajgreeny on 2015-01-08
No, I'm not aware of any specific server issues.

But then, I've never installed a server version!

---

### Post by kpatz on 2015-01-08
Hit Ctrl-Alt-F4 during the time it's hanging.  It'll tell you what it's doing at that point.  I think hardware detection occurs sometime after setting keyboard layout.

Hit Ctrl-Alt-F1 to return to the installer.

---

### Post by nerdtron on 2015-01-09
Ctrl+Alt+F4 to see the debugging mode. I'm guessing it's the network time protocol trying to get the timezone.

---

