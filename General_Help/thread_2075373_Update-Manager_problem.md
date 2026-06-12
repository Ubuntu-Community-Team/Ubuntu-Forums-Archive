---
title: "Update-Manager problem"
date: 2012-10-23
forum: General Help
---

### Post by hgergo on 2012-10-23
Hello
I have noticed an interesting problem whith update-manager
Since the relase of QQ i have upgraded my system form LTS.
Until today i don't got updates.
For curiousity i have run apt-get update from terminal and after than the update notification showed up that i have updates.
I noticed that update-manager is not searching for updates automaticaly.
My setting are the following: Search for updates - Daily, Update Server - Main Server and show critical/normal updates set on imediatly.
Somebodi hase noticed the same problem?
Or somebodi hase a solution for it?

---

### Post by dino99 on 2012-10-23
the web is fullfilled with update-manager issues, better to use synaptic

---

### Post by plucky on 2012-10-24
> **hgergo said:**
> Hello
I have noticed an interesting problem whith update-manager
Since the relase of QQ i have upgraded my system form LTS.
Until today i don't got updates.
For curiousity i have run apt-get update from terminal and after than the update notification showed up that i have updates.
I noticed that update-manager is not searching for updates automaticaly.
My setting are the following: Search for updates - Daily, Update Server - Main Server and show critical/normal updates set on imediatly.
Somebodi hase noticed the same problem?
Or somebodi hase a solution for it?

Only security updates will be notified on a daily basis,all other (recommended) updates will be notified on a weekly basis.

This behaviour was changed a while back (can't remember when).


Good Luck

---

### Post by UltimateCat on 2012-10-24
Keeping a good updated etc/apt/sources.list is a good practice to ensure that you get the updates you need. Also; a few http: backports can be helpful in the multimedia area.

When updates for your distro come available your update manager should alert you to distro updates, security updates and updates for your software.

Have a great day!

---

### Post by hgergo on 2012-10-24
> **plucky said:**
> Only security updates will be notified on a daily basis,all other (recommended) updates will be notified on a weekly basis.

This behaviour was changed a while back (can't remember when).


Good Luck

The recommanded updates was set to daily to

---

