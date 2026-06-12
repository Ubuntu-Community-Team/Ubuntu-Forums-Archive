---
title: "menu.lst changes lost after restart"
date: 2007-07-11
forum: General Help
---

### Post by CSMatt on 2007-07-11
I've noticed that my Wubi installation has the "failed to set xfermode" bug.  As suggested in related posts, I tried to edit menu.lst to add the "irqpoll" option.  I can read and edit menu.lst just fine with gedit, but the file appears to revert itself when it is restarted.  I tried again with superuser access and it still reverted.  I eventually had to boot into Windows and change the file with WordPad instead to get a permanent change.  Gedit saves the file just fine; I can close the file and open it again and see the changes.  It just appears that Ubuntu or GRUB is erasing them upon shutdown or reboot.  Why is this?  This never happened to me with my traditional Feisty install, so I figured Wubi might have something to do with this seeing as the boot files are symbolically linked and not in a virtual disk.

---

### Post by Toadmund on 2007-07-11
Did you save it?
Seems to me it may depend if you put the command in during the bootup, or after bootup, little fuzzy on this, maybe someone can clarify?

---

### Post by ago on 2007-07-11
You have to add any new section at the bottom, all the ones in the middle get regenerated every time

---

### Post by CSMatt on 2007-07-14
Why is that?  That isn't the case in a normal Ubuntu installation.

---

### Post by ago on 2007-07-14
That's the same in Ubuntu. Everything above "### END DEBIAN AUTOMAGIC KERNELS LIST" is generated. The only difference is that with wubi menu.lst is updated at each reboot and with ubuntu at each kernel upgrade. Just put your menu items after that.

---

### Post by carlstand on 2007-07-22
> **ago said:**
> That's the same in Ubuntu. Everything above "### END DEBIAN AUTOMAGIC KERNELS LIST" is generated. The only difference is that with wubi menu.lst is updated at each reboot and with ubuntu at each kernel upgrade. Just put your menu items after that.

hello i'm new here, and i have already made changes after "### END DEBIAN AUTOMAGIC KERNELS LIST" ,i wrote a new section like this :

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Ubuntu, karl
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash nmi_watchdog=0
initrd /wubi/boot/initrd.img-2.6.20-16-generic
boot

```
and everytime i reboot , it will be automatic added a new "/wubi" before kernel and initrd path, even when i didn't set this section as default. just like below:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Ubuntu, karl
find --set-root --ignore-floppies /wubi/boot/linux
kernel **/wubi**/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash nmi_watchdog=0
initrd **/wubi**/wubi/boot/initrd.img-2.6.20-16-generic
boot


```

why? now everytime i have to re-edit the menu.lst to make it work. and what can i do to fix it?

sorry for the bad English, i'm from China:)

---

### Post by mepuntu on 2007-08-10
I've been having the same problem, is there a fix for it yet?

---

### Post by ago on 2007-08-10
> **carlstand said:**
> hello i'm new here, and i have already made changes after "### END DEBIAN AUTOMAGIC KERNELS LIST" ,i wrote a new section like this :

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Ubuntu, karl
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash nmi_watchdog=0
initrd /wubi/boot/initrd.img-2.6.20-16-generic
boot

```
and everytime i reboot , it will be automatic added a new "/wubi" before kernel and initrd path, even when i didn't set this section as default. just like below:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Ubuntu, karl
find --set-root --ignore-floppies /wubi/boot/linux
kernel **/wubi**/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash nmi_watchdog=0
initrd **/wubi**/wubi/boot/initrd.img-2.6.20-16-generic
boot


```

why? now everytime i have to re-edit the menu.lst to make it work. and what can i do to fix it?

sorry for the bad English, i'm from China:)
Hmm not obvious, the issue is due to /etc/init.d/cpkernel, it remaps the paths starting with /boot to path starting with /wubi/boot, which works ok if the path starts with /boot to begin with, but not if it starts with /wubi/boot. You may want to use "kernel /boot" and "initrd /boot" as a replacement string

---

