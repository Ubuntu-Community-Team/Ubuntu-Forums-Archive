---
title: "Shutdown problems after installing/setting up NIS (client)"
date: 2005-06-22
forum: General Help
---

### Post by slipjig on 2005-06-22
Hi.

I've installed and set up NIS on my laptop with the help of a Mandriva using friend.  It's working very nicely as long as the machine is on and connected at work (where the NIS server is runnning).

However, when I shut the machine down it appears to hang with "Deconfiguring network interfaces...".

Also, if I try to start the machine up without the network cable plugged in, or at home, startup seems to hang while it tries to run ypbind.

So, the questions:

Any clues as to what could be causing the "Deconfiguring network interfaces..." problem on shutdown?

And how can I set things up so NIS and YP services are only started manually?

Cheers :)

---

### Post by slipjig on 2005-06-22
I'm happy to report that I've solved the network shutdown problem.  In my file /etc/nsswitch.conf, there were some poorly written settings which were causing the computer to refer to NIS before files.  I can go into more detail if anyone's interested.

But I'm still looking for an elegant way to make NIS and YP services *off* by default, only to be started manually...

---

### Post by slipjig on 2005-06-23
Actually - sorry to have bothered you all.  I've decided to use ssh rather than nis for this particular solution.

 :roll:

---

### Post by boltronics on 2005-09-10
I work at a GNU/Linux (almost exclusive) shop, and decided to get my Ubuntu laptop to hook into NIS when I bring it in from home. I seem to be in a similar situation with the Deconfiguring network interfaces... freezing the computer for about 5 minutes before continuing, so I am very curious to know what needs changing. My nsswitch.conf file is the same as a Fedora Core 2 box that works perfectly, so I can't figure it out.

As for the manual activation of the /etc/init.d/nis startup script (which runs ypbind) for when I am at work, I simply created an alias for it in runlevel 3, and turned it off at runlevel 2. I use runlevel 2 by default, and add a "3" at the end of my menu.lst *kernel* line (by hitting 'e' at the grub menu) when NIS is needed.

---

