---
title: "Setting mount options (async) for hotplugged usb-storage device?"
date: 2004-11-10
forum: General Help
---

### Post by jcspray on 2004-11-10
I'm using a usb mass storage device which is correctly detected and mounted.  The problem is that this is a rather slow device, and it's getting mounted in "sync" mode.  To make it easier to work with, I prefer to use it in "async" mode.  I can accomplish this after it has been automatically mounted using "mount -o remount,async /dev/sda1".  The question:  how can I make it be mounted automatically in async mode?

---

### Post by p00p on 2004-11-12
I am wondering something very similar.  In order to extend my thumbdrive's lifetime, I would like to set the noatime option on it but I also do not know how.  Anybody got any suggestions?

---

### Post by ubik on 2004-11-13
setting these options in fstab???

Since you both don't tell if you try that, that's the only suggestion i've got!!

---

### Post by jcspray on 2004-11-13
There's no entry in fstab, since these devices are automatically detected and mounted when connected.

If I create a line such as "/dev/sda1 /media/sda1 vfat user,async" in fstab, then the device is not automounted at all.

---

### Post by ynef on 2004-11-13
The program that does the actual mounting, if you're running gnome, is the gnome-volume-manager. It calls pmount, which according to its manpage mounts the device with the following flags:
> The    device    will    be   mounted   with   the   following   flags: sync,atime,nodev,exec,noauto,nosuid,user,rw
So, unless you recompile the program with your added option of async, you're out of luck. You could always disable the automounting by running gnome-volume-properties and then adding a line in your fstab about the drive so you can manually mount it.

---

### Post by duff on 2004-11-13
[QUOTE=ynef]So, unless you recompile the program with your added option of async, you're out of luck.[/QUOTE]

I can see a lot of advanced users wanting an option like this.  Maybe a request should be passed on to the g-v-m devs for a gconf key in /desktop/gnome/volume_manager for enabling/disabling sync.

---

### Post by ynef on 2004-11-13
[QUOTE=duff]I can see a lot of advanced users wanting an option like this.  Maybe a request should be passed on to the g-v-m devs for a gconf key in /desktop/gnome/volume_manager for enabling/disabling sync.[/QUOTE]
 Well, since it calls the pmount program, maybe the request should be sent to the developer for that instead.

Weird how there is no configuration file for the program, after all, this IS *NIX -- things are supposed to be easily configurable.

---

### Post by jcspray on 2004-11-14
I've emailed the pmount writer about this, will update this thread upon a response.

---

### Post by TravisNewman on 2004-11-14
Couldn't you make an entry in the fstab similar to cdrom drives so that it's only mounted when the media is insterted? I don't know if it works differently since the drive and the media are insterted at the same time, and I don't have a usb drive to try it out, but it's worth a shot.

---

### Post by jcspray on 2004-11-14
panickedthumb: yes, that worked once I created the mount point.  Thanks for the suggestion.

---

### Post by TravisNewman on 2004-11-14
Yay! Glad you got it working. It was a hunch, but it worked

---

### Post by jcspray on 2004-11-14
Just got a reply from Martin Pitt, the pmount man.

> Indeed I'm currently at tackling this problem. There is already a bug
about it [1]. pmount version 0.3 got the -a/--async option which
mounts the device in write back mode, which makes them an order of
magnitude faster.

Integration into the Utopia framework is still missing, though. But if
people allow me (i. e. if they calm down with finding security holes
in Warty :-) ), I should finish this integration by the end of the
week.

The default will be to mount devices async which are bigger than 2 GB.
So USB memory sticks will still have the slow, but safe sync mode (so
you can just rip them out), but external USB hard drives behave sane.

[1] [https://bugzilla.ubuntulinux.org/show_bug.cgi?id=2386](https://bugzilla.ubuntulinux.org/show_bug.cgi?id=2386)



So it looks like this issue is getting proper attention.

---

