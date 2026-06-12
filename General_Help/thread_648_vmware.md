---
title: "vmware"
date: 2004-10-14
forum: General Help
---

### Post by nburns on 2004-10-14
Is there a way to install vmware via apt?  I don't see it in the repository.

---

### Post by randy on 2004-10-14
There isn't a package in the repository.  I can't get mine to startup after I isntall it.  I get some symbol relocation error when I install it from the .tar.gz.

---

### Post by triad169 on 2004-10-14
Packages you need from Synaptic:

GCC
G++
Linux kernel headers to match your running Kernel Image

Once those are installed.  Follow install per VMware Manual (Note all done as root):

> Use the tar installer: You may copy a tar archive to your hard disk and install
following the directions below. Or you may skip the steps for copying and
unpacking the archive and install directly from the vmware-distrib
directory on the CD.
Copy the tar archive to a directory on your hard drive -- for example, to/tmp.
cp VMware-&lt;xxx&gt;.tar.gz /tmp
Change to the directory to which you copied the file.
cd /tmp
Unpack the archive.
tar zxf VMware-&lt;xxxx&gt;.tar.gz
Change to the installation directory.
cd vmware-distrib
Run the installation program.
./vmware-install.pl


Once it is all installed it will ask you do you want to config your system for vmware.  say no.

You need to patch VMware modules to be compatable with the kernel.  To do this download:   vmware-any-any-update83.tar.gz from vmware.  

```
tar zxf vmware-any-any-update83.tar.gz
cd vmware-any-any-update83
sudo ./runme.pl
```

Follow the on screen directions.  This time you want it to config the modules though.  

Then reboot your system and you should be all set to go.  This worked for me on version :

VMware-workstation-4.5.2-8848

triad

---

### Post by nburns on 2004-10-14
Thanks for the help.. That looks like it worked.

---

