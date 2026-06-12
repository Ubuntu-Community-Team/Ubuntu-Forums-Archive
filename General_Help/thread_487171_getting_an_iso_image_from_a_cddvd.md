---
title: "getting an iso image from a cd/dvd"
date: 2007-06-28
forum: General Help
---

### Post by raddellee on 2007-06-28
Hello, i am wondering ow to get an iso image from a cd/dvd to the computer, so that i can put it on anther cd/dvd, for example, i have a ubuntu disk that i wish to copy how is this done, help will be appreciated. \\:D/ raddellee

---

### Post by smoker on 2007-06-28
hi, i'm not sure exactly what you mean - if you mean how do you create an iso image from a cd, and subsequently copy that iso image to another cd - then insert the cd, when it appears on the desktop, right click, and select copy disk, then choose 'iso image' from the dropdown menu. once copied to your desktop (or desired folder), you can then copy to another disk, either as an iso, or you can burn to a cd to make a bootable disk.

hope this helps

---

### Post by raddellee on 2007-06-28
I clicked copy disk and the options i got were, 'ATAPI DVD DUEL 4XMax' and 'file image', is file image an iso? And with what program would i use to burn onto a cd as an iso?

---

### Post by smoker on 2007-06-28
file image is an iso, and once you have the iso on the desktop, copy as a file to a blank cd (not burn image to disk).

if you want there are some good disk copy/burning appz in the repository, eg, gnomebaker, kd3, are two i've tried and found easy to use, though there are more available.

---

### Post by raddellee on 2007-06-28
Thank you, your help is much appreciated

---

### Post by HermanAB on 2007-06-28
The best CD burning program is 'k3b'.

A CDROM pretty much 'is' an ISO file.  Therefore, any method that can do a low level read of a CDROM device, can extract the file system:
dd if=/dev/cdrom of=image.iso

Even the common kitty can do it:
cat /dev/cdrom > image.iso

Cheers,

Herman

---

