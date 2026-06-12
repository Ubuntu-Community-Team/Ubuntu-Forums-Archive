---
title: "How do I share files w/ Vmware xp &amp; Ubuntu?"
date: 2007-10-01
forum: General Help
---

### Post by kris2pe on 2007-10-01
How do I make a share folder for both Vmware & Ubuntu?

---

### Post by JawsThemeSwimming428 on 2007-10-01
Try these:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer+samba)

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

[http://ubuntuforums.org/showthread.php?t=559147](http://ubuntuforums.org/showthread.php?t=559147)


The first two worked for the most part, it was just getting them to work together that was tricky. I got it working on Vista and Feisty so it might help ya out. Worth a look.

---

### Post by veloce on 2007-10-01
> **kris2pe said:**
> How do I make a share folder for both Vmware & Ubuntu?

Once you have samba worked out, there are some tricks for using it btw a xp vm and an ubuntu host.  

Vmware sets up three virtual networks (by default from the repositories):
host only
bridged
nat

For communication btw host and vm you want to ensure the communication goes over the host only.  The others can be incredibly slow - it's like the info is going out to the wider network and circling a few times before coming back!

The easiest way to ensure this is to turn off the other two networks.  Otherwise you need to tweak the routing table on both machines - I've not done it and don't know how.

(Or the complicated approach I take (for other reasons mainly) is to have a virtual firewall to manage either bridged or nat networks and the only direct connection to the host uses host only network.)

---

### Post by kris2pe on 2007-10-07
I just use the seamless procedure so I don't need to give myself a headache!
But thanks!

---

