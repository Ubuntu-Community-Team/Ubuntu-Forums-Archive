---
title: "desktop.ini and Thumbs.db are making my home folders look messy!"
date: 2007-05-26
forum: General Help
---

### Post by happy-and-lost on 2007-05-26
Right. I have classic Windows syndrome in my /home folder (Accessed under WinXP using Ext2ifs). In my Music folder especially I have been plagued by desktop.ini and Thumbs.db files, which are just an eyesore and serve no practical purpose on the system they are accessed on 99.99% of the time. Is their either a way of preventing them from being created, or a nice script to nuke them all when I feel the need to clean?

I've been using
```
 rm /home/jo/Music/*/*/*/*.ini
```
With varying numbers of wildcarded directories to clean up so far, but there must be a simpler way..?

Maybe piping a locate command in? I'm a bit scared of the destructive power of rm to experiment with this. Is there some fearless bash wizard out there who can tell me what I need to hear?

---

### Post by Tautoa on 2007-05-28
If i remember correctly, Thumbs.db is used for storing thumbnails, and desktop.ini contains info on a folder's icon, and other little things. To stop Windows from creating Thumbs.db files, in Explorer, go to Tools, then Folder Options, choose the View tab, and select the "Do not cache thumbnails" option. I can't remember about Desktop.ini files, but i have a similar setup (home folder accessed under WinXP using Ext2ifs), and I dont seem to have any Desktop.ini files, so I must have done something to stop it :)
I'll have a dig around, see if i can remember. :D

---

### Post by fackaff on 2007-12-13
any solution found for this yet?
i keep getting dektop.ini file on my desktop in xubuntu everytime i boot up...
using WinXp in dual-boot with Ext2Fs

---

