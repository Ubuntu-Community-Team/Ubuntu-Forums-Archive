---
title: "Ubuntu 16.04 Not hibernating on HP Pavillion g6 2005tx"
date: 2016-05-02
forum: General Help
---

### Post by johnygeorgemalayil on 2016-05-02
I upgraded to the Ubuntu 16.04, I was able to hibernate on the previous versions (15.10), but this one is not hibernating.
I am running an HP Pavillion g6 2005tx. I get a long black screen when I try to hibernate.

What should I do to fix that ?

---

### Post by ajgreeny on 2016-05-02
In 14.04 you needed to edit and add text to a system file as shown in the thread at [http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403)

Have you tried doing that? I am not aware of changes in 16.04 related to that requirement, but if that does not work come back again and ask.

---

### Post by johnygeorgemalayil on 2016-05-02
This is file /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultActive=yes
```


Its same as in the post, still doesn't work.

---

### Post by ajgreeny on 2016-05-03
In that case I am sorry but I have no idea.

I have not yet moved to 16.04 except as a VM in VirtualBox and I do not need to hibernate that; I'm not even sure if you can hibernate a VM.

---

### Post by neo11 on 2016-05-16
Same proble with hp g6-2221es, wifi no turn on (the led for harware switch not turn white, only orange), and after upgrade not suspend
In ubuntu 15.10 I fix not turn on wireless card with suspend and wake notebook, now after upgrade not work!

Any solution?

Thanks for advance,

BR

> **johnygeorgemalayil said:**
> This is file /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultActive=yes
```


Its same as in the post, still doesn't work.

---

### Post by neo11 on 2016-05-18
I make this file as root and same problem...

Best regards!

---

