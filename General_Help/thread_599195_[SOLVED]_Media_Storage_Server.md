---
title: "[SOLVED] Media Storage Server"
date: 2007-11-01
forum: General Help
---

### Post by ghandi69_ on 2007-11-01
Hey guys, I recently installed server edition on an old machine with a huge hard drive, and I have loaded all of my music files (.mp3) and movies (.iso) to it.  I haven't however, been able to play these files. 

My goal is to be able to browse the network, click on the video/audio file, and say open with vlc/xmms and play the file.  My network has 2 Ubuntu machines viewing the server, and 3 XP machines.  One thing I wish to avoid is having to mount the server directories locally on any of the machines.

Is there a way to do this??

( I am using Samba currently on the server, and I can successfully browse the network and find the files. I just can't play them as of now on the Ubuntu machine(havent tried the xp machines)

---

### Post by JBAlaska on 2007-11-01
What happens when you try to play a movie iso through VLC?

I do this flawlessly between my Ubuntu mediaserver, a windoze mediaserver and a modded xbox running XBMC, all through samba.

Maybe your samba permissions are not set correctly?

---

### Post by ghandi69_ on 2007-11-02
Oh Screw it, everything works fine on the XP machines, and I've decided that mounting the samba share locally on the ubuntu machines is the way to go, and that fixes the problem.

---

