---
title: "LibreOffice Writer 4.2 Slow in Ubuntu"
date: 2014-07-31
forum: General Help
---

### Post by webmanoffesto on 2014-07-31
LibreOffice Writer is running very slow. A huge part of my work is "copy web page" (with pictures), Paste Special (HTML), then make lots of revisions. I'm very happy with Ubuntu 14 but if I can't get Libre Writer working better then I have a problem. I usually save to .doc or .docx to preserve better compatibility.

Ubuntu 14,
LibreOffice: 4.2.4.2

---

### Post by mcduck on 2014-07-31
One quite easy way to speed up LibreOffice (and OpenOffice) is disabling Java.

Go to Tools->Options, and then LibreOffice->Adnavced and untick the "Use a Java runtime environment"-option. This can make a huge difference in the speed of LibreOffice applications, but more special features might require Java to be enabled (in which case you'll get a popup asking if you wish to enable it again).

If that doesn't do it, you probably won't have much options. Copying a web page is rather expensive operation, especially if there's lots of images and other content, and saving to Microsoft's formats doesn't really help either...

---

### Post by david-daking on 2015-02-01
I am also having a problem with LibreOffice running very slow. This has only happened recently, it used to be okay. It is version 4.2.7.2, Build ID: 420m0(Build:2). My Ubuntu is 14.04 with XFCE. I have increased the graphics RAM available to 256 MB and 20 MB per object, and disabled Java as described above.
Yet when I try to type things in Writer, it goes very slow and very lagging behind what I am typing, or clicking on. It is becoming quite unusable.
Is there way to fix this or should I look for an alternative word processor?

---

### Post by scouser73 on 2015-02-01
Go to /Home press CTRL & H, go to .Config and delete the libreoffice folder.

Once you have done that, restart LibreOffice and it will be as quick as the day you installed it.

You will not lose any documents by having done that, it just basically resets the application back to new.

---

### Post by danbasper on 2015-08-21
Thanks! Worked great for me.

---

