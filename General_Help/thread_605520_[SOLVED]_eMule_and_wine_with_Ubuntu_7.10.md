---
title: "[SOLVED] eMule and wine with Ubuntu 7.10"
date: 2007-11-07
forum: General Help
---

### Post by squalho on 2007-11-07
I'm running emule under Linux, Ubuntu 7.10. I use wine to emulate the windows' version of emule.
My problem is this: everything seems to be fine, i corretly connect to servers and kad, i obtain high id, i can search for file and download, but in the upload section i have never seen a sigle request... this is really strange. Under windows even with a few shared files there is always a lot of people in the upload queue and my emule is always uploading. Under linux the upload queue is always empty, although i'm sharing really popular files..
Can anybody tell me if there's something wrong? I can't believe that in hours and hours of connection i don't receive neither a sigle upload request. Is there a network problem, or something related to the emulator (wine) or something else??
Thanks

Squalho

---

### Post by mpierce on 2007-11-07
You are probably experiencing some type of firewall problem since you are using wine which is an emulator. My bet is that you don't have it configured properly to receive requests. A long time ago when I ran VMWare to do a few things I ran into a similar type of problem; pulled my hair out before solving it. Do a google search to find out how you have to configure when using Wine.

---

### Post by mpierce on 2007-11-07
Forgot to mention that you run amule directly under ubuntu without the need for wine. It will be a hell of lot easier as I used amule previously.

---

### Post by weblordpepe on 2007-11-07
amule?

---

### Post by Hallvor on 2007-11-07
Much better to use a native client, imho...

---

### Post by Unspeakable Horror on 2007-11-07
Yes, but unfortunately it seems it doesn't support files bigger than 4GBs.

---

### Post by Hallvor on 2007-11-07
If you know how to compile, you could use the aMule CVS version. It has large file support.

---

