---
title: "Can't shutdown computer"
date: 2007-08-03
forum: General Help
---

### Post by RaZoR1394 on 2007-08-03
Hello.

I can't shutdown my computer normally. When I tell the computer to shutdown it stops at approximately 85% with a blinking underscore in top left corner. Then when I use CTRL-ALT-DEL it continues a bit more , 95% then it stops again with a blinking underscore. What I have to do is ALT-SYSRQ-S, ALT-SYSRQ-U and ALT-SYSRQ-B so it can reboot without any heavy repercussions.

I think there are som bug reports on this issue. Here is one of them:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/117490](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/117490)

First I tried adding "acpi=force" to the boot parameter but It didn't work so I removed that and added "acpi=on nolapic". This didn't work either.

I have this problem on a laptop and on a desktop. I'm not sure but I think these problems started when I started using nfs shares on my fileserver alternatively something with Automatix isn't right because I've messed with that a bit.

I hope someone can help. Bye.

---

### Post by Gremlinzzz on 2007-08-03
Automatix  has a repartition for breaking systems. i would never use it;think you should just do a complete reinstall without Automatix .you can use the halt command in the terminal that might get ya to close a little faster

---

### Post by Gremlinzzz on 2007-08-03
> **Gremlinzzz said:**
> Automatix  has a repartition for breaking systems. i would never use it;think you should just do a complete reinstall without Automatix .you can use the halt command in the terminal that might get ya to close a little faster

the halt command
sudo halt
:guitar:

---

### Post by RaZoR1394 on 2007-08-03
Sudo halt doesn't help and reinstalling isn't really a comfortable option, maybe good as a last resort.

---

