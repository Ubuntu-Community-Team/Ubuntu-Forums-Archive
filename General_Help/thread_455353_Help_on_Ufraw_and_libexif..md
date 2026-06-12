---
title: "Help on Ufraw and libexif."
date: 2007-05-26
forum: General Help
---

### Post by alelinuxbsd on 2007-05-26
I have realized a package of the last release of ufraw for the Edgy but i have one problem. I can export exif data because libexif isn't recognised.
I have install libexif-dev and libexif12 but without result. :(

This is my [package]("http://www.mediafire.com/?00jcd1gxt3x")

Someone can help me?

Thank in advance, Alessandro

---

### Post by mbradlcu on 2007-05-27
humm, are you using a x64 version? could the proggy be looking for the 32 bit lib? (yea I'm guessing here) anyway. maybe building libexif12 from source or installing the ia32-libs package may help..

---

### Post by alelinuxbsd on 2007-05-27
I'm using a x32 version (not the x64 version). 

When i start the ./configure from ufraw i obtain the data that i have posted to ufraw.txt.
===== summary ======
configure: build GIMP plug-in: yes
configure: hidden directories support (GTK>=2.6): yes
configure: EXIF support using libexif: no
configure: EXIF support using exiv2: no
configure: JPEG support: yes
configure: PNG support: yes
configure: TIFF support: no

I have install:
libexif-dev - library to parse EXIF files (development files)
libexif12 - library to parse EXIF files
libexif-gtk-dev - Library providing GTK+ widgets to display/edit EXIF tags (development files)
libexif-gtk5 - Library providing GTK+ widgets to display/edit EXIF tags
then i restart the configure of ufraw without result. :(

Some other idea?

Bye Ale

---

### Post by mbradlcu on 2007-05-27
sorry no,, maybe explicitly setting your lib path in the config options?

---

### Post by alelinuxbsd on 2007-05-27
Now i have resolved my problem.

The solution is to start:
sudo ./configure --with-libexif

When i used only ./configure the ufraw use DCRaw for  EXIF data read but it doesn't output exif data.

Now, it's ok.

Bye Alessandro :)

---

