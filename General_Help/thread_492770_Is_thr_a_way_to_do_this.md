---
title: "Is thr a way to do this ?"
date: 2007-07-05
forum: General Help
---

### Post by ss0007 on 2007-07-05
Hi ,

Recently , when I opened the Update notifier in Ubuntu, I noticed an update for adobe acrobat. The download size was approx 11MB. But , I wanted to keep the current version and use it. Hence , I have to uncheck the adobe acrobat and update the remaining packages. Now, I dont want to do this everytime . There are also other packages which I dont wish to get an update. So ,how can I disable specific package from being updated from the repo's every time I do "sudo ap-get update" ?

thanks in advance ,

---

### Post by Stephen Howard on 2007-07-05
Its called 'pinning' or 'locking', and it allows you to stop upgrades of a package that matches a certain criteria.

You can specify it manually by editing/creating /etc/apt/preferences.  For further information on the format of the file, type "man apt_preferences".   Alternatively, you can use a package installation program such as Synaptic to do it for you - look under Synaptic's Package | Lock menu while your cursor is highlighting the installed application you want to pin at its current version.  Other installers will no doubt have a similar mechanism.

---

