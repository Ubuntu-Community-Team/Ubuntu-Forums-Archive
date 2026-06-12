---
title: "VMWare-Player"
date: 2006-09-10
forum: General Help
---

### Post by jmonteiro on 2006-09-10
I am trying to install vmware-player in a fresh install of Ubuntu 6.06.1.

I recieve alwayis the following error:

> Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: erro processando vmware-player (--configure):
 subprocesso post-installation script retornou código de saída de error 1
Erros foram encontrados durante processamento de:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have already tryied reinstalling, removing and purging, but I alwayis recieve this message.

Do anybody know what is this?

Thanks!

---

### Post by tuxinvader on 2006-09-10
Have you also installed vmware-player-kernel-modules-2.6.15-26 or the right version for your kernel?

---

### Post by jmonteiro on 2006-09-10
tuxinvader, this is exactaly the problem. It is installed the kernel 2.6.15-26 (the lattest), but there are only modules for kernel 2.6.15-23 (the vmware-player-kernel-modules-2.6.15-23 package). I installed the 2.6.15-23 kernel, rebooted in it and retryed to reinstall vmware, and it worked!

Thanks for the attention :-)

---

### Post by jongkind on 2006-09-10
I had the same problem. I decided to install it via Automatix which went well.

---

