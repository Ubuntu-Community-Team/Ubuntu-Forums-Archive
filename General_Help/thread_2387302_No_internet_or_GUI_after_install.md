---
title: "No internet or GUI after install"
date: 2018-03-17
forum: General Help
---

### Post by nejcsterle on 2018-03-17
Hello Ubuntu users!

I am returning ubuntu user, i've been using ubuntu for quite a lot of time. I switched to windows a couple of years ago because of my work needs. Hovewer, I installed Ubuntu 16.04 LTS on my USB drive (full OS on usb, NOT live USB). I used Ubuntu mini ISO, version 16.04 LTS. I've had no problems during installation through virtualbox on USB. I am able to get pass encryption screen and login normally. Hovewer, during installation I chose Dekstop version (i suppose it installed DE as well), but after I boot to OS, there's no GUI or Internet. I've tried setting up wireless manually but all without success. ifconfig shows 3 devices (ethernet, lo and another ethernet, which is supposed to be wlan), but I cant set them up. I've even tried tethering internet via iPhone's USB connection but DHCP command is not working. Does any of you have any idea how I might fix this?

Many thanks in advance,
Nejc

---

### Post by nejcsterle on 2018-03-17
Oh, and I forgot to mention that my Kernel version is 4.4

---

### Post by elephe on 2018-03-17
Does 'startx' do anything? what is in your ~/.xinitrc file?

---

### Post by cruzer001 on 2018-03-17
The server.iso can be used just like the mini.iso (using the F4 option to install a minimal system and later in the install process to manually install packages) and will attempt to auto detect/install your network.  Plus it can be used on uEFI systems; the mini.iso cannot.

It is also not necessary to create a USB for installation with any .iso.  Place the .iso in the host and point the virtualbox installer at it.

And do you have your network correctly set in virtualbox settings manager?

There has also been problems with vBox and the newer ubuntu kernels.  I recommend using the latest vBox version from their site instead of the one provided by ubuntu software sources.

And startx/.xinitrc are not part of the default install.

---

### Post by nejcsterle on 2018-03-17
i think we have a misundrstanding here. i only used vbox to install the system on usb, but i boot OS from usb as a hard drive

---

### Post by elephe on 2018-03-17
So manually configure network, install xorg, install de, and work from there?

---

### Post by cruzer001 on 2018-03-17
If your installing the DE then xorg will be installed for you.  Need to know more about your system.

Can you post the output of
```
inxi -F
```

Ctrl + Alt + F1 may get you to terminal.

---

