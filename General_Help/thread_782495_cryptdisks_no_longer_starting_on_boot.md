---
title: "cryptdisks no longer starting on boot"
date: 2008-05-05
forum: General Help
---

### Post by leftyfb on 2008-05-05
Ubuntu 8.04 fresh install from net install

I've created /home on a separate encrypted partition using the alternate  installer. Everything was going fine until I booted up today. For some reason dm-mod, dm-crypt, sha256 and aes modules were no longer loading at boot. As well, /dev/mapper wasn't being created. I fixed these by adding the modules to /etc/modules. Now those load fine and /dev/mapper is created, but cryptdisks isn't loading at boot and prompting me for the passphrase as it was before. I can run "sudo /etc/init.d/crypdisks start" manually after boot just fine and then mount my /home. But it won't start on it's own like it used to. 

What calls cryptdisks at boot and where might I find out why it's not starting? Neither /var/log/message, syslog, udev or dmesg seem to have anything.

I've also tried dpkg-reconfigure cryptsetup. It runs through it's process successfully but doesn't fix the problem.

---

### Post by feld on 2008-06-07
did you find an answer to this? i need a fix for this.... no output or anything. something is broken and we can't be the only two people running this.

---

### Post by leftyfb on 2008-06-07
Unfortunately, no. I actually gave up with crypt on this particular machine for other reasons. eeepc with internal 4GB usn flash drive installed. The usb device kept changing and using a persistent udev rule or by UUId wasn't working all the time. Just got annoying.

---

