---
title: "unreliable boot on laptop in Ubuntu 16.04"
date: 2018-05-19
forum: General Help
---

### Post by gleedadswell on 2018-05-19
My computer is failing to make it as far as the login screen frequently on boot.  The behaviour is intermittent and I haven't figured out any pattern to when it does this and when it doesn't.

I am running:
```

geoff@kubo-mobile:~$ uname -a
Linux kubo-mobile 4.4.0-124-generic #148-Ubuntu SMP Wed May 2 13:00:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

This is a Dell laptop.  The system details say:

Processor: Intel® Core™ i5-7300HQ CPU @ 2.50GHz × 4
Graphics: GeForce GTX 1050/PCIe/SSE2

To run the NVIDIA graphics I have installed the package:
nvidia-387
Synaptic says the current version of this package is 390.48-ubuntu0~gpu16.04.3

Here is more on the symptoms.

Sometimes the boot goes normally with no trouble.  Sometimes it gets stuck on the blank dark purple screen.  The bongo drum sound that normally accompanies the login screen plays, but it remains on the blank purple screen instead of bringing up the login screen.  When this happens I usually try ALT+SHIFT+PrtScr+REISUB.  Often I have to do this several times in a row before it successfully boots.  Sometimes I resort to a hard reboot with the power button if it does this a few times.  Usually if it successfully boots after one or more failures then at some point during the boot there will be a black screen with text reporting one or more orphaned inodes.

Sometimes when it has failed to boot correctly and I have rebooted it, upon the reboot it reports that the system is running in low graphics mode.  If I tell it to run in the default graphics mode it will then successfully get to a login screen but there will be no wifi connection.

---

### Post by oldrocker99 on 2018-05-19
It is possible that an upgrade to the nVidia 390 drivers could solve your problem. It's worth a try.

---

### Post by gleedadswell on 2018-05-20
> **oldrocker99 said:**
> It is possible that an upgrade to the nVidia 390 drivers could solve your problem. It's worth a try.

Hmm...didn't notice that the nvidia-390 package is already installed.  Might it be a problem if nvidia-387 and nvidia-390 are both installed?

[Nope, nvidia-387 is a transitional package for installing nvidia-390.  It says it can be safely removed.  I've done so but no apparent change to the behaviour.]

---

### Post by gleedadswell on 2018-06-05
I seem to have fixed the problem!

Doing some reading I came across the grub kernel parameter, vt_handoff.  Apparently it is supposed to make a "smoother" looking boot, with a lot of the black screens full of cryptic messages hidden by the "aubergine screen".  Anyway, since the problem with my boot was that it often got stuck in the aubergine screen, I reasoned that turning off vt_handoff might fix it.  After a bit of fiddling I found that in the /etc/grub/10_linux file is a line:

```

vt_handoff=1

```

Just commenting out this line seems to have fixed the problem.  I note that now that I can see the messages during the boot I must have some other things happening that are slowing down my boot (lots of orphaned inodes and things like that).  But at least my boot is reliable now.

I'll flag this as solved.

---

