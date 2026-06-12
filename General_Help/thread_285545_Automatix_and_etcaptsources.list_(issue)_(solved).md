---
title: "Automatix and /etc/apt/sources.list (issue) (solved)"
date: 2006-10-26
forum: General Help
---

### Post by ekravche on 2006-10-26
Hello,

I've installed automatix 2 on edgy and it modified my source.list to contain the following.
> 
#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END

My questing is whether it is normal because in the previous version of automatix it used to ask you whether or not you'd like to remove any repositories that were added to your sources.list by automatix while using automatix? My concern is that by having the above repros, I'll end up upgrading libs and apps that may conflict with the usual edgy repositories. There should be an option in this version of automatix to remove the repositories that are added by automatix from the source.list.

Looking forward to your answer.

Thanx in advance! :)

---

### Post by JimmyJazz on 2006-10-27
> **ekravche said:**
> Hello,

I've installed automatix 2 on edgy and it modified my source.list to contain the following.


My questing is whether it is normal because in the previous version of automatix it used to ask you whether or not you'd like to remove any repositories that were added to your sources.list by automatix while using automatix? My concern is that by having the above repros, I'll end up upgrading libs and apps that may conflict with the usual edgy repositories. There should be an option in this version of automatix to remove the repositories that are added by automatix from the source.list.

Looking forward to your answer.

Thanx in advance! :)

In Automatix goto File -> Remove Automatix Repos...
and they will be removed but on the most part though these repos pose no risk to your system and you probably wanna keep them.

---

### Post by ekravche on 2006-10-28
Thank you for the post.

---

