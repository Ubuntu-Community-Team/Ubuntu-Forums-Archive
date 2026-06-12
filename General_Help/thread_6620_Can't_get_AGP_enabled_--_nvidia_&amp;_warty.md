---
title: "Can't get AGP enabled -- nvidia &amp; warty"
date: 2004-11-30
forum: General Help
---

### Post by negativ on 2004-11-30
Desktop is running Hoary, laptop is running Warty.

I was feeling a little more daring than I should have, so when I spotted [this thread](http://ubuntuforums.org/showthread.php?t=6175) I thought I'd give it a go.

Well, various problems occurred that I didn't really feel like living with, so I used synaptic to "force version" the original versions of nvidia-glx and the restricted modules package.

The problem I have now is that AGP isn't working, whereas it was before.  GLX works, but windows in X redraw PAINFULLY slowly.

dmesg says:
```
NVRM: not using NVAGP, AGPGART is loaded!!
NVRM: not using NVAGP, AGPGART is loaded!!
```

and then there's:

```
$ cat /proc/driver/nvidia/agp/status
Status:          Disabled
```

I did it on the Hoary desktop, and for completely unrelated reasons I decided to do a re-install of Warty on the laptop... and now it has the same problem.

It was working before, and it doesn't seem to be specifically related to Hoary.

I'd REALLY like to get my snappy X environment back.  It's now pretty sluggish, and window redraws are ... disappointingly slow.

---

### Post by daniels on 2004-11-30
sudo rmmod agpgart

---

### Post by negativ on 2004-11-30
```
 $ sudo rmmod agpgart
ERROR: Module agpgart is in use by via_agp
```

---

### Post by daniels on 2004-11-30
sudo rmmod via_agp
sudo rmmod agpgart
sudo modprobe nvidia

---

### Post by negativ on 2004-11-30
I edited my post with updated info, but for some reason that seems to have reverted.

Anyway, I've got that handled, but the changes don't survive reboot.  Is there any way to make it permanent so I don't have to redo that every time the system restarts?

---

### Post by negativ on 2004-11-30
anyone?

I also edited /etc/hotplug/blacklist and added:

agpgart
via_agp

yet they're still loaded at boot time.

 :confused: 
 ](*,)  ](*,)

---

### Post by daniels on 2004-12-01
[QUOTE=negativ]anyone?

I also edited /etc/hotplug/blacklist and added:

agpgart
via_agp

yet they're still loaded at boot time.[/QUOTE]Try removing them from /etc/modules.

---

### Post by negativ on 2004-12-01
They aren't in /etc/modules.   #-o

---

### Post by negativ on 2004-12-02
Well, so far I haven't found anything useful.  I guess I'll just have to do it manually all the time from now on, which sucks, but oh well.

---

### Post by diebels on 2004-12-02
[QUOTE=negativ]Well, so far I haven't found anything useful.  I guess I'll just have to do it manually all the time from now on, which sucks, but oh well.[/QUOTE]
 It's not the "right" way, but you could put the commands in /etc/init.d/bootmisc.sh

---

### Post by Bannet on 2004-12-06
I fixed mine here.
[http://www.ubuntuforums.org/showthread.php?t=6237&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=6237&page=1&pp=10)

---

### Post by nocturn on 2005-01-06
I have file a bugreport for this one:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=5242](https://bugzilla.ubuntu.com/show_bug.cgi?id=5242)

As a workaround, I moved the previously loaded agp modules to .saved files.
This works nicely (although it is un unclean fix).

---

