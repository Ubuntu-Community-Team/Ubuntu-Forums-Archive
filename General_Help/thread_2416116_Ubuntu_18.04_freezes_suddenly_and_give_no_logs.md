---
title: "Ubuntu 18.04 freezes suddenly and give no logs"
date: 2019-04-05
forum: General Help
---

### Post by Cayo_Emilio_Montei on 2019-04-05
Hello

I have Ubuntu 18.04 installed in my working computer. All of a sudden, it seems to me that when I use any interface interaction such as clicking somewhere, it freezes. I see that it keeps running my terminal commands, saving in the disk and everything. Only the interface freezes. I tried to wait some hours, but nothing happens. So I have to restart, and when I log in again, there is no logs. I happened twice to me today, one while I was writing this post, but it seems to be random to me. Sometimes it takes one week running (I don't turn off the computer) and sometimes several times in a day like today. 
The specs are: i7-4930K, 64gb of Ram, 2 x 1Tb HDs and a GeForce GT 740 as video card. 
The programs that are usually running are Chrome, terminal, gedit, matlab and a latex editor.

Please, someone can at least help me to track the problem? It is hard to work this way...

Many thanks in advance,

Cayo

---

### Post by dragonfly41 on 2019-04-05
You have quite a powerful configuration with 64Gb of RAM.

I can only suggest trying a process of elimination.

Does the freeze occur in a guest or new user account?

Does the freeze occur if you install [gnome-flashback]("https://www.debugpoint.com/2018/05/how-to-install-classic-gnome-flashback-in-ubuntu-18-04-lts/") and switch to that mode which is less demanding?

Have you tried testing memory?

Do you have many browser tabs / windows open?  Your workflow apps seem to be cpu demanding. Can you shut down and try one app at a time.

[STACER]("https://linuxconfig.org/system-monitoring-on-ubuntu-18-04-linux-with-stacer") is a useful monitoring tool (although there are others such as default system monitor and TOP to inspect running processes).

These are first ideas I would try intuitively.  Then progress to shutting down to remove different banks of RAM (32 Gb + 32 Gb) then reboot.

---

