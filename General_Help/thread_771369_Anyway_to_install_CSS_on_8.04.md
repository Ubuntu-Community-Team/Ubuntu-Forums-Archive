---
title: "Anyway to install CSS on 8.04?"
date: 2008-04-27
forum: General Help
---

### Post by Cephaus on 2008-04-27
I have read a while back that someone installed Counter Strike Source on Ubuntu

Can anyone give me a guide?

---

### Post by igfud on 2008-04-27
I can't say I am familiar with the game, but see if this HOWTO is of any help:

[http://ubuntuforums.org/showthread.php?t=5182](http://ubuntuforums.org/showthread.php?t=5182)

igfud

---

### Post by kavon89 on 2008-04-27
> **Cephaus said:**
> I have read a while back that someone installed Counter Strike Source on Ubuntu

Can anyone give me a guide?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=22999](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=22999)

Some people are reporting Wine 0.9.60 is having some issues with HL2/CSS, but 0.9.58 seems to work great. Overall the Source engine works pretty well in Wine.

Basic way to install: 

1. Install wine from the Synaptic Package Manager
2. Run winecfg
3. Copy the Steam folder over from Windows into "~/.wine/drive_c/Program Files"
4. Install the Verdana font (steam requires it), you can copy it from a Windows install and put it into wine's windows/fonts folder.
5. run: wine steam.exe  while inside the steam folder.

@igfud, that link assumes you have Cedega, and that program has a monthly fee associated with it.

---

