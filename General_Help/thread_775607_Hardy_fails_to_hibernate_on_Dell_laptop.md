---
title: "Hardy fails to hibernate on Dell laptop"
date: 2008-04-30
forum: General Help
---

### Post by EliBaskin on 2008-04-30
I am having a problem to hibernate/suspend with 8.04 (had the same problem with 7.10). I am on Dell Inspiron 6400.

I've found a solution on [this site]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/"), installing uswsusp, however when I try to do sudo s2disk or sudo s2both, I get a black screen with two rows, one about splash screen, and the other that says hibernation in process (or something to that extent, don't remember the exact sentence). However, nothing happens - the HD light blinks for a while, and it doesn't change even after 10 minutes.

Is there a solution? This is a big problem, since I am on a laptop, and I don't want to get back to Windows... :(

---

### Post by astadolfo3 on 2008-05-08
Yap! same for me! Vaio VGN SZ450. suspend and hibernate worked great up to 7.04, then stopped working on 7.10 and the upgrade to 8.04 didn't solve the problem. There must be a solution since it worked great on past versions! Suspend and hibernate is vital to me to say the least.

I tried also uwsusp, but when I put the log level higher, it hangs on "suspending console(s)", then I have to do a painfiul hard powerdown.

Please help!!

---

### Post by mfb52 on 2008-05-18
Me three! Same problem here, one of many introduced by Hardy actually :(

---

### Post by fragos on 2008-05-18
I've a Dell Inspiron 1420n. Hybernate in 7.04 and 7.10 didn't work, couldn't restart wireless, but it does in 8.04. This may be impacted by which wireless and video you have. My video is Intel X3100 and my WiFi is also Intel.

---

### Post by jahvascriptmaniac on 2008-05-20
Same problem here, I see the "[37.773161] suspending console(s)" linne.
I'm not on a laptop, and I have a nvidia GeForce (same problem even if I unload the module), and a D-Link PCI wireless adapter (atheros chipset).
Indeed, since hardy, it seems that extra features from my atheros were detected.

---

### Post by fragos on 2008-05-20
Perhaps I spoke to soon. Hibernate failed to restart my wireless today. It came up as a wired which has no physical connection. I was however able to restart networking by righ clicking the networking icon and disabling then enabling networking which came up as my wireless. Past releases had this problem but wouldn't restart the network unless rebooted.

---

