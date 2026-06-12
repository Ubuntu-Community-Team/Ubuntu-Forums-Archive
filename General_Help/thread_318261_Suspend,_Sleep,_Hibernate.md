---
title: "Suspend, Sleep, Hibernate"
date: 2006-12-13
forum: General Help
---

### Post by golem3 on 2006-12-13
I run 6.06 Dapper Drake on my Acer Travelmate c314xmi (c310 series). I do not have the options for sleep (or is it suspend?). I have the hibernate button, but it is broken, and seems to do exactly the same thing as Lock Computer. 

**I would like to know how to enable Sleep.** I don't really care about Hibernate that much, but any help is greatly appreciated.

Thanks in advance.

BTW - I know the Sleep/Suspend feature should work since I remember seeing it  when I booted to Live CD, before I installed Dapper on my hard drive.

---

### Post by wpshooter on 2006-12-13
Are you using Ubuntu/Gnome interface or KDE ?

---

### Post by golem3 on 2006-12-14
> **wpshooter said:**
> Are you using Ubuntu/Gnome interface or KDE ?

Ubuntu GNOME. Isn't Ubuntu KDE called Kubuntu?

Anyway, help on Sleep/Suspend is greatly appreciated.

---

### Post by strabes on 2006-12-14
I also have this problem. I cannot get my computer to suspend or hibernate. My swap partition is 2 gigs. I get this message after I try to suspend or hibernate and it doesn't:

> Message from syslogd@alex-laptop at Thu Dec 14 13:06:50 2006 ...
alex-laptop kernel: [17181029.396000] unregister_netdevice: waiting for eth1 to become free. Usage count = 1

---

### Post by golem3 on 2006-12-14
bumpity bump bump, bump.

---

### Post by golem3 on 2006-12-18
> **golem3 said:**
> bumpity bump bump, bump.

bonus bumpity bumping

---

### Post by Rumpanzle on 2006-12-23
Try to open gconf-editor (shell, or ALT-F2 gconf-editor) and then go to /apps/gnome-power-manager/check_type_net and untick this for a test. At least it sounds like the right thing.

---

### Post by golem3 on 2006-12-25
> **Rumpanzle said:**
> Try to open gconf-editor (shell, or ALT-F2 gconf-editor) and then go to /apps/gnome-power-manager/check_type_net and untick this for a test. At least it sounds like the right thing.

Thanks for your reply, Rumpanzle. 

It however did not work. I switched over to Edgy, and the problem is even worse! Now, when I attempt to shut-down, the X-server reboots on its own.

---

### Post by thor918 on 2007-01-19
make a shortcut that execute this command:
[http://ubuntuforums.org/showthread.php?p=2032330#post2032330](http://ubuntuforums.org/showthread.php?p=2032330#post2032330)

---

