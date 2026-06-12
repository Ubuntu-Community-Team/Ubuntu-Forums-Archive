---
title: "Nvidia 8500GT driver issues on Feisty 7.04?"
date: 2007-05-15
forum: General Help
---

### Post by a.d.gardiner on 2007-05-15
Hey all,

I've been trucking around the support forums and have gotten the idea in my head that the Nvidia 8500GT is not yet supported fully with 7.04?

I've tried using the 'Envy' script thing which just crashes my xserver - well makes it produce an error, similar results with automatix2 and also with a manual install of 9755 I can't seem to get anywhere.

The error read out after restarting pertains to something along the lines of 'no screens found'.

Any ideas?

I am using the AMD64 build for my AMD 3800 X2.

Thanks,

Alex :) 

(please excuse any inaccuracies in my post, I'm new but doing my best with ubuntu.. kinda enjoying linux)

---

### Post by canonbeck on 2007-05-15
You'll need to use the new beta drivers:

[http://www.nvnews.net/vbulletin/showthread.php?t=90139](http://www.nvnews.net/vbulletin/showthread.php?t=90139)

Although, even with these I have a problem upon the first post-installation reboot:

[http://www.nvnews.net/vbulletin/showthread.php?t=90323&highlight=8500gt](http://www.nvnews.net/vbulletin/showthread.php?t=90323&highlight=8500gt)

So, in summary, I dont think the 8500gt is really functional as yet...

HTH

---

### Post by a.d.gardiner on 2007-05-15
Thanks for the links :)

Looks like im nearly there but there is still one problem.

I've managed to get the Nvdia beta to work, but as soon as I restart the machine all I get is blank black screen.

To get things back up and running I have to restart, go into recovery mode, reconfigure xserver with vesa drivers, reboot, then modify xorg.conf entry from "vesa" to "nvidia". If i then kill the xserver from terminal and then fire it back up again I'm again running with acceleration, but only until I next restart.

Any ideas? ](*,)

---

