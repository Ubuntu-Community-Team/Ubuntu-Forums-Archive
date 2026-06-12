---
title: "Skype 4.2 installs but doesn't run on 13.04"
date: 2013-05-27
forum: General Help
---

### Post by rhardie on 2013-05-27
I was running Skype and it worked OK up until an Ubuntu update around the middle of May 2013.  I've not been able to get Skype 4.1 or 4.2 to run after installation.  I have attempted to do an installation from the software center and also the Skype web site with the same results.

The Skype icon appears in the software search bar but when I click on it, nothing happens.

I did the "sudo dpkg --add -architecuture i386" then the "sudo apt-get update" and reinstalled Skype with the same results of Skype won't run.

I've uninstalled and reinstalled Skype and rebooted.

MSI laptop
Pentium Dual core
3GB RAM
80 GB free hard drive space
nVIDIA GeForce 820M G
Ubuntu 13.04 64 bit with latest updates

Any Ideas appreciated.

---

### Post by btindie on 2013-05-28
You could try using ldd to see if there's any libraries missing that it requires

```
user@localhost:~$ ldd /usr/bin/skype | grep not\ found
    libXv.so.1 => not found
    libXss.so.1 => not found
    libQtDBus.so.4 => not found
    libQtWebKit.so.4 => not found
    libQtXml.so.4 => not found
    libQtGui.so.4 => not found
    libQtNetwork.so.4 => not found
    libQtCore.so.4 => not found
```

They'll be the 32bit versions that it's after.

---

### Post by rhardie on 2013-05-29
Yup, you were right.

rocky@rocky-A6000:~$ ldd /usr/bin/skype | grep not\ found
	libGL.so.1 => not found
	libGL.so.1 => not found

I suppose that I need to find a way to get these loaded.  What command would I need for this?

Thanks in advance.

---

### Post by Jovanontherun on 2013-05-31
I've described my problem with HP laptop, probook 4540s, intel hd 3 or 4000, 4gb, etc.:
[http://ubuntuforums.org/showthread.php?t=2145229&page=6&highlight=skype](http://ubuntuforums.org/showthread.php?t=2145229&page=6&highlight=skype)
I wonder if I can resolve skype somehow?

---

### Post by Jovanontherun on 2013-05-31
@rhardie
please check what I've done so far, nothing:

[http://ubuntuforums.org/showthread.php?t=2145229&page=6&highlight=skype](http://ubuntuforums.org/showthread.php?t=2145229&page=6&highlight=skype)

---

