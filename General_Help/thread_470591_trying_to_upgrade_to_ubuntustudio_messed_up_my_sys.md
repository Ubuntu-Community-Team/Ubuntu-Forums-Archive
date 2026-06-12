---
title: "trying to upgrade to ubuntustudio messed up my system"
date: 2007-06-11
forum: General Help
---

### Post by sg_2342 on 2007-06-11
Hello there,

this is some really strange problem: I am using a 2 systems installation on my pc: on hda1 I use debian linux (Etch), on hda2 I use Ubuntu 7.04, which I intend to upgrade to Ubuntustudio. Since I have installed debian first and Ubuntu second (it was released in that order :D), Ubuntu has taken the GRUB boot manager to hda2 without asking me (I used the standard live-cd installer, unfortunately...). So, after adding the ubuntustudio repo's to /etc/apt/sources.list and installing these metapackages, the Ubuntu system doesn't boot into X-Window-System any more since the lowlatency-kernel does not load the nvidia module, which i used in ubuntu before (i think I could fix that with another apt-get command to reinstall these modules). 
But somehow this action has also affected my debian installation on hda1: This one still works, but while booting, it offers me a root console (or Ctrl-D to override) - so something seems to be "broken", but I haven't figured out what. I think it may have something to do with GRUB being loaded from hda2 (which isn't mounted in the debian system, I don't have it written in the /etc/fstab file), but I am not sure. Since I don't have much linux/unix experience, I also do not want to do anything which could kill my system so much that I cannot restore it with my poor state of knowledge..
I would be glad about any suggestion that might help me solve this problem.
My idea is to reinstall the grub manager on hda1 and put it back into the boot sector (so debian should hopefully work perfectly again) and then install ubuntu server on a "wiped" hda2 (since I didn't use the ubuntu-install very much yet and /home is located on another partition anyways, I wouldn't lose anything) and then upgrade it to -studio. But I would like to know how to prevent the ubuntu installer from rewriting the boot sector to its own boot manager, and: What is it, that in the /boot/grub/menu.lst file the partitions of Ubuntu are designated "UUID=" + a long chain of numbers&letters&dashes, instead of /dev/hda2 or something like that? Is it possible to change this back to how it was, since I like human-readable better..?

Thanks for any answers!

sg

---

### Post by michaelzap on 2007-06-14
Try loading the generic kernel instead. You can also type e to edit the grub commands if you find that grub is trying to load the system from the wrong drive or partition. I just made the mistake of trying out Ubuntu Studio as well, and the same thing happened to me (I also have an nVidia card). I was able to log back in normally once I chose the right partition using the generic kernel. I also had a helluva time removing most of what was installed by Ubuntu Studio (still not sure I'm finished). I even lost my cool Feisty sounds in the process!

---

### Post by sg_2342 on 2007-06-14
GRUB loads the right systems from the right partitions, but GRUB itself is loaded from the wrong partition. Also, it is a real pain in my neck that in the menu.lst file the ubuntu-rootpartition ist named "UUID=" and a long string of numbers and letters, i would like to change that back into the easy human-readable "/dev/hda1" etc.!

I still plan on using ubuntustudio, but does it run with the generic kernel at all? Or can I install an nVidia module into the lowlatency-kernel?

Anyway the fact that you lost your sounds was merely a user-mistake, you could have put them into your $home-dir and have this on another partition of your hard drive than the system itself is located.

Thanks anyway,

sg

---

### Post by Stinger on 2007-06-14
> **sg_2342 said:**
>  Or can I install an nVidia module into the lowlatency-kernel?
sg

Nvidia driver works for me using the lowlatency-kernel , I installed the restricted modules packages for the lowlatency-kernel.

This should do the trick.

Boot on the generic kernel and do this in a terminal

```
sudo apt-get install linux-restricted-modules-lowlatency linux-restricted-modules-2.6.20-16-lowlatency
```

and reboot into your lowlatency kernel (should be default)
this would bring you the newest restricted-modules matching your kernel.

Hope it helps.

---

### Post by dedhandi on 2007-06-27
I upgraded to ubuntu studio with no problems on my laptop but unfortunately with the same low-latency problems on my desktop. I've just tried to upgrade using the restricted modules packages but apparently mine are all the latest ones.

sudo apt-get install linux-restricted-modules-lowlatency linux-restricted-modules-2.6.20-16-lowlatency
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-lowlatency is already the newest version.
linux-restricted-modules-2.6.20-16-lowlatency is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

---

### Post by raintheory on 2007-06-28
I'm running into the same problem.

My restricted modules are up to date as well.

...

---

### Post by BreakYourTV on 2007-06-30
idem for me, restricted module are installed but I can't use 'nvidia' driver

---

### Post by raintheory on 2007-07-03
recent updates seem to have resolved this issue, at least on my system.

---

