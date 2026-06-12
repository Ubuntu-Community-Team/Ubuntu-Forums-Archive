---
title: "using ssh and a live-cd to recover files"
date: 2007-02-23
forum: General Help
---

### Post by dexter on 2007-02-23
I just came back from a friend who's having computer problems. His windows is no longer able to boot. He told me he was planning on "cleaning up" his pc, so he would not mind it if I would format his hard drive and reinstall windows. The only thing i had to do was take a backup of his files in the My Documents folder. 

I was armed with an Ubuntu live-cd and my little friend, my MacBook. I put the live cd in his computer and booted. I could get into linux just fine. His harddrive wasn't auto mounted, but that was easily fixed. After being able to read his files at that computer, i installed openssh-server. Now i thought i could copy the files to my MacBook using ssh. 

The first problem I encountered was that the live cd uses the user ubuntu and no pass. I could not connect to the computer by using ubuntu or root as login name. But that did not seem to be a big problem, i just added a new user with password. After that, i could login to the computer using ssh from my MacBook.
This new user however did not have the rights to read the windows drive, and I did not found a way to get rights (using chmod, chown, ...). A possible solution would be to add this new users to administrators, however i could not get this done.

So after quite some frustration (mainly because my linux knowledge was unsufficient), i could not do the job at his home. I took the computer to my place, connected the harddrive to another computer, made a backup of the files, and windows is installing as we speak. 

So what should i have done to do the job there ? It must be possible to add a user which has sufficient rights to read the hard drive ? What did I do wrong ?

---

### Post by taurus on 2007-02-23
You should have mounted it like

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows **-o nls=utf8,umask=0222**
```

---

### Post by dexter on 2007-02-23
> **taurus said:**
> You should have mounted it like

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows **-o nls=utf8,umask=0222**
```

Can you give a quick explanation what the bold part does ?

---

### Post by taurus on 2007-02-23
It means mounting it with a read permission for everybody--222.

---

### Post by dexter on 2007-02-23
Thank you very much!
This is something i won't forget soon :).

---

