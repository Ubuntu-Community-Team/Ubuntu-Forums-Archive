---
title: "menu.lst change itself"
date: 2007-07-23
forum: General Help
---

### Post by carlstand on 2007-07-23
> Originally Posted by ago View Post
That's the same in Ubuntu. Everything above "### END DEBIAN AUTOMAGIC KERNELS LIST" is generated. The only difference is that with wubi menu.lst is updated at each reboot and with ubuntu at each kernel upgrade. Just put your menu items after that.
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
kernel /wubi/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash nmi_watchdog=0
initrd /wubi/wubi/boot/initrd.img-2.6.20-16-generic
boot
```

why? now everytime i have to re-edit the menu.lst to make it work. and what can i do to fix it?

sorry for the bad English, i'm from China
__________________

---

### Post by Xenomorph on 2007-07-23
> **carlstand said:**
> 
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Ubuntu, karl
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash nmi_watchdog=0
initrd /wubi/wubi/boot/initrd.img-2.6.20-16-generic
boot
```

why? now everytime i have to re-edit the menu.lst to make it work. and what can i do to fix it?

sorry for the bad English, i'm from China
__________________

I don't know how or why it does it, but it changes paths for no reason for me as well.

Sometimes it shows the correct path, ie:
kernel /wubi/boot/vmlinuz-2.6.20-16-generic

Sometimes it takes off part of the location, ie:
kernel /boot/vmlinuz-2.6.20-16-generic

Sometimes it doesn't have any directory listed, and just shows:
kernel /vmlinuz-2.6.20-16-generic


I'd like to find out how and why it keeps-auto changing itself, what program does it, WHERE that program gets its information from, and I want to be able to change it - either correct where it looks, or just tell it to STOP changing the menu.lst file.

If the system boots with MENU.LST, then WHY would the OS need to keep changing it?

On every system I've used Wubi on, I end up with messed up MENU.LST files.

The system works on the first boot, then menu.lst is changed to show the wrong paths.

---

### Post by carlstand on 2007-07-23
i think it  maybe changed by /wubi/tools/wubiBSD.exe, but i cann't watch this file or edit it. maybe we have to ask the developer for a answer.
or i  have to give my virtualbox up.i need to shutdown the watchdog to use my virtualbox driver.

---

### Post by ecology2007 on 2007-07-24
You do not have to edit the menu.lst yourself anymore for a month or two.
It is updated automagically everytime ubuntu uppgrades its kernel so wubi will boot with the very last kernel version.

---

### Post by ecology2007 on 2007-07-24
The wubi/wubi/... line is of course a bug.
We ll try to find out why.

---

### Post by carlstand on 2007-07-24
can someone give me a solution to shutdown the watchdog at startup without adding a new section to the menu.lst? 
I realy want to use the virtualbox.

---

### Post by carlstand on 2007-08-11
now i can only use rc.local to make this change everytime on boot .

---

