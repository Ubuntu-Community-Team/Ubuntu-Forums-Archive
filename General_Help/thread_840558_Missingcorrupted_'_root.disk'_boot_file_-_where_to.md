---
title: "Missing/corrupted ' root.disk' boot file - where to find?"
date: 2008-06-25
forum: General Help
---

### Post by Fatal Equinox on 2008-06-25
Hello,

First off i am running 8.04 hardy through wubi and all was pretty much fine. However, Wubi lost the ubuntu/disk folder and with it i lost 'root.disk'.  Does anyone know where i can get a copy of this file so i can at least boot into ubuntu one more time to take off some files.  Or even just how to access the the files in ubuntu through windows to take off what i need.  

Thank you

---

### Post by jtpoole99 on 2008-09-24
:confused: 

I found the root.disk file for my corrupted system on the actual drive I used to install Ubuntu on in the first place.  So look for that drive if you can and then go to ubuntu/disks folder and the root.disk file should be right there.  All I need to know now is how to access it so I can go in and get my files out of there too.

:confused:

I hope this helps you out...

---

### Post by dodle on 2008-09-24
Your root.disk should be located in the following directory:

C:\ubuntu\disks

To access the files on root disk, you need [Linux Reader]("http://www.diskinternals.com/download/Linux_Reader.exe").

In Linux Reader:  Go to Drives > Mount Image.  Click "Browse".  Make sure that down at the bottom at "Files of type", "All Files" is selected or else it won't see root.disk.

If Linux Reader doesn't work alone, then you will also need to install [Ext2fsd]("http://downloads.sourceforge.net/ext2fsd/Ext2Fsd-0.46a.exe?modtime=1212530235&big_mirror=0").

---

