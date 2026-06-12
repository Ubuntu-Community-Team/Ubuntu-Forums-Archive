---
title: "Screen resolution stuck at 640x480"
date: 2008-05-26
forum: General Help
---

### Post by Istonian on 2008-05-26
Ok, so I started my computer this morning and it was at 640x480. My resolution is supposed to be at 1440x900. So I reinstall ubuntu because I needed to do it soon anyway. It was still at 640x480. I tried Mandriva and the resolution was fine. How do I change this?

---

### Post by strabes on 2008-05-26
What video card do you have? What drivers are you using? Please paste the output of this command in a terminal (Applications > Accessories > Terminal):```
lspci | grep vga -i
```

---

### Post by geezerone on 2008-05-26
I have same problem on the login window. After the auto login runs the screen res is back to 1280x960??

```
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
```

---

### Post by Istonian on 2008-05-26
```
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
```

---

### Post by Istonian on 2008-05-26
ummmmmm.......bump

---

### Post by kmslinux on 2008-05-26
You could try going to System > Preferences > Screen Resolution.  If that doesn't work, try downloading the driver for your graphics card from the nVidia website and setting Screen Resolution again.

---

### Post by Istonian on 2008-05-26
Tried both of them. Still doesn't work.

---

### Post by Dave Otter on 2008-05-26
alt + F2 >>sudo displayconfig-gtk
click on Model then chose your screan model >> ok

---

### Post by Istonian on 2008-05-26
Thank you very much for your help.

---

### Post by Istonian on 2008-05-30
New problem. displayconfig worked, but it made my fonts look like crap. Any ideas on how to get them to normal.

---

### Post by Istonian on 2008-05-30
bump....fonts.....really....bad....

---

### Post by alguin2 on 2008-05-30
Does System->Preferences->Appearance  
- Go to Fonts tab
- Does setting Rendering to "Best Shapes" help?

Also, if your video card supports exactly 1440x900, your display should be crisp.  

The other problem could be the monitor.  The HANNS-G JW199D (and its ilk) is best at displaying 1440x900, and has trouble displaying any other resolution.  The effect is crappy fonts, and screen scaling.

---

### Post by Istonian on 2008-05-30
The video card is well capable and the monitors native resolution is 1440x900. Everything was fine and then I started my computer a couple of days ago and the resolution was at 640x480. Not even reinstalling fixed the resolution. 

Best shapes did not help.

---

### Post by Istonian on 2008-05-31
bump

---

### Post by Istonian on 2008-05-31
bump

---

