---
title: "error starting Matlab r2007a"
date: 2007-04-30
forum: General Help
---

### Post by longbow on 2007-04-30
I've installed matlab r2007a on ubuntu 6.10. I started Matlab in a terminal, and the main mablab GUI appears normally.
However, after a while, about 5~10 seconds, mablat crashes, while there is the following error in the terminal:
[COLOR="Blue"]
Missing Charset in string to FontSet conversion.
Unable to load any usable fontset.[/COLOR]

I've already modified the fontpath in /etc/X11/xorg.conf to /usr/share/fonts/X11, but no use.

Thanks!
-----------------------updated-------------------------------------
Currently I solve this problem by start matlab using
> LC_ALL=C ./matlab

---

### Post by lbig on 2007-04-30
same thing happend to me. Still no clue.
I've switched back to R14, which works fine.

---

### Post by /error on 2007-05-01
I think i have the same error here with matlab r2007a (7.4.0) but with ubuntu feisty fawn 7.04.
It doesn't crash with normal usage, but when acessing file->preferences->fonts
and if i want to edit a graph (in other cases probably too, but they didn't occur so far...).

fontpaths are changed like longbow did. could it probably depend on utf-8 charset?
the log looks like this:
```

------------------------------------------------------------------------
       Segmentation violation detected at Tue May  1 16:48:37 2007
------------------------------------------------------------------------

Configuration:
  MATLAB Version:   7.4.0.336 (R2007a)
  Operating System: Linux 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686
  GNU C Library:    2.5 stable
  Processor ID:     x86 Family 6 Model 9 Stepping 5, GenuineIntel
  Virtual Machine:  Java 1.5.0 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode
  Default Charset:  UTF-8

Register State:
  eax = 9aa10734   ebx = a0d255a8
  ecx = 9aa0f74c   edx = 6a81e910
  esi = a0b23e84   edi = 9aa0b9b4
  ebp = a0b23e3c   esp = a0b23e14
  eip = a0cd8340   flg = 00010286

Stack Trace:
  [0] libfontmanager.so:0xa0cd8340(0xa0b23e84, 0, 10, 0xada1a690)
  [1] libfontmanager.so:0xa0cddefe(0xa0b23e84, 0x9aa0d0c8 "/libc.mo", 0x9aa0d136, 0x088becc4)
  [2] libfontmanager.so:0xa0cde286(0xa0b23ffc, 0x9aa0b8f0, 0x9aa0d0c8 "/libc.mo", 0x9aa0d136)
  [3] libfontmanager.so:0xa0ce06c2(0xa0b24144, 0x9aa0f74c, 0x9aa0b884, 110)
  [4] libfontmanager.so:0xa0cdeaca(81, 0x9aa0f74c, 0x9aa0cfa0, 0xa0b24144)
  [5] libfontmanager.so:0xa0cdefe2(0x9aa0cfa0, 0x9aa0b280, 0xa0b24290, 1)
  [6] libfontmanager.so:0xa0ccb5db(0x9aa0b280, 81, 0, 0)
  [7] libfontmanager.so:0xa0ccd33c(0x9aa0b280, 81, 0, 0)
  [8] libfontmanager.so:Java_sun_font_FileFont_getGlyphImage~(0x088fc09c, 0xa0b244b8, 0x9aa0bbf0, 0) + 288 bytes
  [9] 0xada1bb7a(0, 0xada19589, 81, 0x9aa0bbf0)
  [10] 0xada159fa(0, 0, 0, 0)
  [11] 0xada159fa(0, 0, 0x7f7fffff, 81)
  [12] 0xada15a25(110, 0xa48e7128, 0xa0b24598, 0xadc70c1c)
  [13] 0xadd24f78(110, 0xa48e6f38, 10, 0xa0b245d8)
  [14] 0xada7ecc0(110, 0xa48e6f38, 0xa0b245bc ", 0xa9fa4970)
  [15] 0xada159cf(0, 0xa48e6ed0, 0xa48e6d38, 0xa5738178)
  [16] 0xada159a4(0xa0b24624 ", 0xab2ac529, 0xa0b2465c, 0xab2bd640)
  [17] 0xada159a4(0, 0, 0, 0xa48d7d30)
  [18] 0xada15a7b(0, 0, 0, 0)
  [19] 0xada15a7b(0, 0, 0, 0)
  [20] 0xada13157(0xa0b24798, 0xa0b2495c, 10, 0xab2c8e00)
  [21] libjvm.so:0xb26a68ec(0xa0b24958, 0xa0b2483c, 0xa0b248f8, 0x088fbfe0)
  [22] libjvm.so:0xb2795378(0xb26a6730, 0xa0b24958, 0xa0b2483c, 0xa0b248f8)
  [23] libjvm.so:0xb26a671f(0xa0b24958, 0x088beca4, 0xa0b248f8, 0x088fbfe0)
  [24] libjvm.so:0xb27b65cc(0x088beca0, 0x088beca4, 0x088becac, 1)
  [25] libjvm.so:0xb27b9510(0xa4732310, 0, 0x088fbfe0, 0)
  [26] libjvm.so:JVM_NewInstanceFromConstructor~(0x088fc09c, 0xa0b24ae8, 0, 0xa9e40d48) + 237 bytes
  [27] libjava.so:Java_sun_reflect_NativeConstructorAccessorImpl_newInstance0~(0x088fc09c, 0xa0b24adc, 0xa0b24ae8, 0) + 45 bytes
  [28] 0xada1b42b(0xa9e40780, 0xada19593, 0, 0xa4732310)
  [29] 0xada159a4(0, 0, 0xa4732360, 0xa0b24b1c)
  [30] 0xada159a4(0, 0xa4732378, 0xa0b24b48, 0xa9dcb834 ")
  [31] 0xada15caa(0, 0, 0xa4732310, 0xa0b24b78)
  [32] 0xada159a4(0, 1, 0xa4732310, 0xab2c9978)
  [33] 0xada159a4(0xab2c9978, 0xa0b24bd4, 0xab29a790 ", 0xa0b24c0c)
  [34] 0xada159a4(0, 0, 0xaaffa2a0, 0)
  [35] 0xada159a4(0, 0xa4a93c10, 0, 0xab44cde0)
  [36] 0xada159a4(0xab44cde0, 0xa4a87798, 0xa0b24c7c, 0xab4e1d40)
  [37] 0xada159a4(0, 0, 0xa476a5d8, 0xa476a5e8)
  [38] 0xade1c4c0(0xa476a5e8, 0xa55a8008, 0xa0b24cf0, 0xa55a8008)
  [39] 0xadcc2fc7(0xa476a5e8, 0xa55a8008, 0xa0b24d38, 0xadb4a089)
  [40] 0xadcc272a(0, 0xffffffff, 0xa55a7908, 0xa0b24d5c)
  [41] 0xada15923(0, 0xa55a8078, 0xffffffff, 0xa55a7908)
  [42] 0xada15a7b(0xa55a8078, 0xffffffff, 0xa55a7908, 0xa0b24dc0)
  [43] 0xada15a7b(0xa55a8078, 0xa55a7908, 0xa0b24dec, 0xaa17afd1)
  [44] 0xada15a7b(0, 0, 0, 0)
  [45] 0xada13157(0xa0b24ea0, 0xa0b25054, 10, 0xaa17b068)
  [46] libjvm.so:0xb26a68ec(0xa0b25050, 0xa0b24f38, 0xa0b24fa0, 0x088fbfe0)
  [47] libjvm.so:0xb2795378(0xb26a6730, 0xa0b25050, 0xa0b24f38, 0xa0b24fa0)
  [48] libjvm.so:0xb26a6145(0xa0b25050, 0x088bec8c, 0xb2c8b430 ", 0xb2c8b4fc)
  [49] libjvm.so:0xb26a61de(0xa0b25050, 0x088bec88, 0x088bec8c, 0xb2c8b430 ")
  [50] libjvm.so:0xb2713495(0x088fbfe0, 0x088fbfe0, 0, 0)
  [51] libjvm.so:0xb27ee30d(0x088fbfe0, 1, 0, 0)
  [52] libjvm.so:0xb2795e88(0x088fbfe0, 0xa0b25470 ", 0xa0b25470 ", 0xa0b25470 ")
  [53] libpthread.so.0:0xb765831b(0xa0b25b90, 0, 0, 0)


```

---

### Post by jsgosselin on 2007-05-04
I have the same problem with Matlab R2007a with Feisty Fawn.

If you try to edit the font in a graph, for example:

Title('Ceci est un test','fontname','times new roman')

You can see that it doesn't recognize the 'special' characters like é,à,ù,ô. And when I go in the file>preference>font, Matlab is killed and it closes......

---

### Post by stee on 2007-05-04
> **/error said:**
> I think i have the same error here with matlab r2007a (7.4.0) but with ubuntu feisty fawn 7.04.
It doesn't crash with normal usage, but when acessing file->preferences->fonts
and if i want to edit a graph (in other cases probably too, but they didn't occur so far...).


Mathworks has this registered as a bug. The workaround, which I use successfully is:

sudo chmod 000 /usr/share/fonts/truetype/ttf-gujarati-fonts/
sudo chmod 000 /usr/share/fonts/truetype/ttf-bengali-fonts/

---

### Post by /error on 2007-05-05
thank you, the workaround works very well :)
have you a link to the bug report from mathworks? just for staying up to date.

cheers!

---

### Post by stee on 2007-05-05
[http://www.mathworks.com/support/bugreports/details.html?rp=357408](http://www.mathworks.com/support/bugreports/details.html?rp=357408)

---

### Post by jsgosselin on 2007-05-06
wow!

thanks!

JS

---

### Post by longbow on 2007-05-06
I also find a workaround:
at the command prompt, issue:
LC_ALL=C ./matlab

Then everything works fine.

> **stee said:**
> Mathworks has this registered as a bug. The workaround, which I use successfully is:

sudo chmod 000 /usr/share/fonts/truetype/ttf-gujarati-fonts/
sudo chmod 000 /usr/share/fonts/truetype/ttf-bengali-fonts/

---

### Post by stee on 2007-05-06
What does that do, really?
I'm curious!

---

### Post by syxbit on 2007-05-08
I am taking a matlab class
i just use it in the lab.
i'm thinking about buying the student edition for cheap
will this work in linux, or do you need a special linux version?
thanks

---

### Post by stee on 2007-05-13
I am not sure if you can use wine or something to get the windows-version to work, but there are special linux versions available (it's a dual mac/unix cd). 

You should check if your uni/college has a license you can use on your home computer though. Mine has.

---

