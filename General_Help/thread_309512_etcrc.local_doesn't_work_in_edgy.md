---
title: "/etc/rc.local doesn't work in edgy"
date: 2006-11-29
forum: General Help
---

### Post by hexion on 2006-11-29
In dapper, I included some commands in /etc/rc.local to be executed at boot time with root privileges.

Now in edgy, with the same content, some things work and others don't.

My etc/rc.local file contains:
> #!/bin/sh -e
mknod /dev/lirc c 61 0
lircd
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit 0Two first lines are for lirc, and the third is to enable sound in enemy territory game. Ok, lirc works BUT the third command doesn't make any effect. I have to run it with sudo in a terminal :(

Any idea why that doen't work in edgy?
Any other way to run a command as root (important) at my session init?

Thanks

---

### Post by hexion on 2006-11-29
Nevermind...

Just changing #!/bin/sh -e   to #!/bin/bash did the trick...

---

### Post by dcstar on 2006-11-29
> **hexion said:**
> In dapper, I included some commands in /etc/rc.local to be executed at boot time with root privileges.

Now in edgy, with the same content, some things work and others don't.

My etc/rc.local file contains:
Two first lines are for lirc, and the third is to enable sound in enemy territory game. Ok, lirc works BUT the third command doesn't make any effect. I have to run it with sudo in a terminal :(

Any idea why that doen't work in edgy?
Any other way to run a command as root (important) at my session init?

Thanks

I'm wondering if it is a timing issue with Edgy processing the rc.local commands before the various /proc stuff has established (where previously it was diffetent).

---

### Post by hexion on 2006-11-30
> **dcstar said:**
> I'm wondering if it is a timing issue with Edgy processing the rc.local commands before the various /proc stuff has established (where previously it was diffetent).

That makes sense... but then why does it work just changing sh to bash? :-k

---

### Post by superm1 on 2006-12-05
This is probably caused by the bash-> dash change more so then an order of processing commands.

---

