---
title: "problem trying to update ubuntu 14.04 64"
date: 2014-10-23
forum: General Help
---

### Post by hunterkasy on 2014-10-23
Setting up brltty (5.0-2ubuntu3) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service brltty
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package brltty (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.11.0-19-generic
Errors were encountered while processing:
 brltty
E: Sub-process /usr/bin/dpkg returned an error code (1)
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$ 

having problem updating ubuntu, how can I make it update properly? 

thanks

---

### Post by hunterkasy on 2014-10-24
still having problems any ideas?

---

### Post by flopex on 2014-10-24
This worked for me

```
sudo apt-get install initscripts
```

---

### Post by Rahul_Raj on 2015-09-12
> **flopex said:**
> This worked for me

```
sudo apt-get install initscripts
```
This worked for me too!

---

