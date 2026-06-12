---
title: "dumpe2fs: Block bitmap checksum does not match bitmap while trying to read '/dev/sda4"
date: 2019-05-06
forum: General Help
---

### Post by mmalware on 2019-05-06
Hey I had an issue with my pc just a few moments ago , but I was able to fix with after performing a repair on the dpkg packages as well as an Unmount -l and rebooting my pc .
After that I was able to access the desktop , I ran dumpe2fs to see if there is a problem with my filesystem .

I got the following warning  : 
dumpe2fs: Block bitmap checksum does not match bitmap while trying to read '/dev/sda4' bitmaps
*** Run e2fsck now!


I ran e2fsck after that but I got this message : 
e2fsck 1.44.6 (5-Mar-2019)
/dev/sda4 is mounted.



WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.


Do you really want to continue<n>? no


What should I do please ?

---

