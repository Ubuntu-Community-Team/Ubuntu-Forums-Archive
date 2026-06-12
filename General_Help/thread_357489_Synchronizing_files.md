---
title: "Synchronizing files"
date: 2007-02-09
forum: General Help
---

### Post by GoodPanos on 2007-02-09
I have 3 PCs and one NAS.  One WinXP, one WinXP/Ubuntu and one Ubuntu.  Do you have any suggestions on how to synchronize files from all three PCs.  I like it to be seemless like the equivalent of SyncToy.

Thank you

---

### Post by nickoli_02 on 2007-02-09
I hear rsync is pretty good. Havent used it myself, so thats all I can do for ya :P

---

### Post by shak on 2007-02-09
You may have a look on the Unison Project.
In short : From the  Pennsylvania State University for Unix/Windows/Linux:
Unison functions as a two-way rsync.

[http://packages.ubuntu.com/edgy/net/unison](http://packages.ubuntu.com/edgy/net/unison)

Enable SSH-Server on all machines in your Wlan and you have a solid solution.


kind regards

edit: i should mention there is a gtk version 

```
sudo  apt-get install unison-gtk 
```

[http://doc.gwos.org/index.php/UnisonAndOSX](http://doc.gwos.org/index.php/UnisonAndOSX)

---

### Post by n00blar on 2007-03-22
I have yet to get Unison running properly between my XP and Linux box; after two hours of trying, I gave up.

PowerFolder is another solution, but this software is buggy at times. I got it to run fine for about two months when bugs crawled up. The application configuration files get corrupted or something and it looses all your sync settings and so on, and then all hell breaks loose.

Too bad MS bought out FolderShare, by far one of the best sync apps out there, and yes, they used to have a Linux version that got pulled out once MS bought them out. You can get version for Windows and OS X, but not Linux.

---

### Post by Krydahl on 2007-08-24
Did you make any progress on this? I have a similar set up (one XP machines, one Ubuntu and a NAS).

I got Unison to sync the NAS and the Ubuntu machine, but then found that the XP machine now thought every file on the NAS had been changed as a result.

PowerFolder looks interesting. Has anyone else had problems with it?

---

