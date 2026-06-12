---
title: "how to get around this problem for booting"
date: 2006-11-17
forum: General Help
---

### Post by redsax on 2006-11-17
Someone could help with this critical problem?

I have ubuntu/edgy, and installed sk98lin downloaded
from marvell.com to run its ethernet 88E8056 card.

Somehow, whenever this sk98lin is loaded, my computer dies.
So now the problem is whenever I boot the computer in ubuntu,
the computer dies right away after it loads sk98lin during booting.
I cannot log in ubuntu to change anything for fixing this problem?

Is there any way to get around and fix this problem?
I tried adding some option line after kernel when booting, something
like "nonet" or "noload=sk98lin", but none of them worked.

Any help here? The only way I may think is to re-install edgy, which
will automatically replace every file.](*,) ](*,) ](*,) ](*,)

---

### Post by angrykeyboarder on 2006-11-17
> **redsax said:**
> Someone could help with this critical problem?

I have ubuntu/edgy, and installed sk98lin downloaded
from marvell.com to run its ethernet 88E8056 card.


Just out of curiosity, had you tried installing Edgy without the driver you downloaded?

In other words, how did you know that you needed that driver to begin with?

I'm running Edgy now and have run every version of Ubuntu since Hoary.

I've never had a problem with it detecting my SATA RAID controllers, sound card, TV tuner card, USB controllers, Firewire controllers and my Marvell 88E8001 Gigabit Ethernet Controller (basically it detects all my hardware, even hardware I don't want it to detect - my BIOS-disabled onboard sound).

---

### Post by redsax on 2006-11-17
Edgy does have sk98lin/skge modules. The problem is they 
are kind of out of date (at least not uptodate), so edgy
doesn't identify Marvell controller 88E8056.

I installed the latest driver sk98lin, which automatically
detects the controller and is causing the problem. my bad luck.:( 

anyway to log in to fix the problem?

---

