---
title: "kubuntu-desktop"
date: 2007-01-11
forum: General Help
---

### Post by drito on 2007-01-11
I have a PC which is not connected to the Internet, with Ubuntu Edgy running on it. I would like to add kubuntu-desktop. I've done it before using:

```
sudo aptitude install kubuntu-desktop
```

on Internet connected box. However, I do have both Ubuntu and Kubuntu LIVE CDs, but I don't want dual boot. Is it possible to add just kubuntu-desktop using Kubuntu CD as some kind of repo?

---

### Post by hal10000 on 2007-01-11
I guess you can. Just put in the Kubuntu cd and add this to your repositories list

---

### Post by ajgreeny on 2007-01-11
Unfortunately you need the alternative install CD to do that.  If you know someone who runs ubuntu and who is prepared to help, or you have another computer running it which is connected to the internet, use synaptic and do the usual mark for install.  Then when you click the apply icon, tick the "Download package files only" tick box.  Make a note of all the packages downloaded (there will be lots, easiest to do this by just noting the time of downloading and then sorting in the cache by date) and then copy them from /var/cache/apt/archives to a CD or other medium.

Now copy these packages to your machine not connected to the internet (to the same folder you got them from) and you will be able to use synaptic to install the packages simply by clicking install kubuntu-desktop.

Good luck.

---

### Post by drito on 2007-01-14
Thanks a lot!

---

