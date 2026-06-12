---
title: "Can Dmg be used on ubuntu some how?"
date: 2007-02-22
forum: General Help
---

### Post by rigdzinthar on 2007-02-22
Is this possible,
to run DMG files on Linux,  I just bought a mac, but and love it!
but was wondering about going back to Ubuntu :-D
:guitar:

---

### Post by kb3hkg on 2007-02-22
DMG install files cannot be used, but you can mount dmg drive images. Or atleast that is the understanding I gathered from my previous endeavors.

---

### Post by vav on 2007-03-01
Since OS/X is unix based, if the source code were available would it be possible to compile it for ubuntu?

hasnt someone hacked this already?

---

### Post by Ramses de Norre on 2007-03-01
It's quiet difficult to port mac apps to linux and vice versa... And even if it would be easy, mac apps aren't open source...

For the dmg files, I think you can mount them with a line like this: ```
mount /pathTo/file.dmg /media/createdMountpoint -t hpfs -o loop,rw
``` the "hpfs" could also be "hfs".
The easiest way will be to use iso instead of dmg, it has (AFAIK) the same functionality and works on all OS.

---

### Post by vav on 2007-03-02
So no wine-like emulator for OS/X apps? 

I heard someone talk about a powerpc emulator... can that be used like Virtualbox to install OS/X?

---

### Post by Ramses de Norre on 2007-03-04
The mounting doesn't work?

---

### Post by ZipoTe on 2007-03-07
I have some interest in running MAC applications too and i've tried some line commands but they don't work :( has anyone got working any MAC stuff??

---

### Post by Osvaldo on 2007-03-07
Hi.

Look for** fink:**

[http://www.finkproject.org/](http://www.finkproject.org/)

**Rudix:**

[http://www.apple.com/downloads/macosx/unix_open_source/rudix.html](http://www.apple.com/downloads/macosx/unix_open_source/rudix.html)

**MacPorts:**

[http://www.macports.org/](http://www.macports.org/)

**And Gnu Darwin:**

[http://www.gnu-darwin.org/](http://www.gnu-darwin.org/)

I haven't tested them myself, but I believe they should work.

Best regards

Osvaldo

---

