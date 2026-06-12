---
title: "Missing graphics libraries in ia32-libs?"
date: 2014-07-31
forum: General Help
---

### Post by kleinempfaenger on 2014-07-31
Hi,
I posted the following question on Askubuntu, about the filebrowser contained in DraftSight, which is a drafting program similar to ACad. 

[http://askubuntu.com/questions/504834/strange-file-browser-how-to-configure](http://askubuntu.com/questions/504834/strange-file-browser-how-to-configure)

Related to that question:
Happens, that I installed this 32-bit-program on two different computers with Trusty Tahr 64-bit, and the desktop appearance is different, although I installed the same package with gdebi. It seems to be a different theme, one looks similar to Windows 95 (horrible). As I know the program very well, I can confirm that from the inside there is no way to select different flavours. During installation I had some problems with ia32-libs, which were installed on the first computer (from Raring repositories). But I could not install them on the second computer, which instead has the following 32-bit-libraries:

[COLOR=#5C5C5C][FONT=Arial]sudo apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386 libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 libxrender1:i386 libx11-6:i386 libfontconfig1:i386 lsb-core

Now, my question is, which library is responsible for the windows rendering, and if I can still get and install it. As there are also some other problems with graphics (program crash when inserting jpeg-images), I need to understand how this works.

Thanks and greetings, kl [/FONT][/COLOR]

---

