---
title: "Virtualbox- Windows 7 don't start up after upgrade"
date: 2014-10-25
forum: General Help
---

### Post by innominate2 on 2014-10-25
Hello!
After upgrade to ubuntu 14.10, one of the virtual OS (Windows 7 32-bit) didn't start.
To be in consideration, the last time I was using it before the upgrade", I chose "Save the machine state".
Thanks in advance

---

### Post by stevedude on 2014-10-26
Same issue here. Did you get any error windows?

I did, and it tells you to recompile virtualbox with the latest linux kernal by typing this in terminal: 
sudo /etc/init.d/vboxdrv setup

I also got a warning about reinstalling DKMS so do this:
sudo apt-get install dkms

Lastly, and admittedly I don't know enough about this, but I read somewhere that Ubuntu Utopic is not including "system.d" which is a service that init.d runs from in the
prior command, so that may not work. So... someone else will have to step in here with the system.d issue (if that is a culprit) because I would like to know also.

---

