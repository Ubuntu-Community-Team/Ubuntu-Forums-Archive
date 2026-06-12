---
title: "A problem with kernel upgrade"
date: 2008-02-07
forum: General Help
---

### Post by niethslim on 2008-02-07
Earlier today I compiled the 2.6.24 kernel from source and installed the most recent nvidia driver.
It all compiled nicely, but when I restarted the computer I only could use it in low graphics mode.
So obviously I tried to reinstall the nvidia driver a hundred times, and reconfigured some things.
Anyway, now I cant even log in to the graphic interface (it freezes in the middle of the boot).
I can use it in run level 1 (restore mode, I think they call it).
I'll restart and post the exact place it freezes in a bit later.
Edit: it freezes on *running local boot scripts (/etc/rc.local)  
Any help is welcome,

---

### Post by geraldm on 2008-02-07
Unless you have changed /etc/rc.local, it should be a script that contains one command, "exit 0"
There is no reason to believe that would cause a hang.

Changes that I would make to mine, if I were in your position, would be to be sure that the links in that runlevel have only 1 link as S99rc.local and change all other "S99*" links to "S98.." so that rc.local runs last.  If that did not boot, I would change the name of the rc.local script to another name like rc.local.null and then test that.  I also have one runlevel dedicated to command line work, no X server.  That is the greatest test because it does not allow X to interfere with the boot.

Gerald

---

### Post by niethslim on 2008-02-07
Thanks for reply geraldm, especially for the x-server suggestion, it wasn't the x-server but another thing called stop-read$ that needed to be changed, I think.
Now I can login to gnome in low graphics mode.
Any suggestions to how can I make the nvidia driver work? 


Thanks,

---

