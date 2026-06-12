---
title: "Where'd the login screen go?"
date: 2007-05-18
forum: General Help
---

### Post by iPirates on 2007-05-18
Firstly this - I do not think that it's the video card, or the nVidia drivers that caused this problem.

I've installed a new graphics card - nVidia 8600 GTS.  The card worked fine under the "nv" drivers, however I wasn't able to alter my resolution (1680x1050 - even by manually editing my xorg.conf file.)

So, I downloaded and installed the nVidia drivers for my card - the only ones actually available are in the beta version.  I logged out, Ctrl+Alt+F1 to bring up command prompt, stopped my x-server and installed the drivers.  (I had previously deleted my old nvidia-glx, in order to install the new nvidia drivers).

It installed fine, then backed up and altered my xorg.conf file, restarted the xorg server, logged in, and it worked perfect.  I changed the resolution in my xorg.conf, restarted my xorg again, the nVidia beta splash screen came up, and I was good to go.  

After I restarted my computer completely however, it now never makes it to the login screen.  After the Kubuntu loading screen is finished, it flashes a little text (no errors that I can see), and I'm left with a blinking parser, as if the computer doesn't know what to do next.  I hit ctrl alt f1 again, and it brings me to the command line login, which works fine.

I think it has something to do with the x-server, or even Kubuntu.  I'm running feisty, and i've noticed Kubuntu occasionally hangs on loading screens, or shutting down screens.  Now it refuses to give me a login, unless I choose to manually login through prompt. ...

any ideas?  maybe this is a potential bug.

---

### Post by arloth on 2007-05-18
see this thread here, [http://ubuntuforums.org/showthread.php?t=432340](http://ubuntuforums.org/showthread.php?t=432340)  for full instructions..

The nvidia 8600 series isn't too well supported yet - it hasn't been out too long yet, but the beta drivers seem to work, i've been able to play Nexuiz without problems.  

good luck with getting it to work.

---

### Post by iPirates on 2007-05-18
hey thanks for the reply, but i actually solved it sorta...

turns out it was kubuntu.  i installed ubuntu and tried installing it the exact same way, and it works perfect.... i'm assuming it's a bug?

---

