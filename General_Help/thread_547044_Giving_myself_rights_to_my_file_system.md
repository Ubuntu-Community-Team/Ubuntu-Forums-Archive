---
title: "Giving myself rights to my file system"
date: 2007-09-09
forum: General Help
---

### Post by Fenresulfr on 2007-09-09
Hi,

When I open 'Computer' in 7.04, I cannot make a new folder because the rights are read-only.  How do I change this?

Thanks,

CJ

---

### Post by merlinus on 2007-09-09
In what folder are you trying to create the new one?

File System folders are not meant for storing or creating data.

Try making the folder in Home Folder.

---

### Post by Linux_Man on 2007-09-09
Make sure you are IN the filesystem, when your in computer your really in nowhere, if you want to make a file in the root of your filesytem type in 


```
gksudo nautilus
```

That will give you root permistions to modify anything on your filesystem however if you delete something that shouldn't you can end up killing your linux machine.


However you more then likly shouldn't mess with the root of your filesystem

---

### Post by Fenresulfr on 2007-09-09
Hi again, thanks for the quick responses,

The original problem I was having was installing adobe reader plugin, which defaults its directory to a /user directory, which is read only, but I placed in my home directory and it worked. 

Now I'm trying install Adobe Flash 9, but I'm having a problem executing the install because I'm getting an error:

 [INDENT]ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
[/INDENT]

Any ideas?

The installation package is definitely x86 Linux.

Thanks again,

CJ

---

### Post by Fenresulfr on 2007-09-09
up..

---

### Post by Maestro23 on 2007-09-09
If you are running 64-bit, check the last post in the following thread: [http://ubuntuforums.org/showthread.php?t=538617&highlight=flash+64+bit](http://ubuntuforums.org/showthread.php?t=538617&highlight=flash+64+bit)

---

### Post by Fenresulfr on 2007-10-09
Thanks man!

---

