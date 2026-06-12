---
title: "Two Separate Samba Directories"
date: 2007-07-07
forum: General Help
---

### Post by tj71587 on 2007-07-07
I have a really old computer holding all the music, so its stable and neone in the house can get to it at netime, now I am starting to develop a site and would like to have two separate drive in windows one with the media on it and one with only the website im working on on it. So i would like two separte network drives on my xp machine, coming from two separate directories, on the ubuntu server. Let me know if that makes sense or if I need to clarify better. One directory (drive on the windows machine) would have apache on it and the other one is just for music. I used this tutorial to set it up.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

So how would i set this up for two directories? The most basic anyone could make it would be great, but any help would be appreciated.

Thanks

---

### Post by Steven_B on 2007-07-07
You should be able to add another file share by adding another share block to the smb.conf:
```
[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
```
Modify the settings however you need them as per the howto.
You can also set up Samba file shares via System->Administration->Shared Folders.

---

