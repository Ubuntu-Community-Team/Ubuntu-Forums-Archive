---
title: "Ubuntu 14.04 Software Updater Not Enough Free Disk Space Error"
date: 2014-12-29
forum: General Help
---

### Post by carmen2012 on 2014-12-29
I've been trying to update by Ubuntu 14.04 install.  When I run Software Updater, I get the error message "not enough free disk space - The upgrade needs a total of 83.5M free space on disk '/ boot'.  Please free at least an additioanl 20.1M of disk space on '/boot'.  Empty your trash and remove temporary packages of former installations using 'sudo-apt-get clean'.

I've run the sudo-apt-get clean command from a terminal session but keep getting the same not enough free disk space.  I have a fairly large hard drive and other than Google Chrome, FileZilla and perhaps a very small handful of other apps, I haven't really installed anything.

Any thoughts on how I can perform the necessary update?

Thank yu

Carmen

---

### Post by whitesmith on 2014-12-29
Try this. In a terminal type:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get dist-upgrade
sudo apt-get autoclean
```
Code's a bit heavy handed, but it did the job for me. The official how-to for apt-get may be found at [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto). Cheers!

---

### Post by Holger_Gehrke on 2014-12-29
Let me guess: /boot is on a small partition of it's own.

**Ubuntu keeps all old kernels**. So if you leave it alone, boot will slowly but surely fill up with old kernel versions.

Go into Synaptic, click on Sections on the lower left, then select the section "Kernels and modules" in the list above the buttons. In the package list Kernels and related files will be shown, the ones that are installed will have a green square in front of them. Look for packages with names like 'linux-image-x.y.z-nn-generic' (x,y,z and nn are numbers). Mark all but the last (newest, highest version numbers) three or four of them for complete deletion then click on "Apply" in the Toolbar.
After its done, you should have enough space for a few kernel updates.

---

### Post by schragge on 2014-12-29
Sometimes, but unfortunately not always, old kernels may go away after
```
sudo apt-get autoremove
```
See [post=13186077]this thread[/post].

---

