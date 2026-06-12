---
title: "Mount Windows Share Permanently"
date: 2012-11-06
forum: General Help
---

### Post by chideock on 2012-11-06
I had trouble mounting windows share. I wanted to auto mount so that my Ubuntu 12.04 computer would connect to my windows server on my home network. I spent a lot of time in the last several days trying to get it to work. 

If it helps anyone, since I have seen a few posting here with the same problem, this is how I finally got it working.

Go to this doc 
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) 

and follow the instructions, in my case I am using "[SIZE=2]Mounting unprotected (guest) network folders" so I used the entry in fstab[/SIZE], all one line,

//servername/sharename  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

I changed //servername/sharename to my system which is //storage/public

This did not work until I made my servername "storage" capitals so that my fstab entry startes //SERVERNAME/sharename  etc
It works all the time now

---

### Post by dcstar on 2012-11-09
> **chideock said:**
> 
........
It works all the time now

Then this thread is **SOLVED**, isn't it?

---

