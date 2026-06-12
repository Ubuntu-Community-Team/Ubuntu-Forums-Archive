---
title: "How to Install VMware Player? Not available in Synaptic; Converted RPM Fails"
date: 2008-04-04
forum: General Help
---

### Post by OzzyFrank on 2008-04-04
OK, I am pretty sure that back in Feisty you could install either VMware Player or Server through Synaptic, and I mean "either" because as I remember, you had to unistall one to install the other (meaning in Ubuntu at least, they couldn't coexist on the same machine).

Now, I have some appliances I can't run in Server, but apparently run fine in Player, so was willing to ditch Server in favour of Player (unless someone knows of a way to have them coexist peacefully?), but Player isn't available through Synaptic anymore.

Now, I did download the .rpm of Player and convert it via Alien (sudo alien -i --scripts) and it seems to have converted fine, but I can't seem to install it. All I am told is that "Installation finished", but then "Failed to install package..." underneath it. Do I first need to get rid of Server? Is this why it is failing? I am running 64-bit but made sure to have the correct version, so it isn't that (besides, it complains when I try to install the 32-bit version). Any ideas? (I'd prefer not to uninstall Server just to find out, especially if one of you already knows that won't make a difference). Cheers

---

### Post by badfish591 on 2008-04-04
Have you thought about trying virtualbox? instead of VMware player, i know some people prefer VMware, but i've had good experience with virtualbox.

---

### Post by Toet on 2008-04-04
When I still needed VMWare player, I installed it myself, but not from the RPM package, but rather the .tar.gz version. There is a vmware-install.pl file in it. Run it with sudo, and you are fine. You need the kernel headers package for it.

---

### Post by OzzyFrank on 2008-04-05
I admit total ignorance regarding virtualbox, but am willing to look at it. My main concern is that all the images I get are for VMware, and even that (or Server at least) can't play all of them (generally the "bagvapp" ones you find compressed in .7z format).

I might try the .tar.gz package and install from that. You say I need the "kernel headers package" for that - do I need to find that somewhere, or are you saying it is needed but comes in the .tar.gz (which is why the .rpm won't work)?

And does anyone know if I am wasting my time trying to install Player whilst Server is still on my system? I'd hate to be getting false negatives. Cheers

---

### Post by zvacet on 2008-04-05
You will find in synaptic **linux-headers-generic.**

---

### Post by chip616 on 2008-04-06
I just installed VMWare Player 2.03 on Ubuntu 7.10 using the tar.gz file and it all went without a hitch.  Full instructions on how to do this are available from VMWare in the "Getting Started Guide" for VMWare Player 2.0.  It is quite easy to do.  All you have to do is unpack the archive (they detail how and where to do this) and then run a script.  Just accept all the default values by hitting <Enter> each time you are asked a question.

As noted above, you have to have the generic kernel headers installed.  

When I installed the player on Fedora 8, I also had to have gcc installed (the Gnu C Compiler) as the script had to compile a version to match the Fedora kernel.  While I did check to be sure that Ubuntu 7.10 had gcc already installed on my machine, I don't think it was used to compile anything.  It appears that there is a generic binary already available for Ubuntu 7.10, but I cannot say that for certain.

In any case, it was very successful, and I am far from being a Linux guru.

Frank.

---

