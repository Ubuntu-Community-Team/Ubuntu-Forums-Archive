---
title: "Disk usage analyzer question"
date: 2015-11-20
forum: General Help
---

### Post by ra7411 on 2015-11-20
This is probably a newbie question.

My 2tb HD is more filled up than I would have expected.
Here's a pic of my disk usage. 
My question is: is media/ra/25---long alphanumeri..de0d  an additional storage to what's in home/ra ?

Can media/ra/25---long alphanumeri..de0d be deleted along w/ the other 2, or will that delete all the files I actually use?

Thanks

---

### Post by ian-weisser on 2015-11-20
Check that files in /media are really on your hard drive. Usually /media is used to mount filesystems on other *media*. Like external drives or across a network.
System-critical (OS) files are never on /media .
If a file has erroneously been put on your hard drive in /media, and you are not using it, then you can safely delete it.
Be very sure that you know where the file is really located before you delete it.

---

### Post by Topsiho on 2015-11-21
Generally, before removing a file completely, it is better to just rename it, adding -old or something like that to it's name. If after that everything still "works" then you may remove this file completely.
That's far less fuss then after discovering you deleted a file that you need. You can then fix this by renaming the file to it's former name again.

Just my two euro cents :)

Topsiho

---

