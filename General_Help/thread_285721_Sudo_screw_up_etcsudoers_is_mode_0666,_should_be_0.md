---
title: "Sudo screw up /etc/sudoers is mode 0666, should be 0440"
date: 2006-10-27
forum: General Help
---

### Post by titancomputing on 2006-10-27
I just installed Edgy, and I did something kinda stupid. I edited the /etc/ folder to where everyone could have read write access through Konqueror. Problem is, now I know that screws up some major components. Everytime I try to sudo, I get /etc/sudoers is mode 0666, should be 0440. I can't even kdesu to fix the problem, and I need root permissions to change it back to how it was. How do I fix this?

---

### Post by diepruis on 2006-10-27
Reboot into recovery mode. That should drop you to a root shell. Then just do:

```

chmod -R 0440 /etc

```

Reboot using

```

shutdown -r now

```

...and you should be fine.

---

### Post by doctorberen on 2006-11-29
diepruis, help me please.

I have the same problem with sudo. I get the same error message.

However, when I type:
```
 shutdown -r now
```I get this messge:
```
 shutdown: Need to be root
```What do I do next?

---

### Post by RAOF on 2006-11-30
Just restart from the system menu.  You don't need to run **shutdown -r now**, it does exactly the same thing.

---

### Post by diepruis on 2006-11-30
> **RAOF said:**
> Just restart from the system menu.  You don't need to run **shutdown -r now**, it does exactly the same thing.

I believe he booted into recovery mode, as per my post.

Could you tell me what the prompt looks like? Are you in recovery mode?

---

### Post by doctorberen on 2006-11-30
Hello.

I'm not in recovery mode. I'm in my normal (user mode).

---

