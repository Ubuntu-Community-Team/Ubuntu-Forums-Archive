---
title: "[SOLVED] Adding Ubuntu to GRUB"
date: 2008-07-10
forum: General Help
---

### Post by awesty on 2008-07-10
I am was dual-booting ubuntu hardy and XP. I thought I would try out Arch Linux but I was having trouble setting up my connection.

I want to go back to ubuntu but since Arch installed GRUB I can only choose to boot to either Arch or XP.

Is there a way I can reinstall ubuntu's GRUB without installing ubuntu again? I am planning on removing arch so editing arch's GRUB isn't really an option.

Sorry if this is a stupid question or if this doesn't make any sense but I am pretty new to ubuntu.

---

### Post by Elfy on 2008-07-10
You can use the livecd to reinstall grub, that should work for you - if not try supergrub - info on same page.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by carcdrcdr on 2008-07-10
Makes sense to to me ;)

Now lets get started:

Fire up your linux install that you can get to via grub and bring up your fave text editor(vi) and edit this file (as root): /boot/grub/menu.lst


**PLEASE NOTE:**  You MUST change what I typed below to match your configuration!

Here is a sample one (if you know how to alter it go ahead), at the bottom of this file add this:
```

title    Ubuntu, kernel 2.6.20-16-generic
root     (hd0,4)
kernel      /boot/vmlinuz-2.6.20-16-generic root=UUID=3d8473cb-a3b6-4973-9a51-cdaee9fa13ba ro
initrd      /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

And if you want "recovery mode" add:

```

title    Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root     (hd0,4)
kernel      /boot/vmlinuz-2.6.20-16-generic root=UUID=3d8473cb-a3b6-4973-9a51-cdaee9fa13ba ro single
initrd      /boot/initrd.img-2.6.20-16-generic

```

I can tell you what to change the settings to if you post the out put from these commands: (from your Arch Linux side)
```
sudo fdisk -l
```

```
cat /etc/fstabs
```

---

### Post by carcdrcdr on 2008-07-10
> You can use the livecd to reinstall grub, that should work for you - if not try supergrub - info on same page.

True, but then he will need to add Arch Linux into grub still...

---

### Post by Elfy on 2008-07-10
The OP says - 
> I am planning on removing arch so editing arch's GRUB isn't really an option.

so it's quite pointless adding ubuntu to the arch grub :) 

Just reinstall you're buntu grub and you should be ok. Might be worth running the livecd and mounting the booting ubuntu partition, navigate to your /boot/grub folder and copying the original menu.lst so you know what the new one needs.

---

### Post by awesty on 2008-07-10
Thanks, worked perfectly. :)

---

