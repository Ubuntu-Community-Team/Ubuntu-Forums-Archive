---
title: "Accidentally deleted sources.list.d"
date: 2013-11-26
forum: General Help
---

### Post by sydney2 on 2013-11-26
Hello There

Well I made a clumsy mistake. I deleted the sources.list.d accidentally while accessing the folder to delete a file of a previously added ppa rep. I went through some of the previous posts but did not find any solution. Is there a way to restore it back or generate it ?

---

### Post by ian-weisser on 2013-11-26
To be clear:
/etc/sources.list is a file that records the current Ubuntu repositories.
/etc/sources.list.d is a directory (not a file) that users add separate list files into. When you installed Ubuntu, the directory was empty.

Is there a way to restore it? Depends how you deleted it. Often not.
Do you have backups?
Is there a way to regenerate it? I doubt it. The system expects the human admin to track important non-ubuntu software.

In mine, for example, you can see old (obsolete) PPAs, dropbox, netflix, and Google Talk. Yours would depend entirely upon what non-Ubuntu software you installed since your last release-upgrade.
```
g$ ls /etc/apt/sources.list.d/
ansgar-43-1-ppa-karmic.list
ansgar-43-1-ppa-karmic.list.distUpgrade
ansgar-43-1-ppa-karmic.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
ehoover-compholio-quantal.list
ehoover-compholio-quantal.list.distUpgrade
ehoover-compholio-quantal.list.save
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
lernid-devs-lernid-releases-karmic.list
lernid-devs-lernid-releases-karmic.list.distUpgrade
lernid-devs-lernid-releases-karmic.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
minetestdevs-stable-quantal.list
minetestdevs-stable-quantal.list.distUpgrade
minetestdevs-stable-quantal.list.save

```

---

### Post by oldfred on 2013-11-27
You can try this:

 Ubuntu Sources List Generator
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by heir4c on 2013-11-27
If you delete a file/folder, it will normally in the Trash. Is it there?

---

