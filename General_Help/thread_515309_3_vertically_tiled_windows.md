---
title: "3 vertically tiled windows"
date: 2007-08-01
forum: General Help
---

### Post by aldago on 2007-08-01
I've just installed WUBI Ubuntu 7.04 with Windows XP Pro and when open it I get 3 vertically tiled identical windows. I'm using a Dell Inspiron, 855 MHz processor and 512Mb RAM. I've had this kind of problem with Ubuntu before on this laptop and never got the issue resolved so I just took it off. I had Xandros on this laptop as a dual boot with the WinXP and no problem. I redid the laptop with a reinstallation of WinXP and left Linux off. WUBI sounded interesting so I installed it and got the same problem that I had before with Ubuntu. Does anyone know if there's a solution for this?

---

### Post by ago on 2007-08-02
Might be that the wrong video driver and/or xorg configruation was used

---

### Post by aldago on 2007-08-02
Okay. So what do I do to check it or fix it???

---

### Post by ago on 2007-08-02
You press alt+f2 to get to a console, the configuration is in /etc/X11/xorg.con, you can use nano to edit. Or you can run: sudo dpkg-reconfigure xserver-xorg

The quickest way is to look for your video card on the general forum and see if there are any issues/fixes

---

### Post by aldago on 2007-08-02
Thank you. I'll check it out.

---

