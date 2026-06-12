---
title: "Hey when I try to install something my authorization prompt doesn't show up"
date: 2013-04-17
forum: General Help
---

### Post by EliteNeophyte on 2013-04-17
The title clearly explains the problem, when trying to install a package, either directly, through an installer, the package manager, or the software center, I am told that propper authorization was not provided, but I was never prompted to authorize, halp

---

### Post by ibjsb4 on 2013-04-17
You may be missing polkit-1

[https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/758592](https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/758592)

[https://bugs.launchpad.net/ubuntu/+source/qapt/+bug/875657](https://bugs.launchpad.net/ubuntu/+source/qapt/+bug/875657)

Found that here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=proper+authorization&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=proper+authorization&sa=Search&cof=FORID:9)

---

### Post by EliteNeophyte on 2013-04-18
Strangely enough after a couple of hard reboots (my shutdown command in the gui also wasn't working) and trying to get the caches to clear the problem seemed to sort itself out (bear in mind I had tried restarting) the packages installed without issue, I entered shutdown into the console followed by a couple of options.... think they were -Hhfrv, though I could be wrong, probably am, after a reboot that way the shutdown command worked from the gui, after that I did a standard restart, tried installing the package again and it worked fine

confused but functional

---

### Post by dabl on 2013-04-18
> **EliteNeophyte said:**
> Strangely enough after a couple of hard reboots (my shutdown command in the gui also wasn't working) ...

If by "hard reboots" you mean you pushed the reset button, please don't do that any more -- it is extremely rare that the system is so hung up that killing power is necessary.  Moreover, you are giving the ext4 filesystem a stress test every time you do it, and sooner or later you'll probably break it.

Linux includes an emergency reset capability known as [**[color=green]"magic sysrq"[/color]**](http://en.wikipedia.org/wiki/Magic_SysRq_key) (System Request) key combination.  Next time you think you can't shut down normally, wait two minutes for whatever is going on with the filesystem to settle, and then press Alt-SysRq (the "print screen" key) and while holding those keys down, press R  S  E  I  U  B in slow sequence.  Your system will sync the disk(s) and do a graceful shutdown and reboot.

"_R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring"

;-)


And, next time you want to use muon to install software, try Alt-F2 "kdesudo muon" with no quote marks.

---

