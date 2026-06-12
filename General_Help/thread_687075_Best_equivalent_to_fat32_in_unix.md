---
title: "Best equivalent to fat32 in unix"
date: 2008-02-03
forum: General Help
---

### Post by Mr.Johnny on 2008-02-03
Hi!

I don't have the need for access control (it's just a multimedia machine), so I would like to have a partition with a file system that wouldn't bother me with file permissions. 

Anything like that in unix? 

Thanks!

---

### Post by manimal347 on 2008-02-03
Not really. The whole Unix philosophy is based around security, including, but not limited to stern acess controls. After all, Unix was intended to be a distributed academic operating system which powered a computer many people shared through terminals. You could perhaps look up things like ReiserFS, but I really don't see how they'd be in the kernel if they didn't provide for access restrictions. Even if this was possible, it would be dangerous, as your machine would be thoroughly exposed to both malware threats and user stupidity, such as accidentally deleting a system folder.

Sorry. There may be a way around this, like to create a cron job that  makes sure that "everybody" has ownership of all of your harddisk files and that they are told to chmod +rwx so they are usable both you and root.

---

### Post by Mr.Johnny on 2008-02-03
No problem, I understand the whole philosophy behind Unix, just wondering if there would be any workaround. "A computer many people shared" is really what comes to my mind when using linux, but I would really need not to worry about that, for what I'm doing. It's got its advantages and disadvantages, I'm just seeing where it goes.

My goal is to use my vst plugins, running under wine, in an usb disk.

From my experiments so far, it is perfectly possible, although i've been struggling with a much higher cpu load and some registry/access permission issues.

---

