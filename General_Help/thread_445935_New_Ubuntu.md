---
title: "New Ubuntu"
date: 2007-05-16
forum: General Help
---

### Post by linuxbun on 2007-05-16
Jeez, where have I been? 

I've only just found out there's a new Ubuntu out (yes I know I need to be IN more :lolflag: ).

The last time I formated this laptop it took me 5 hours to get it back just the way I want it (yes, I'm a very fussy moo).

How good is the one compared to Edgy? I'm a bit reluctant to upgrade right now unless it's seriously that much better.

Just interested in your views.

Many thanks!!

---

### Post by aysiu on 2007-05-16
Well, if you [back up your current Edgy installation](http://www.psychocats.net/ubuntu/backup), you really have nothing to lose.

Do you have anything to gain?

I, for example, didn't have working suspend on my laptop in Edgy or Dapper. Once I upgraded to Feisty, suspend worked out of the box.

---

### Post by linuxbun on 2007-05-18
> **aysiu said:**
> Well, if you [back up your current Edgy installation](http://www.psychocats.net/ubuntu/backup), you really have nothing to lose.

Do you have anything to gain?

I, for example, didn't have working suspend on my laptop in Edgy or Dapper. Once I upgraded to Feisty, suspend worked out of the box.

Ooooh nice! Same here, that never works on this.

At the moment I only back up my home folder. 

My only question is can I backup all my programs and settings, install fiesty then restore all the programs? I'm not sure if this will be possible as I've got programs like vmware installed.

Am I right in thinking that I would have to re-install programs like vmware back manually?

Thanks

---

### Post by carlosqueso on 2007-05-18
You could try upgrading through the update-manager.   Then you would keep everything.  From what I've been hearing, upgrades were a lot smoother Edgy->Fiesty than Dapper->Edgy.

---

### Post by allwin on 2007-05-18
> **carlosqueso said:**
> You could try upgrading through the update-manager.   Then you would keep everything.  From what I've been hearing, upgrades were a lot smoother Edgy->Fiesty than Dapper->Edgy.

Yeah, I did the update manager route on 2 PC's here, Edgy>Feisty.  Both worked.  Took about twice as long as the progress bar indicated (said 2 hours, took more like 4-5).  Other than that, the only BIG surprise was that /dev/hda turned into /dev/sda and some tweaks I had which previously addressed /dev/hda NO LONGER WORKED.  For example, explicitly turning on DMA to the hard drive and all that.  Also changing the EXT3 options in fstab no longer "stuck" in Feisty.  Since all disks now seem to use the SCSI/Sata/whatever drivers, you can't set DMA and 32 bit explicitly.  However they seem to be almost as fast even though you can't set them.

Oh...and when you disconnect an external USB device, IT REMOUNTS (well known bug).  Use unmount in a terminal window.  Don't forget to have ENVY installed so you can reload the Nvidia drivers if you are so inclined, or your first login will be a PITA after the upgrade.

Allow a good 6 hours of uninterrupted face time when you update.  That way you won't be up all night.  Can't disturb the thing while it's installing.  Things may be better these days now that the rush is over!

---

