---
title: "Ubuntu crashes whenever I open my ownCloud folder"
date: 2013-11-10
forum: General Help
---

### Post by plazman30 on 2013-11-10
So, I decided to take my data in my own hands, and set up my own ownCloud server.  So far, it's been working pretty good, though there are  few little glitches here and there...

And, here is the first glitch....

On Ubuntu 13.10, I have the 1.4.2 version of the ownCloud client installed from the ownCloud.org repository.  That seems to work fine.  However, when I try and open the ownCloud folder on my desktop, Nautilus immediately crashes.  How can I troubleshoot this, so I can see what's causing it to crash?

---

### Post by plazman30 on 2013-11-10
Woohoo!  Figured it out myself.

Went into bash and did an ls -al | more.  Saw 3 zero byte files.  I figured these files were probably corrupt, so I deleted them.  Nautilus now opens without crashing.  Love it when it's something simple.

---

### Post by wavesound on 2014-04-14
Hi
I had this when video downlod helper tries to copy a youtube video but just makes a 0 byte file.

This then crashed Nautilus untill you manually go in at the CL and remove it.

Seems  Google keep breaking the video downloader and this is the result.
A real pain.

---

