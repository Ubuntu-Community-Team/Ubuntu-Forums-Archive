---
title: "Android device ends up at different places every time"
date: 2014-11-16
forum: General Help
---

### Post by guraknugen on 2014-11-16
Old Ubuntu 12.04:
My Nexus 4 always ended up at some place like ~/.gvfs/mtp/SomeName/
Now, in Ubuntu 14.04, the place is different all the time. Right now it is:
/run/user/1000/gvfs/mtp:host=%5Busb%3A001%2C007%5D/
Nautilus also says: mtp://[usb:001,007]/
The last one doesn't work in a terminal though.

Now, I am working on a script that is supposed to copy some files to the Nexus, and sure I know that I can let the script figure out the correct path, but it would be so much easier if there was a way to make sure that the path is the same every time. Is this possible? Besides, other software, that use my Nexus for storing, needs to know where to look for the files without any manual work involved.

I asked this question on a few other forums and mail lists, but nothing so far. And I did some searching too, of course, but either I didn't type the right things (English is not my native language) or there is just nothing out there to help me…

It would be very nice if it is mounted as something like ”/run/user/1000/gvfs/Nexus4/” (because ”/media/${LOGNAME}/Nexus4/” will never happen, right?).

---

### Post by guraknugen on 2014-11-23
I'm not sure what to think about this. Am I really the only one who experience these problems? Ubuntu and Nexus 4 (or maybe any Android device) can't be such an unusual combination, can it? Or is it just that there is no obvious way around this? Or maybe just nobody around here knows anything about this? It can't be that bad, can it?

---

### Post by guraknugen on 2014-12-20
Seriously? Nobody?

---

