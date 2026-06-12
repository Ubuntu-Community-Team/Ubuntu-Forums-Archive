---
title: "sapphire x1950 bigdesktop only in loginscreen"
date: 2008-05-14
forum: General Help
---

### Post by no_hup on 2008-05-14
hello, this is my first post.

As from the title, I installed ubuntu8 and enabled restricted drivers (ati drivers, those automatically detected). Then I downloaded the last opensource ATI drivers installer from the support.ati.com site and installed.

After realizing I'm a jerk because I couldn't find the ATI controlcenter anywhere.. and it was a gigantic link I wasn't able t see :D .. I start this controlcenter and set up my two monitors (one LG23 and a Samsung32 TV, vga connected) and it correctly switches to bigdesktop.

It requests me to reboot, but always when I do, the bigdesktop only affects the login screen, and once xorg is loaded it switches always back to clone mode.

How can I resolve this issue?

I noticed that when I configure ati catalyst control center to use bigdesktop the xorg.conf file is not changed, and this does not sound good to me, so I launched the c.center with root rights but again no changes in xorg.conf, while I expected to see 2 monitors .. 2 devices .. etc. Perhaps am I missing some package or application to install? The ubuntu-embedded applications to manage the resolutions or the displays does not detect my videocard configuration (says vesa or unknown, or see 3 monitors output (1 motherboard, 2 ATI videocard I suppose) but I can enable only one at a time.
If I run opengl tests as flgears or simlar I prove that ogl is fully supported and running > 2000 fps, so it's installed!

Thanks in advance.

Paolo

---

### Post by no_hup on 2008-05-14
p.s. I've read in many places that some people succeded in this by going to "screen & resolutions" (something like that, now I'm at at office with xp) and setting a "big screen resolution" that should become available, and then it would do.
The problem is that in that application all I get is "unknown.. unknown... 60Hz .. 800x600" so I always quit it without apply those  pesky faulty settings. Am I doing wrong?

---

