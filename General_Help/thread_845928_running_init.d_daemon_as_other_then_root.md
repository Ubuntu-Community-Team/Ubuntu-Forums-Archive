---
title: "running init.d daemon as other then root"
date: 2008-07-01
forum: General Help
---

### Post by peterlauri on 2008-07-01
Hi,

I want to run a daemon as someting else then root. In redhat environment I have used a common tool for handling daemons, basically functions for starting and stopping scripts.

In Ubuntu there is the /lib/lsb/init-functions that I noticed. However, I miss a functionality that I can run a daemon as a different user.

Is there any common way to start a daemon as something else then root? I cannot chroot, as I need access to whole file system. But I am a bit concerned of security, as the daemon is not really tested well, and I want a limited user to run it.

The daemon is perl based...

I tried this in my init script:

su - theuser

But the problem is that it then gets into that prompt, and doesn't continue with the execution of the rest of the init script.

Thanks,
Peter

---

### Post by sisco311 on 2008-07-01
You can run a command as a different user with sudo:
```
sudo -u username command
```
I'm not 100% sure if this will work in the init script.

---

