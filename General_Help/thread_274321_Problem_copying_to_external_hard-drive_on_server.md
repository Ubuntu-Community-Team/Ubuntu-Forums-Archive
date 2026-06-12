---
title: "Problem copying to external hard-drive on server"
date: 2006-10-09
forum: General Help
---

### Post by AndyCooll on 2006-10-09
This problem has perplexed me for awhile.

I want to backup some of my files, so I have attached an external hard-drive to my server. I then SSH into my server (which is on my internal LAN) and find it is recognised as /media/usbdisk ... fine so far. 

However when I try copying to it I always get the "cp: omitting directory ..." error message. I've tried "cp" sudo cp" and "sudo -s" followed by "cp". 

In the end I find myself have to use xdmcp, logging on to the file server and then using "gksudo nautilus". From there I can manually copy and paste. Indeed I have tried the command line on the server itself and run into the same problems. I simply cannot seem to copy files using this method.

I always thought that using "sudo" or "sudo -s" gave you admin powers, so why am I still meeting restrictions? Surely it's easier than this? :-? 

:cool:

---

### Post by Jussi Kukkonen on 2006-10-09
> I always thought that using "sudo" or "sudo -s" gave you admin powers, so why am I still meeting restrictions?

...Because it's not about permissions, it's about *cp* by default not copying directories. Try *cp -R*

---

### Post by AndyCooll on 2006-10-09
Thanks very much for the reply, you've taught me something (that I probably should have known ...but didn't!)

:cool:

---

