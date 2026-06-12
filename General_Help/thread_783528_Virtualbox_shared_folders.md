---
title: "Virtualbox shared folders"
date: 2008-05-05
forum: General Help
---

### Post by xaenyx on 2008-05-05
Ok, so I wanted to sync my Zune player, but it only works with windows.  Luckily, I had a copy of windows xp, so I installed it in virtualbox (not OSE).  Everything works great--except shared folders.  In the host os (ubuntu 8.04) I ran:

```

VBoxManage sharedfolder add "xp" -name shared -hostpath /media/main_ext

```

Which worked fine.  I then booted up my xp vm, and tried to mount the share:

```

net use x: \\vboxsvr\shared /persistent:yes

```

But I get:

```

System error 53 has occurred.

The network path was not found.

```

I also can't browse to \\vboxsvr (I thought it might be a typo and tried it with \\vboxsrv as well) in Explorer.  Any ideas?

---

### Post by qpieus on 2008-05-05
Is your installation of virtualbox a fresh installation, or one that you've apt-get updated as new versions came out? I also had trouble with shared folders not working - the windows vm could not "see" the shared folder on the host. What happened was that I had upgraded virtualbox as newer versions came out. Along the way, one of the new version implemented the shared folders feature. But the feature never worked for me. I even uninstalled and reinstalled and still no luck. Then I had the idea to uninstall, then remove the ~/.VirtualBox directory (actually, I just renamed it), then reinstall. Now shared folders started working. So there was something in the ~/.VirtualBox directory that was hosing that feature. Only when I started fresh with no ~/.VirtualBox directory and a reinstall did it work right.

Note that the ~/.VirtualBox directory contains information about your VMs (it might also contain the VM virtual hard disks, unless you keep them elsewhere). So I recommend just renaming the directory rather than deleting it, in case you need some of that info later. After reinstallation you'll need to create new VMs and have them use the existing virtual hards drives. If you have a lot of VMs, then my solution moght not be worth the hassle. For me I only had a couple VMs so it wasn't a lot of work to get them set up again.

---

### Post by xaenyx on 2008-05-15
I still haven't gotten shared folders to work ;_;

I don't seem to be able to use \\vboxdrv at all..  I tried starting it manually:

```

desktop:~$ sudo /etc/init.d/vboxvfs
Usage: /etc/init.d/vboxvfs {start|stop|restart|status}
alex@alex-desktop:~$ sudo /etc/init.d/vboxvfs start
Starting VirtualBox Additions shared folder support ...fail!
(modprobe vboxvfs failed)
desktop:~$ sudo modprobe vboxvfs
WARNING: Error inserting vboxadd (/lib/modules/2.6.24-16-generic/misc/vboxadd.ko): Operation not permitted
FATAL: Error inserting vboxvfs (/lib/modules/2.6.24-16-generic/misc/vboxvfs.ko): Operation not permitted
desktop:~$

```

---

### Post by jrusso2 on 2008-05-15
I think you need to install the virtual box additions.


[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

### Post by xaenyx on 2008-05-15
That was the first thing I did..

---

