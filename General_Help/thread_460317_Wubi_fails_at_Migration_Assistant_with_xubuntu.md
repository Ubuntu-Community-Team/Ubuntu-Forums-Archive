---
title: "Wubi fails at Migration Assistant with xubuntu"
date: 2007-05-31
forum: General Help
---

### Post by piers on 2007-05-31
Hi,

I dont know if this is a bug, but when installing xubuntu via wubi all goes well until the Migration Assistant kicks in, I get an error message saying tha /dev/hda1 cannot be unmounted. If i ignore it and complete the rest of the tasks and finnish the install i get a kernal panic (something about syncing)

I have tried the latest installer from the minefield and the standard test3 installer, both fail at the mgration assistant. I'm using an i386 xubuntu alternate iso downloaded recently from the canonical mirrors.

Am i doing something wrong? I couldnt find anyone else reporting the same issue.

---

### Post by ago on 2007-05-31
Can you send me the content of /var/log/syslog?

You can save it to the file to the windows partition (/media/host)  by entering into console with alt+f2 after the error happens.

---

### Post by piers on 2007-05-31
I'm just installing with all the migration assistant options commented out in the preseed.cfg, seems to be going better now.
I'll reinstall again though if you still want a copy of that syslog

---

