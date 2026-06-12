---
title: "Booting Fiesty Fawn thru Wubi"
date: 2007-05-18
forum: General Help
---

### Post by JupiterMike on 2007-05-18
Trying to boot Fiesty Fawn thru Wubi.  Dowload went OK.  Ubuntu shows on my boot screen.  Get error message when trying to open.
 Try (hd,0): NTFS5: 3
 Try (hd,1): invalid or null
 Try (hd,2): invalid or null
 Try (hd,3:  invalid or null
 Try (fd,0): invalid or null

Error: Cannot Find CRLDR in all devices.  Press Cntrl+Alt+Delete to restart


Not only do I not understand these messages,  but I cannot figure out what I,m doing wrong.

HELP HELP

---

### Post by ago on 2007-05-18
CRLDR?

Should be **g**rldr. And you should have a file called C:\grldr.

---

### Post by JupiterMike on 2007-05-19
I apologize for my mis-spelling.  Sometimes it's difficult to see the small letters on the screen when you wear bifocals.  I still need help though. What do the messages mean?

---

### Post by raybaron on 2007-05-20
Hi!
I just had the same problem . I copied C:\grldr and c:\menu.lst to d:\ and the error messages went away. I'm still having boot problems, Wubi is installing on my second partition (D:\) and I end up in the BusyBox but still trying to figure it all out once I can get a log posted up here. As Ago mentioned, make sure you have a grldr file in the same directory Wubi has installed everything into. I believe you can determine this during the install procedure. (i.e. it tells you where it is installing as it is installing. In my case, It tried to install on my 500 GB external USB drive. I saw that during the install then unplugged it and re-installed. It then  went to my next largest drive which was my D:\ drive .
thx,
Ray

---

### Post by ago on 2007-05-21
grldr has to be in the same folder where you have boot.ini. If you have boot.ini in several partitions copy grldr on all of them.

---

