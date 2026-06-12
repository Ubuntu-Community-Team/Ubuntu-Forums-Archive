---
title: "Trouble with photorec"
date: 2008-05-26
forum: General Help
---

### Post by klato on 2008-05-26
I've just recently did a "low level format" of my SD card using my Canon PowerShot SD1000.  I'm now trying to recover a few photos off the card that I didn't back up, so I'm trying to use photorec, but I'm having a bit of trouble.

I did *sudo photorec /dev/mmcblk0p1*, which is apparently my card
I ran that with the default options, no partition, Other filesystem, but it just retrieves 6 files, which I cannot even look at because the folder is owned by root...

Any ideas? I've been reading around and it looks like other people have pretty good luck with photorec, but am I just screwed here?

Thanks!

---

### Post by phidia on 2008-05-26
Have you tried using photorec as a regular user-without sudo?
You could also chmod your files/pictures so that everyone can access them.

---

### Post by klato on 2008-05-26
yup i tried it as a normal user as well, but it does some funky things and automatically quits when i start it up. also, the photorec site says to run it as sudo

---

