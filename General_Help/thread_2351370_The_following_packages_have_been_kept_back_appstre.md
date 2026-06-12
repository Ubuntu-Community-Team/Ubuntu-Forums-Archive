---
title: "The following packages have been kept back: appstream"
date: 2017-02-02
forum: General Help
---

### Post by sccjono on 2017-02-02
Hello all,

I recently started getting this warning after running a 'sudo apt update && sudo apt upgrade'. If I understand it correctly, this is caused by the system holding back an upgraded package because newer dependencies are required as well yes? In the past when this warning has appeared I have happily manually installed the package thus forcing the upgrade but I am reticent on this occasion. Recently there was a bug affecting the appstream metadata and it was fixed by following some advice on here I now cannot locate. What are your thoughts, should I go ahead and force this install or should I just ignore this warning?

Thanks as always,
jono

---

### Post by #&amp;thj^% on 2017-02-02
Have you had a look at what it wants to update?
```
sudo apt update
sudo apt dist-upgrade -s
```
The dist-upgrade will not take you to another OS version it just updates all on your current system... the tailing -s marks it as a dry run  or simulation of the process.

---

### Post by oldos2er on 2017-02-02
Thread moved to *General Help*

---

### Post by deadflowr on 2017-02-02
You can now downgrade the package back to the -updates version, from the -backports version.
The bug was fixed and the updated fix is now in xenial-updates.

To downgrade:
```
sudo apt install appstream/xenial-updates
```
The bug: [https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498]("https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498")

> Have you had a look at what it wants to update?
The new -backports version goes too far for the version of gnome-software (it requires gnome-software 3.22 but xenial only has 3.20-stuff)

---

### Post by sccjono on 2017-02-05
Ah thanks for the advice. It looks like I didn't haven't have to do anything as it has been upgraded automatically. I appreciate the advice for the future though.

jono

---

