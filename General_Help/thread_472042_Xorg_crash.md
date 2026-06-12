---
title: "Xorg crash"
date: 2007-06-12
forum: General Help
---

### Post by spynode on 2007-06-12
I was playing one game on my Ubunty system when my PC crashed and I was forced to reboot using Reset button. After that my X started to crash at the beggining right after the NVIDIA graphical logo when mouse cursor appeares. Tried several times - it always happens.

My xorg.log

```
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list
Backtrace :
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/bin/X(main+0x6bf) [0x80749af]
3: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xdc)
4: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal Server error: Caught signal 11. Server aborting
```

I think it may boucouse of some filesystem damage, and tried to reinstall X but it didn't work. Maybe I tried wrong packages. Help me out please ;)

---

### Post by Josey on 2007-06-12
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by spynode on 2007-06-12
Josey thanks for quick replay. Now I will know how to reconfigure xorg, but I managed to solve my problem by disabling usbhid module. I enabled it a while ago and totally forgot about it and it appears that after reboot that was the reason X won't start. After disabling usbhid and rebooting X started up fine again.

EDIT: Well unfortunatly problem still remains. After another reboot X crashed again, so I rebooted PC and X started again without any problems. So my system is pretty unstable right now as I dont know if my X will start normally again afetr I turn on my PC next time.

---

