---
title: "a couple more questions (automatix and Grub MBR)"
date: 2007-03-06
forum: General Help
---

### Post by theophane.weber on 2007-03-06
Hello again,

I realize I have two more questions (sorry for bugging you with that. If I ever become more knowledgeable, I promise I ll spend time on the forum helping out others..)

a) Automatix
I understand the question does not necessarily make sense (and does not have one good answer), but in general what is the consensus on automatix. I know it used to be fairly negative. Now, with automatix 2 promising not to touch your sources, not --force-yes ing the installs and everything, is it really dangerous.  I came to linux to learn it, but at the same time, I think I understood how to add reps to synaptic,  and how to do sudo apt-get, sudo dpkg and similar install commands. I guess I would be willing to spend more time on other stuff than installing countless packages, so I am interested in using automatix. Can it harm your system?

b) boot, GRUB and MBR

I have a disk partitioned in four, with two partitions (/ and swap on (hd0,0) and (hd0,1) ) for ubuntu, one for xp(hd0,2) , one for vista (hd0,3). Previously, I installed ubuntu first, got grub info from it, plugged that info in xp, installed vista. So, bootldr was on my MBR, and was able to boot all three systems from it. Since, I reinstalled ubuntu (to upgrade to edgy) on (hd0,0), and because I didn want to destroy my install, used the alternate cd and told ubuntu NOT to install grub on the MBR, but on (hd0,0). Since vista was on the MBR, I thought that vista loader would still be kicking in at start, and at worst I wouldn be able to boot ubuntu from it (since I had changed the kernel). Things happened differently, I am not sure why:
even though supposedly (I really don t know, in the end) vista is still on the MBR, somehow Grub starts first, and suggests either Ubuntu, or Longhorn. If I choose ubuntu, it boots. If I choose Longhorn, I then get my old boot screen with a choice between ubuntu and windows vista or xp.  If I choose ubuntu, it does boot ubuntu. Vista and XP still boot fine.

I guess I am just curious about what happened....

c) Hibernate

I like putting my system in hibernation (saves power, nature, the planet and all). The only time I used hibernate on ubuntu, when I restarted my system, it was as dead. Wouldn boot hard drive, cd, anything. It was stalling at BIOS ! (the freakiest computer thing that ever happened to me). I couldn t even get to the BIOS. I disconnected the computer, played with the RAM inside (out of sheer desparation). Left for work. Came back, reconnected the power supply, and it worked (i assume it has nothing to do with the RAM but more with the fact that it was off the power supply for a while).

Since, I have been too scared to use hibernation again on ubuntu. Is this a known problem? Or just incredible bad luck?

Thanks again for your help... and sorry for asking so many things

-theo

---

### Post by true_friend on 2007-03-06
a) I think it is not bad. Automatix can be used with care but it certainly creates some problems for system while upgrading but i overcame it through one by one use of synaptic, apt-get and Adept i downloaded and installed every package which was told me any of them as available for upgrade. apt-get do not work while upgrading it says following packages are upgradeable but old  will be kept back. synaptic then solves the problem this was the only problem in go
Regards
True_Freind

---

