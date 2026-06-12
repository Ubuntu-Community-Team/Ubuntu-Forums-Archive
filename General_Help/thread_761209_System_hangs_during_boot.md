---
title: "System hangs during boot"
date: 2008-04-21
forum: General Help
---

### Post by jjk7288 on 2008-04-21
This just started occurring, and a clean install didn't help. Was using Gutsy, then upgraded to Hardy and it still persists.

What happens is that during the loading screen, right after GRUB, the loading will freeze for quite a long time (30 seconds to a minute) when the bar is about 1/8th of the way full. Any ideas on what might cause this to appear seemingly out of the blue and to persist even after I formatted and reinstalled Ubuntu? The only thing preserved between installs was the home directory (separate partition) and several other data-storing directories.

---

### Post by sekinto on 2008-04-21
Remove "quiet" and "splash" from the Ubuntu boot section of your /boot/grub/menu.lst file, you can always add it back later. This will disable the bootsplash so you can see what it is hanging at.

---

### Post by jjk7288 on 2008-04-21
It looks like the culprit is my external hard drive. Having it unplugged during boot reduces the boot time drastically.

Several times during boot the console spit out "device descriptor read/64, error -110" and "new high speed USB device using ehci_hcd and address x"

The device apparently kept denying the address it was given for some reason: "device not accepting address x, error -110"

It did this from 7 through 10, each step taking a ridiculously long time.

My external hard drive has never done this before - any ideas how I can fix it? It's NTFS formatted, if that matters at all.

---

### Post by sekinto on 2008-04-21
Is your external hard drive in your /etc/fstab file? If it is then you should probably add the "noauto" option.

---

### Post by jjk7288 on 2008-04-21
My hard drive wasn't in /etc/fstab, but I added it by UUID and made sure to include the "noauto" option which doesn't seem to have an effect. I think the problem lies with actually registering it as a USB device. Toggling the power hasn't helped either.

Guess I'll have to leave it off or unplugged from now on.

---

