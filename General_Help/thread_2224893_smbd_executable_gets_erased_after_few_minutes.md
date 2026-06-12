---
title: "smbd executable gets erased after few minutes"
date: 2014-05-18
forum: General Help
---

### Post by philippeM on 2014-05-18
I am having a rather puzzling issue which started very recently.
I have the 12.04 LTS pretty much up-to-date. A little while ago (few weeks, don't know exactly), something happened with samba.
I discovered that the smbd executable disappeared from /usr/sbin . I re-intalled. Few minutes after re-starting, the dameon disappeared again.
I made the file non-writable, same thing !

The messages are like this :


[  369.254426] init: smbd main process (2891) killed by KILL signal
[  369.254448] init: smbd main process ended, respawning
[  369.258026] init: Failed to spawn smbd main process: unable to execute: No such file or directory

After the KILL, the file is gone.

Anyone has ever seen anything like this ?

Thanks,
Philippe

---

### Post by realmkeeper on 2014-08-03
Hi Philippe 

Did you get samba back up again? I'm sitting with a similar problem, but I have a compromised system that does not want to play nice.

I have a suspicious hidden file in my /tmp/ directory named .flush and even with sysdig I cannot see what deletes the smbd and nmbd binaries.

---

