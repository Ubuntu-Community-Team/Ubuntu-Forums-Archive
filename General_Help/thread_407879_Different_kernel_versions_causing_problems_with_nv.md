---
title: "Different kernel versions causing problems with nvidia drivers"
date: 2007-04-12
forum: General Help
---

### Post by cdrom600 on 2007-04-12
(I'm using Ubuntu 6.10 [Edgy]).

I somehow have the packages linux-image-generic, linux-image-2.6.17-10-generic, and linux-image-2.6.17-11-generic (along with the headers for both of these versions) installed, and sets of files for both kernel versions are in my /boot directory.  Grub's menu.lst is set up to give me a choice of whether to boot 2.6.17-10 or 2.6.17-11.

My problem is that when I select and boot 2.6.17-10, the system loads properly, whereas with 2.6.17-11, the X Server crashes when it tries to start and the output shows an error related to the Nvidia driver.  I have nvidia-kernel-common, nvidia-glx, and both linux-restricted-modules-2.6.17-11-generic and linux-restricted-modules-2.6.17-10-generic installed.

I have three main questions:
- Why does the nvidia driver only work with 2.6.17-10?
- How can I make it work with both 2.6.17-10 and 2.6.17-11?
- What does the -10 or -11 after the kernel version number designate?

Thanks.

Potentially useful information:

```
$ uname -r
2.6.17-10-generic
```

```
$ cat /etc/X11/xorg.conf
[...long file; I've removed some...]
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MX1000" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
Load "dri"
Load "dbe"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Driver         "nvidia"
#next line was added
Option  "XAANoOffscreenPixmaps"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "0x0"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "0x0"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "0x0"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "0x0"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "0x0"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "0x0"
    EndSubSection
EndSection
Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

```
$ ls /boot/
abi-2.6.17-10-generic
abi-2.6.17-11-generic
config-2.6.17-10-generic
config-2.6.17-11-generic
grub/
initrd.img-2.6.17-10-generic
initrd.img-2.6.17-11-generic
memtest86+.bin
System.map-2.6.17-10-generic
System.map-2.6.17-11-generic
vmlinuz-2.6.17-10-generic
vmlinuz-2.6.17-11-generic
```

```
$ cat /boot/grub/menu.lst
[...long file; I've removed some...]
title           Ubuntu 6.10, kernel 2.6.17-11-generic (/dev/sda4)
root            (hd2,3)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu 6.10, kernel 2.6.17-11-generic (recovery mode) (/dev/sda4)
root            (hd2,3)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu 6.10, kernel 2.6.17-10-generic (/dev/sda4)
root            (hd2,3)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu 6.10, kernel 2.6.17-10-generic (recovery mode) (/dev/sda4)
root            (hd2,3)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu 6.10, memtest86+ (/dev/sda4)
root            (hd2,3)
kernel          /boot/memtest86+.bin
quiet
boot
[...]

```

---

### Post by Darkdelusions on 2007-04-12
What u can do is under the working kernal download the install script from nividia log out log back into the new kernal and reinstall the drivers. 

Then what you can do is download the [Envy Script]("http://albertomilone.com/wordpress/?p=66") so it builds a kernal module and you shouldn't have a problem agian.....

---

### Post by astoltz on 2007-04-12
You should also have a "linux-restricted-modules-generic" package installed.  That's a dummy package that will install the restricted modules (the actual Nvidia kernel module) that matches your kernel.  Sounds like you have a 2.6.17-10 version but not a 2.6.17-11 version.

---

### Post by cdrom600 on 2007-04-12
Would I do any damage to the system by removing the packages related to 2.6.17-10 and leaving the ones related to 2.6.17-11?

---

### Post by astoltz on 2007-04-12
Before you remove anything, post the output of```
dpkg -l | grep linux-restricted
```

---

### Post by cdrom600 on 2007-04-12
```
$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1                        Non-free Linux 2.6.17 modules on x86_64 generic
ii  linux-restricted-modules-2.6.17-11-generic 2.6.17.7-11.2                        Non-free Linux 2.6.17 modules on x86_64 generic
ii  linux-restricted-modules-common            2.6.17.7-11.2                        Non-free Linux 2.6.17 modules helper script
ii  linux-restricted-modules-generic           2.6.17.11                            Restricted Linux modules for generic kernels
```

also...
```
$ dpkg -l | grep linux-image
ii  linux-image-2.6.17-10-generic              2.6.17.1-10.34                       Linux kernel image for version 2.6.17 on x86/x86_64
ii  linux-image-2.6.17-11-generic              2.6.17.1-11.37                       Linux kernel image for version 2.6.17 on x86/x86_64
ii  linux-image-generic                        2.6.17.11                            Generic Linux kernel image
```
```
$ dpkg -l | grep linux-headers
ii  linux-headers-2.6.17-10                    2.6.17.1-10.34                       Header files related to Linux kernel version 2.6.17
ii  linux-headers-2.6.17-10-generic            2.6.17.1-10.34                       Linux kernel headers for version 2.6.17 on x86/x86_64
ii  linux-headers-2.6.17-11                    2.6.17.1-11.37                       Header files related to Linux kernel version 2.6.17
ii  linux-headers-2.6.17-11-generic            2.6.17.1-11.37                       Linux kernel headers for version 2.6.17 on x86/x86_64
ii  linux-headers-generic                      2.6.17.11                            Generic Linux kernel headers
```
And note the files which I posted in my first post as well.

---

### Post by astoltz on 2007-04-12
Sorry, I guess I didn't read the first post close enough - seems you already provided that info.  I'm stumped...  You could try re-installing nvidia-glx.  I'd be cautious removing any of the 2.6.17-10 stuff since that is your only working config.

You could also try Darkdelusions suggestion - the script from Nvidia is very easy.  Just remove Nvidia-glx and the restricted modules package first (don't forget to change the "nvidia" driver in xorg.conf to "nv").  Also, a small warning if you go that route.  Using a third party Nvidia driver can cause problems later on if Ubuntu updates packages that the driver depends on.

---

### Post by cdrom600 on 2007-04-12
> **astoltz said:**
> Sorry, I guess I didn't read the first post close enough - seems you already provided that info.  I'm stumped...  You could try re-installing nvidia-glx.  I'd be cautious removing any of the 2.6.17-10 stuff since that is your only working config.

You could also try Darkdelusions suggestion - the script from Nvidia is very easy.  Just remove Nvidia-glx and the restricted modules package first (don't forget to change the "nvidia" driver in xorg.conf to "nv").  Also, a small warning if you go that route.  Using a third party Nvidia driver can cause problems later on if Ubuntu updates packages that the driver depends on.

Actually, I followed Darkdelusion's suggestion and now the video works on 2.6.17-11, but not 2.6.17-10.  I had to find the right version of the driver on nvidia's site for the "kernel interface module" (or something like that) that I had installed.  It was an older one, and now I can't set the screen resolution I want.  I didn't do any of the changes you suggested in your second paragraph, though.

I have three (somewhat related) questions here:
- What are the additional (-10 or -11) numbers after the kernel version for?
- How might I have gotten two kernels installed on my system?
- What is the risk of removing the older (-10) one's packages?

Anyway, I think I have two options here:
1) Remove the old kernel packages and all the restricted modules packages (and nvidia-glx, etc.) and try to reinstall them with only one kernel installed.
2) Make the changes you suggested above and try to install the latest driver from Nvidia's site.

What risks might be involved with either of these?  Which would you recommend?
And how might I purge the Nvidia driver I've just installed from my system?

---

### Post by cdrom600 on 2007-04-13
I have made a backup of my root partition using partimage so that I can restore from whatever I do.

---

