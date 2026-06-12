---
title: "oracle-xe installation problems on edgy"
date: 2007-09-09
forum: General Help
---

### Post by jxbmeister on 2007-09-09
I am a total noob on ubuntu.  I originally installed oracle-xe.   Had problems with the listener not starting so I attempted to reinstall.  In the process I accidentally deleted the /etc/init.d  entry for oracle.  Can anyone tell me how to recreate this file/link.  

I have been following the instructions from [https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g).
I have run the following commands:
apt-get update
apt-get install oracle-xe
 
I am now stuck since I can't find the /etc/init.d entry.

Any help would be greatly appreciated.  Thanks in advance.

---

### Post by scxtt on 2007-09-09
try removing it, then reinstalling it ...

aptitude remove oracle-xe
aptitude install oracle-xe

---

### Post by jxbmeister on 2007-09-09
Thanks. I tried it: 
aptitude remove oracle-xe
aptitude install oracle-xe

Again, no entry in the /etc/init.d  for oracle.  

Does anyone know what should be in that script/file?   

Thank you.

---

### Post by jxbmeister on 2007-09-09
When I run:
 sudo apt-get install oracle-xe  

This is the output I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-xe is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.

This is exactly what I was getting before.  I still have no oracle entry in the /etc/init.d  directory. 

To  perform a complete uninstall is there anything else I need to delete? 

Thanks in advance.

---

### Post by scxtt on 2007-09-09
did you not use sudo w/ the commands i gave above?  you didn't in your opening post, so i figured you were root or figured it out for yourself ...

i'm wondering if you can just download the .deb (via aptitude) and extract it ... i do find it odd that it doesn't want to put it back.

---

### Post by jxbmeister on 2007-09-09
Thanks scxtt,

Yes I used sudo on all the previous commands.  Still no luck however.

---

### Post by scxtt on 2007-09-09
if those .deb files weren't so big, i'd download them and see if the startup script was in there ... you should  be able to look through the cache (/var/cache/apt/archives) and find that .deb, open it w/ an archive manager and possibly find that file ...
```
 oracle-xe-client_10.2.0.1-1.2_i386.deb    25-May-2006 00:18   25M  
 oracle-xe-universal_10.2.0.1-1.1_i386.deb 25-May-2006 00:20  250M  
 oracle-xe_10.2.0.1-1.1_i386.deb           25-May-2006 00:19  210M
```

---

