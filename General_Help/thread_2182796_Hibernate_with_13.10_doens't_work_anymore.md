---
title: "Hibernate with 13.10 doens't work anymore"
date: 2013-10-22
forum: General Help
---

### Post by dobriseb on 2013-10-22
Hi all,

I've just upgrade my ubuntu for 13.10 and the hibernate is no more available (no surprise until here).

I've succesfully tested pm-hibernate and made this changes in /etc/polkit-1/localauthority/50-local.d/com.ubuntu.disable-suspend.pkla :
```
[Disable suspend by default]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend
ResultActive=yes
```
But hibernate menu doesn't appear.

Any idea ?

Seb.

---

### Post by heffo_j on 2013-10-24
Didn't work for me either. I think I read somewhere that Ubuntu has moved away from polkit. Don't quote me and no flames please - it is just a recollection I have after spending days searching for hibernate and suspend solutions.

John

---

### Post by Toz on 2013-10-24
> **dobriseb said:**
> Hi all,

I've just upgrade my ubuntu for 13.10 and the hibernate is no more available (no surprise until here).

I've succesfully tested pm-hibernate and made this changes in /etc/polkit-1/localauthority/50-local.d/com.ubuntu.disable-suspend.pkla :
```
[Disable suspend by default]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend
ResultActive=yes
```
But hibernate menu doesn't appear.

Any idea ?

Seb.

Delete the file you created above and create the file **/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla** with the following content:
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
```

On reboot, the hibernate function is missing from the menu until you:
```
killall indicator-session-service
```
...[bug report here]("https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1232814").

---

### Post by dobriseb on 2013-10-26
Thank you very much, it works.

I'll follow that bug report.

---

