---
title: "XGL Help."
date: 2007-01-30
forum: General Help
---

### Post by Roasted on 2007-01-30
I found a how-to guide for XGL help, but I got stuck.

I was using this tutorial found on this page. [http://www.ubuntuforums.org/showthread.php?t=127090](http://www.ubuntuforums.org/showthread.php?t=127090)

I got to this point:

------------------------------Start---------------------------------------

Now restart the x-server, and everything should start fine. If you gfx card won't run with x now, Xgl won't run.

NOTE: If you can't run the x-server, you have to do this:

Code:

sudo apt-get install linux-image-2.6.15-14-k7 sudo apt-get install linux-restricted-modules-2.6.15-14-k7

I used the k7 for my amd64. You propely have to use 386 instead.

Maybe then reinstall nvidia-glx and nvidia-kernel-common again, just to be sure.

Reboot, and try start x again.

----------------------------------------End----------------------------------------

The problem I ran into is actually a couple. For starters, how do I reboot the x-server? Also, I skipped that step since I didn't know how to do it and tried to do the "sudo apt-get install linux-image-2.6.15-14-386" and it said it could not find the packages. I assume it's because a repo is not enabled. But how do I know which? In the guide it said "Dapper Universe" but I couldn't find it and assumed I already had it enabled... maybe my headache is getting to me because I have to be overlooking something simple.

---

### Post by igknighted on 2007-01-30
Are you using an NVIDIA card?  It appears this guide is for NVIDIA cards.  If you are, have you tried AIGLX?  It avoids many of the complex problems that XGL has as it is native to the system, plus it is generally faster than XGL and you can use 3D apps while using beryl/compiz.

---

### Post by Roasted on 2007-01-30
Yes. It's a NVidia Geforce 6600 256mb PCIE card.

No, I am unsure what AIGLX is.

---

### Post by igknighted on 2007-01-30
Ok, there are two engines Beryl and compiz can run on.  XGL is a rather crude and at this stage poorly implemented engine for beryl to run on.  AIGLX is integrated into the standard xserver and is a much more refined implementation right now.  However, almost half of users can't use it because ATI's drivers dont support AIGLX right now.  All you need to do in order to run Beryl on your card is install your NVIDIA graphics driver (package nvidia-glx from synaptic) and then find a repository for beryl (there are probably directions for that in your guide, or post back if you can't find one or don't know what I mean) and install the package 'beryl'.  Thats it, then you can run 'beryl-manager' from a command line and it should work like a charm.

---

### Post by Roasted on 2007-01-30
How can I reverse everything I already did and start from scratch? Or does that even matter? I'm doing what you said in the previous post right now, I'll report back with whatever I find.

edit - actually, what is that repository? Then do I just apt-get beryl?

---

### Post by igknighted on 2007-01-30
Try this guide, it can explain it better than I can.  Use method 1 for the NVIDIA driver install if you havent installed them already, and if you have, just skip that section.

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

As for starting from scratch, you might have to go back and delete the changes you made manually.  Go back to the guide and see if you can go back.  Otherwise I'm not really sure, I'm very re-install happy so that would be my solution, but I am positive you can undo it w/out slash and burn tactics, I just don't know it.  You could use dpkg-reconfigure xserver-xorg to reset xorg.conf, but if I remember correctly there was a .xgl script you had to add and maybe some changes to another file.  These I would try to undo.

---

