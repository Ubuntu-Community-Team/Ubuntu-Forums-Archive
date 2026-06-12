---
title: "cannot remote display VIM GUI to new 12.04.1 LTS install"
date: 2012-12-21
forum: General Help
---

### Post by mvorloff on 2012-12-21
Hello all,

Something totally odd is doing on with my fresh Ubuntu 12.04.1 desktop LTS install. Up until now I used 11.10 and prior versions and never seen anything line this.

So, I am trying to display 'gvim' from the remote server on my desktop. DISPLAY variable is set up properly and X server TCP port on my desktop machine is open. Firewall is disabled.

So I rlogin to server1, set up the DISPLAY variable and run "gvim xyz". Everything is fine, VIM window pops open, no error messages. VIM version is 7.0,  "uname -a" is 
Linux server1 2.6.18-308.1.1.el5 #1 SMP Fri Feb 17 16:51:01 EST 2012 x86_64 x86_64 x86_64 GNU/Linux

Now I login to server2 and try the same thing. VIM is saying "E665: Cannot start GUI, no valid font found" and then opens in a non-GUI mode inside the X terminal.
VIM version is 7.2, "uname -a" is 
Linux server2 2.6.18-308.4.1.el5xen #1 SMP Wed Mar 28 02:14:52 EDT 2012 x86_64 x86_64 x86_64 GNU/Linux

Both servers are running RedHat, and until I installed Ubuntu 12.04.1 LTS on my desktop VIM worked just fine. The font I use in .vimrc is pretty standard I think: "set  guifont=Monospace\ 10"

Has anyone seen anything like that? Any thoughts how I can get VIM on a server2 work properly?

---

### Post by mvorloff on 2012-12-21
I check whether xfs font server was installed... and it wasn't. After I installed it and rebooted problem is gone.

---

