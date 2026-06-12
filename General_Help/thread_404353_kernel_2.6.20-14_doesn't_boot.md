---
title: "kernel 2.6.20-14 doesn't boot"
date: 2007-04-08
forum: General Help
---

### Post by emuman on 2007-04-08
2.6.20-13 works fine. Has anyone the same problem?

---

### Post by xopher on 2007-04-08
Did you file a bug-report on launchpad.net already? If not - do so :)

I haven't tried myself, I'm not home at the moment and I don't want to remotely reboot my box  'cause - what if you're right? ;)

Oh, and does it panic or what do you mean by it doesn't boot?

---

### Post by lpmurder on 2007-04-08
I haven't encounter such problem. current kernel is 2.6.20.6 under the version of 6.10.

---

### Post by xopher on 2007-04-08
If I'm not REALLY lost, I think we're talking about the official ubuntu-shipped kernel for Feisty, not for Edgy..

---

### Post by trexjack on 2007-04-09
Same here.  Running Feisty - 2.6.20-14 won't boot - eventually kicks out to a busybox session.  2.6.20-13 works fine.

---

### Post by BrokenBrick on 2007-04-11
Same here.  I rebooted after the latest update and got a kernel panic message.  Although strangely I almost booted up on the first try but x crashed because the new kernel did not have the nvidia driver module for some reason.  But anyways, .14 and Feisty do not seem to get along.

---

### Post by pastrand on 2007-04-13
Same thing here!
Will try to back the updates to get it working again.
Any tips on how to back the kernel update? Is it enough to link vmlinuz and initrd.img to the older kernel?

/Per

---

### Post by ghidi on 2007-04-13
same here.. how can I go back to 2.6.20-13 ? it's not in Grub list anymore...

---

### Post by pastrand on 2007-04-13
Hm... Seems like the initrd.img-2.6.20-14-generic didn't work after the update.
I managed to change back to the initrd.img-2.6.20-14-generic.bak using the live CD to boot and mount the hard drive and making the changes from there.

No clue what went wrong with the initrd though...

/Per

---

### Post by emuman on 2007-04-14
I've tried it today with the latest 2.6.20-14. It boots until the point after detecting the usb devices. If I detach the usb devices the last driver loaded is the cdrom driver. Don't know what would be the next driver to load though.

---

### Post by nbound on 2007-04-14
Upgrading to 2.6.20-15 should fix most of your probs, unfortunately for me i get kicked to busybox, at least it wasnt saying my CPU was borked like it was in -14 though! :P

---

### Post by emuman on 2007-04-14
I found a solution. It has nothing to do with 2.6.20-14 or 2.6.20-15. They changed the ide driver, no more hd*-devices!
I installed linux on /dev/hda6, this is what I had to change:

1. Change your /usr/src/linux link to /usr/src/linux-headers-2.6.20-14-generic
2. Change /dev/hda? to /dev/sda? in /etc/fstab.
3. Change /dev/hda? to /dev/sda? in /boot/grub/menu.lst in the kernel parameter.
4. Run sudo grub-install --recheck
5. Run sudo grun-install /dev/sda
6. Reboot, recompile the nvidia driver and enjoy!

---

### Post by emuman on 2007-04-14
The bad thing is, cdrom autodetection doesn't work in kde anymore.

---

### Post by emuman on 2007-04-28
The funny thing is, 
with the new final version of 2.6.20-15 I had to change it the other way around. In the fstab I had to address the hda devices, not the sda.

---

