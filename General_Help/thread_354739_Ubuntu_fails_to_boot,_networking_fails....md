---
title: "Ubuntu fails to boot, networking fails..."
date: 2007-02-06
forum: General Help
---

### Post by McLaughysSN on 2007-02-06
Hey guys,

Ubuntu seems to not want to work. During the start up is fails at Starting basic Networking.. and Configuring network interfaces.. Then it just freezes. The networking seemed a little funny before this happened. Any suggestions?.. Sorry about being so broad but im not sure where to go from here, i've never had an issue with boot up.

---

### Post by McLaughysSN on 2007-02-06
bump

---

### Post by McLaughysSN on 2007-02-06
I can get the boot loader to get to the following message now

Starting cluster configuration system: FATAL: Module cman not found
Warning unable to load cman kernel moduleFATAL: Module dlm not found
Warning unable to load dlm kernel modlecman_tool: can't open /pro/cluster/status, cman not running
Starting cluster managercman_tool: can't open /proc/cluster/status, cman not running

Any clue on this one?

Thanks guys

---

### Post by meng on 2007-02-06
I take it this is a HDD-installed system. Did you do anything to it before it went bust like this?

---

### Post by McLaughysSN on 2007-02-06
Yeah, I was editing the /etc/network/interfaces file, not major, just allowing nm-applet to take over.

UPDATE 

after running the disk check, Ubuntu magically worked, even keeping the same processes list as failed on the boot screen. Networking work fine when OS is loaded.

---

