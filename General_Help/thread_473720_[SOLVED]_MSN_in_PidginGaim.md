---
title: "[SOLVED] MSN in Pidgin/Gaim"
date: 2007-06-14
forum: General Help
---

### Post by jw5801 on 2007-06-14
Is there anyway to get Pidgin to display the MSN "Personal Message" of buddies (the quote type thing in grey underneath their friendly name in Windows Live or MSN Messenger on Windows)?

---

### Post by Old Pink on 2007-06-14
Only aMSN, Kopete and KMess have that feature.

All three are available in the repositories, but the KMess in the repositories doesn't have that feature, you'll need to install the 1.5 preview 2 version.

**I've complied and uploaded it for you, here:**
[http://www.mfimg.com/files/8/kmess_1.5pre2-1_i386.deb](http://www.mfimg.com/files/8/kmess_1.5pre2-1_i386.deb)

I'd reccomend the KMess above, it's attractive, very easy to use and full of features, even "What I'm Listening To" a first in Linux. 

**To install Kopete, run:** sudo aptitude install kopete
**To install aMSN, run:** sudo aptitude install amsn

... in terminal :)

---

### Post by jw5801 on 2007-06-14
Thanks heaps! I shall give this a shot when I have some time and report back.

---

### Post by jw5801 on 2007-06-15
Hmm... KMess doesn't appear to integrate well into gnome...

Installs ok, but when I run it, it tries to call files that are part of the kde desktop (at least that is my assumption).

On startup the following error arises (although the program itself still runs fine, apart from notifications anyway.):

> KMess will not be able to play sounds and notifications.
The file 'kmess.eventsrc' could not be found in one of the following folders: 
- /home/jw5801/.kde/share/config/
- /etc/kde3/
Please verify your installation, and copy the missing file to one of the listed folders.

I'll give aMSN a shot, otherwise I think I'll stick with Pidgin. I quite like it's interface anyway, the only issue I had was the Personal Message thing. Well... that and not being able to play the MSN buddy game things, but given the distinct lack of directx that doesn't seem likely. :P

---

### Post by jw5801 on 2007-06-15
Ok decided I'd have a look for the "missing" file. Apparently it was named wrong. No idea how or why. There was a file in ~/.kde/share/config/ called kmessrc, so I fixed the problem with:
```
cd ~/.kde/share/config/
ln -s kmessrc kmess.eventsrc
```
All works good now. Thanks for the tips!

---

