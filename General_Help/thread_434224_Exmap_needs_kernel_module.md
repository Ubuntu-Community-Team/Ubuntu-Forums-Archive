---
title: "Exmap needs kernel module"
date: 2007-05-05
forum: General Help
---

### Post by afoglia on 2007-05-05
I'm trying to get exmap to run, but when I try to run it, either as a normal user, or with sudo, I get the following error:
```
Can't find file /proc/exmap: please check kernel module is loaded
Can't get system info

```

Is there a kernel module that should be installed?  I don't see any likely candidates when I searched to official repository.  There is a exmap-modules-source package.  Do I need to compile the kernel module myself?

---

### Post by lhaeh on 2007-11-19
Here is what I did:
Install the module source:
sudo apt-get install exmap-modules-source

Extract from the archive:
tar -xzf /usr/src/exmap.tar.gz

It will end up in $HOME/modules
The rest of the install instructions are here:
/usr/share/doc/exmap-modules-source/README


For me it went like this:
cd /home/lars/modules/exmap
make
~/modules/exmap$ sudo insmod kernel/exmap.ko
~/modules/exmap$ sudo insmod /home/USER/modules/exmap/exmap.ko
(replace USER with your user name)

Running gexmap should work now.

---

