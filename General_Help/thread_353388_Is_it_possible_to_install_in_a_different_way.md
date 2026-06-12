---
title: "Is it possible to install in a different way?"
date: 2007-02-04
forum: General Help
---

### Post by ZarathustraDK on 2007-02-04
Heya.

I have problems when installing from the live-cd (also from the alternate cd). Somehow it seems my cd-drive is a bit screwy when it comes to actually booting something, otherwise it plays cd's nicely when in an OS. I guess it could have something to do with me running IDE-ports from a pci-card, but there really isn't much I can do about that at the moment.

So, I managed to install the very basic system from the alternate cd (command-line mode), and from there install all the other packages so I ended up with a windowmanager and some basic usability.

The problem is : it aint pretty. The way the system runs really gives off an impression that there's a multitude of packages that's missing and even some which shouldn't be there. Trying to run Wine or other programs that demands a little bit more stability than the basic apps usually results in failure.

My question is : Is there a way to get from a commandline install to an OS identical with a normal live-cd installation? Or somehow type in a "magic" command that fixes the system back/forward to that of an identical live-cd installation from where I'm at now? Booting from anything is basically not an option for me (yeah yeah, except the harddrive ofc ;-)

---

### Post by citizenofnowhere on 2007-02-04
Let's see what we can do here :)

How about we try to figure out why your disk isn't booting up. Do you get any errors (specifically "unable to mount root file system"?) Does it just hang at some point? 

Which version of Ubuntu are you installing? Dapper/Edgy? Do you have a SATA harddisk plugged in?

---

### Post by citizenofnowhere on 2007-02-04
Just thought of a couple of more things you could try:

```
sudo apt-get install ubuntu-desktop
```

This is a meta package for the entire system.

If that doesn't give you all you need, there's also this howto - looks like it's meant for an alternate install as well. Some of these repositories could be helpful.
[http://users.piuha.net/martti/comp/ubuntu/install.html](http://users.piuha.net/martti/comp/ubuntu/install.html)

---

### Post by ZarathustraDK on 2007-02-04
Nah it appears to be pretty random. My experience is that it's something that has been getting worse over time. Back when I installed Dapper it was like a 50/50 chance I could get to the live-cd partition program without the cd clogging up underway. When it came to edgy I could barely get past the menu after bootup before the cd went down (And when I say "went down" I mean like the sound when there's a huge scratch on the cd and one tries to run it without succes. Problem is, I tried with a lot of different installation cd's, some burned some prepressed). I have had the "unable to mount filesystem"-error before and was able to fix it. This really seem like it's hardware related because of the randomness.

On a lighter note I suspect it's the same thing that made me dump XP, since I got booted from the OS 30 days after the wga warning, and was then unable to boot up with the XP-cd: I thought to myself "Heh, good riddance then, Linux here I come" :-)

But to answer the questions :

- It hangs at random, no errors or warnings.

- Harddisk is IDE connected through a PCI-card with IDE-ports.

- CD connected directly to the one IDE-port on the motherboard (Most likely this, in combination with the afore-mentioned pci-card, is the root of the problem, alas investing in hardware is not an option right now).

- At the moment I'm running a weird hybrid of a Xubuntu and Ubuntu install, edgy-grade.

---

### Post by citizenofnowhere on 2007-02-04
Eek, sounds like a fun time :) Glad you dumped XP! Hope the other stuff is helpful...

---

### Post by zvacet on 2007-02-04
If you still have Dapper on your comp,why don´t you just upgrade with alternate CD?
gksu sh /cdrom/cdromupgrade

---

