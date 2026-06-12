---
title: "Problem after upgrade - everything is 'Read Only'"
date: 2008-01-09
forum: General Help
---

### Post by Floren on 2008-01-09
Ubuntu 6.06.1 LTS - Dapper Drake
2.6.15-29-amd64-generic

Hi all,

I just performed a routine remote upgrade (sudo apt-get update / sudo apt-get upgrade). Apparently everything went ok, but after a while I began having problems. I can write or change any file cause the all seem to be "read only".

I have restarted a few times and the problem persists. Furthermore, if I run some programs, the remote connection just freezes and I have to reconnect again.

Any suggestion?

    Floren

---

### Post by dcstar on 2008-01-09
> **Floren said:**
> Ubuntu 6.06.1 LTS - Dapper Drake
2.6.15-29-amd64-generic

Hi all,

I just performed a routine remote upgrade (sudo apt-get update / sudo apt-get upgrade). Apparently everything went ok, but after a while I began having problems. I can write or change any file cause the all seem to be "read only".

I have restarted a few times and the problem persists. Furthermore, if I run some programs, the remote connection just freezes and I have to reconnect again.

Any suggestion?

    Floren

If the root filesystem has errors then it will be mounted read only, and since it seems it cannot fix them automatically then someone needs to boot the system off a Live CD and manually run fsck on that filesystem.

---

### Post by Floren on 2008-01-09
Thanks, the problems is that this computer is about a 1,000 miles away and the people around it is not really computer savvy...

Isn't there anything I could do remotely?

Thanks,

    Floren

---

