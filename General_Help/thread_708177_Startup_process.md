---
title: "Startup process"
date: 2008-02-26
forum: General Help
---

### Post by dmsn on 2008-02-26
I wonder where i can see which programs startup when i boot my machine ?
If i want my shell script to start up where to put it ?
Also i want my smbmount to start.

Thanks for help.

---

### Post by ntetreau on 2008-02-26
Typical services can be enabled disabled in System > Administration > Services.  As for adding scripts, you would normally install them with executable permission in /etc/init.d/ and then soft link them in /etc/rc2.d/

In rc2.d, the scripts name start with S# where # is a number that will decide the order in which the scripts are started.  I'm not an expert with this unfortunately, so I'm usually very careful when making changes there, please be careful too!

---

### Post by dmsn on 2008-02-26
ok but if want to run this on every boot how to do that?
smbmount //192.168.0.1/ftp /mnt/ftp

---

### Post by edm1 on 2008-02-26
I think you should be doing that in fstab (/etc/fstab). A quick search found [this thread]("http://ubuntuforums.org/showthread.php?t=282008") which could contain useful info.

---

### Post by ntetreau on 2008-02-26
I think edm1 is right here, if you only want to mount a filesystem, fstab is probably the best way to do this.  I wonder how you can make sure that your network is up before trying to mount though.  If there is no way to make sure the network is up though, then a script might be a better alternative.

---

