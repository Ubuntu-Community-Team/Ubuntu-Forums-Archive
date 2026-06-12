---
title: "snap-confine has elevated permissions and is not confined but should be"
date: 2022-05-03
forum: General Help
---

### Post by psychohermit on 2022-05-03
Greetings folks,

I'm having problems with snapd. This is what I get launching firefox from CLI. Running ubuntu 22.04

```

snap-confine has elevated permissions and is not confined but should be. Refusing to continue to avoid permission escalation attacks

```

Reinstalling it cures the problem but this is an every boot occurrence and it's a hassle reinstalling, not to mention wear and tear on my ssd.

I would really appreciate it if someone could point out a fix for this.

Thanks in advance,
--glenn

---

### Post by deadflowr on 2022-05-03
Possibly kernel related:.
See: [https://forum.snapcraft.io/t/snap-confine-has-elevated-permissions-error/2391]("https://forum.snapcraft.io/t/snap-confine-has-elevated-permissions-error/2391")

Possible workaround
```
sudo apparmor_parser -r /etc/apparmor.d/*snap-confine*
```

A somewhat related bug report: [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1803476]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1803476")
(Though marked as invalid, it probably contains some useful information.)

---

### Post by psychohermit on 2022-05-03
> **deadflowr said:**
> Possibly kernel related:.
See: [https://forum.snapcraft.io/t/snap-confine-has-elevated-permissions-error/2391]("https://forum.snapcraft.io/t/snap-confine-has-elevated-permissions-error/2391")

Possible workaround
```
sudo apparmor_parser -r /etc/apparmor.d/*snap-confine*
```

A somewhat related bug report: [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1803476]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1803476")
(Though marked as invalid, it probably contains some useful information.)

Didn't help.

Thanks for trying,
--glenn

---

### Post by deadflowr on 2022-05-03
> **psychohermit said:**
> Didn't help.

Thanks for trying,
--glenn

What part? I offered several.

---

### Post by psychohermit on 2022-05-03
```

sudo apparmor_parser -r /etc/apparmor.d/*snap-confine*

```

Thanks,
--glenn

---

