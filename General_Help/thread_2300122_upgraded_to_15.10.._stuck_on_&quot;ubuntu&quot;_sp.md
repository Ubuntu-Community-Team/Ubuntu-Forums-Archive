---
title: "upgraded to 15.10.. stuck on &quot;ubuntu&quot; splash screen"
date: 2015-10-23
forum: General Help
---

### Post by ariel8 on 2015-10-23
soo i updated to ubuntu 15.10, and now its been on the "ubuntu" splash screen for an hour..
what should i do?

---

### Post by QIII on 2015-10-23
Hello!

Would you please give us your machine's hardware specs and also let us know if you were using any proprietary drivers?

Thanks.

---

### Post by grahammechanical on 2015-10-23
There is not much that can be done in this situation. Except, power off, restart and select Advance Options for Ubuntu and then select recovery mode and at the recovery menu select Resume.

If that gets you to a working desktop then open Software & Updates>Additional Drivers tab and activate the open source video driver. Then shut down and restart. If that works then experiment with the proprietary video drivers on offer by Additional Drivers. You need to be connected to the internet and allow time for Additional Drivers to do its stuff.

Regards.

---

### Post by ariel8 on 2015-10-23
> **QIII said:**
> Hello!

Would you please give us your machine's hardware specs and also let us know if you were using any proprietary drivers?

Thanks.

ok, here is what i have:
gpu: radeon HD 6530D
cpu: amd quad-core A6-3620 APU
The Rest ill have to check for the motherboard and stuff
and i was using the drivers from amd..

---

### Post by QIII on 2015-10-23
When doing an in-place upgrade to a new release, it is best to uninstall any proprietary graphics drivers.  Not doing so is the surest way to make the upgrade a significant emotional event.

OK.  You will need to uninstall fglrx.  [It doesn't work with 15.10 at present in any case]("http://theleftcoastgeek.net/index.php/2-uncategorised/8-fglrx-in-ubuntu-15-10-wily-werewolf-is-a-no-go").

You will need to enter "Advanced Options" from the GRUB menu to do this.  If Ubuntu is your only OS, you will probably have to hold down the right Shift key immediately after POST to enter GRUB.  Just hold the button down until you see the GRUB menu.  Go to "Advanced Options".

Select (if memory serves) "Root with networking".

When you reach the prompt, you will need to mount your file system in read/write mode:

```
mount -o remount,rw /
```

Then, run

```
apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates fglrx-core fglrx-updates-core
```

For good measure, add the following back:

```
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

If you get an error to this effect "Internal Error, No file name for libgl1-mesa-dri", try

```
apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core
```

Finally, make sure that your xorg.conf won't confuse things:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Reboot and you should be back to the default open source Radeon driver.  But don't try to reinstall the fglrx driver for the time being.  

Please follow the bug link in my blog article and add yourself to the "Affects me" list.  That will turn up the heat to get a quick resolution on this.

---

### Post by ariel8 on 2015-10-23
> **QIII said:**
> When doing an in-place upgrade to a new release, it is best to uninstall any proprietary graphics drivers.  Not doing so is the surest way to make the upgrade a significant emotional event.

OK.  You will need to uninstall fglrx.  [It doesn't work with 15.10 at present in any case]("http://theleftcoastgeek.net/index.php/2-uncategorised/8-fglrx-in-ubuntu-15-10-wily-werewolf-is-a-no-go").

You will need to enter "Advanced Options" from the GRUB menu to do this.  If Ubuntu is your only OS, you will probably have to hold down the right Shift key immediately after POST to enter GRUB.  Just hold the button down until you see the GRUB menu.  Go to "Advanced Options".

Select (if memory serves) "Root with networking".

When you reach the prompt, you will need to mount your file system in read/write mode:

```
mount -o remount,rw /
```

Then, run

```
apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates fglrx-core fglrx-updates-core
```

For good measure, add the following back:

```
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

If you get an error to this effect "Internal Error, No file name for libgl1-mesa-dri", try

```
apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core
```

Finally, make sure that your xorg.conf won't confuse things:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Reboot and you should be back to the default open source Radeon driver.  But don't try to reinstall the fglrx driver for the time being.  

Please follow the bug link in my blog article and add yourself to the "Affects me" list.  That will turn up the heat to get a quick resolution on this.
ok, i did as you said and here is what i got after the reboot:
[IMG]http://i.imgur.com/BWgPn8y.jpg[/IMG]

---

### Post by ariel8 on 2015-10-23
Ok, I solved the issueby following the instructions on bashing-om's reply to my old thread: [http://ubuntuforums.org/showthread.php?t=2275478&page=3&p=13273926#post13273926](http://ubuntuforums.org/showthread.php?t=2275478&page=3&p=13273926#post13273926)
thank you all for the help, ill mark this as solved

---

