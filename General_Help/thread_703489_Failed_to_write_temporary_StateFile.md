---
title: "Failed to write temporary StateFile"
date: 2008-02-21
forum: General Help
---

### Post by kmzoom28 on 2008-02-21
After searching around a bit, I still haven't found any beginnings to a solution for this.

Whenever I attempt to run adept as root, the "Run as root- KDE su" box comes up, I enter my password and it freezes. The only way to get the box to clear is to kill it using ctrl-alt-esc.

If I run anything requiring root from a terminal, it returns to the prompt without doing/opening anything.
ie:

      [I] kfm@Hytech:~$ sudo mc
       [sudo] password for kfm:[/I]       (I then enter the password)
      * kfm@Hytech:~$ *


If I open aptitude as user and then attempt to become root in the program, I get the following message:

[I]E:Failed to write temporary StateFile /var/lib/apt/extended_states.tmp
E: Subprocess exited with an error -- did you type your password correctly?[/I]


First problem: I never was prompted for my password and even if I was, it would be correct.... I know I'm not entering that wrong. 

Second problem: Since I can't currently become root to attempt to fix anything (not that I have the slightest idea of how to fix it in this case) I'm really at a loss for what to do.


This is the only message I get from any applications. Everything else just hangs or doesn't respond in any way.

There is no way for me to currently open any applications that allow me to add/update software or make changes as root. I'm not really sure of the changes I made at the time when this initially started. The last thing I did was attempt to get Desktop effects working, since that's not cooperating too well with my video card (nVidia 6800xt), which crashed KDE. On the restart, everything came back ok, except this problem emerged. 

Any ideas are appreciated. Thanks!


I'm currently running KDE 4.0.1 on Ubuntu 7.10 with Kernel 2.6.22-14-generic.


~KM


ADD:

Booting into recovery mode at startup allows me to gain full root privileges. I tried removing the extended states.tmp file, which only gave me an error saying it wasn't there in addition to the message it originally gave me. (I have since returned it to its original state)

---

