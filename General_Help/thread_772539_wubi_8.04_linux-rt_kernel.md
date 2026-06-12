---
title: "wubi 8.04 linux-rt kernel"
date: 2008-04-28
forum: General Help
---

### Post by kaiataris on 2008-04-28
I've got a weird problem with my Ubuntu install through Wubi 8.04
It could be Ubuntu, the nvidia drivers, or the linux-rt kernel but I thought I'd start here first.

The plan was to install a base Ubuntu 8.04 install through Wubi,
install the linux-rt kernel then install ubuntustudio-audio and ubuntustudio-graphics...

Installed the base Ubuntu, I had a problem with garbled graphics but dropping out to a terminal and installing nvidia-glx-new fixed that. Setup my mediabuntu repos, installed plugins, installed codecs, configured samba, setup the network printer, bluetooth worked out of the box...I was all set.

I installed linux-rt, reboot, selected the rt kernel in the grub menu. Got to the login screen, put in my username and password, but then the system hangs and freezes...gnome is unresponsive. I drop out to a terminal and I can event type my username and password cause the terminal window is spammed with "Buffer I/O error on device..." messages.

I reboot and use the generic kernel, and everything is good.
I reboot back to windows xp, everything is fine... no other harddrive or file writing errors. I try rebooting back to the
rt kernel without nvidia restricted drivers (vesa instead) and 
same problem with Buffer I/O errors.

Now, I installed Wubi/Ubuntu to my secondary partition (E:) formated as ntfs. The generic kernel seems to be fine with this, even allowing me to access C: (also ntfs) and play music, watch videos...I even burned an .iso from the ntfs partition. So maybe the linux-rt kernel doesn't have support for ntfs? 

Should I try formatting E: to Fat32? Or should I stop being lazy and unformat E: to Unallocated and just install Ubuntu studio directly and use grub as the bootloader. That way the installer can format the partitions to EXT.

-Kai

---

### Post by ago on 2008-04-28
Try commenting out the sysctl block in 

/etc/init.d/lupin-support

---

### Post by coolaj86 on 2008-04-28
```
should I stop being lazy and unformat E: to Unallocated and just install Ubuntu studio directly and use grub as the bootloader.
```
I certainly wouldn't argue against it.

I haven't used wubi myself, but from what I've read I wouldn't be surprised if wubi supplied kernel is not quite so vanilla. If you feel comfortable with it you might have success enabling the real-time options in the wubi kernel and rebuilding it from source.

But yeah, your other option there doesn't look half bad - especially if it's more a problem of laziness than technical aptitude - and would probably take less time than making a special kernel.

---

### Post by kaiataris on 2008-04-28
Yeah partially laziness, but also hoping that if I can get it working on my machine, then I can do the same Wubi install on my friend's XP machine without messing with his partitions. Then we can both experiment with doing Ubuntu Studio audio stuff like netjack and MIDI over network, without him giving up windows (he's not ready to switch)

-Kai

---

### Post by kaiataris on 2008-04-28
> **ago said:**
> Try commenting out the sysctl block in 

/etc/init.d/lupin-support

Thanks, I'll give that a try when I get home and post back.

-Kai

---

### Post by kaiataris on 2008-04-28
ok I didn't see /etc/init.d/lupin-support but there is a lupin-sysctl in there. Is that the file you mean?

---

### Post by kaiataris on 2008-04-28
ok according to this thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204133](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204133)

uninstalling lupin-support removes the lupin-sysctl entires.
I just uninstalled, so I'll reboot and try the -rt kernel and see if that does it.

-Kai

---

### Post by kaiataris on 2008-04-28
that didn't work...back on the generic kernel.

Let me read more of that bug report, because that's seems to be the problem I'm having, where / is being mounted read-only due to a conflict with the partitions being on a NTFS drive.


-Kai

---

### Post by kaiataris on 2008-04-29
alright, looks like the next thing to try is to roll realtime supporting into the generic kernel that Wubi installed...

I'm determined to get this all working with Wubi. It's such a great way to get a dual boot setup and a way for me to convert all of my windows friends with minimal hassle.

I'll post updates as I make progress.

-Kai

---

### Post by coolaj86 on 2008-05-01
I'm interested to learn how it turns out.

---

### Post by kaiataris on 2008-05-05
quick update:

I downloaded the linux-2.6.24 source and applied the preempt patch.

I'm in the process now of comparing the config-2.6.24-16-generic (wubi kernel config)
with the config.amd64 found in the kernel source (debian/binary-custom.d/rt)

I'm thinking there was something configured (or not configured) in "linux-rt" that is causing the incompatibility, so I'm going to compare the files and see if I can find it before I compile the new .debs

-Kai

---

