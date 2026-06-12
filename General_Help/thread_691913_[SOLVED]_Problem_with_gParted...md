---
title: "[SOLVED] Problem with gParted.."
date: 2008-02-09
forum: General Help
---

### Post by geo909 on 2008-02-09
Hello everybody, I have a strange problem with gparted, would really appreciate a little help:

I have an external USB Hard drive which is formatted in NTFS.
Well, the thing is that when I am trying to handle it with gparted, 
It appears that it is not formatted and it's full of unlocated space, 
when definitely this is not the case! 
That's not the first time which I had this problem, it was the same for a USB stick I have...

 To be more clear, I uploaded a screenshot which I think shows clearly the problem:
[IMG][[IMG]http://www.imageshack.gr/files/3z5el89sz028uy0l3jmo.png[/IMG]](http://www.imageshack.gr/view.php?file=3z5el89sz028uy0l3jmo.png)[/IMG]

Any ideas why this is happening and how can I fix it?
Is this a bug of gparted?!

---

### Post by PmDematagoda on 2008-02-09
Install the ntfs-progs package using:-
```
sudo apt-get install ntfs-progs
```
then see if Gparted can see the NTFS volume properly.

---

### Post by geo909 on 2008-02-09
> **PmDematagoda said:**
> Install the ntfs-progs package using:-
```
sudo apt-get install ntfs-progs
```
then see if Gparted can see the NTFS volume properly.

Hmmm..
No such package:

```

jorge@jorge-desktop:~$ sudo apt-get install ntfs-progs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-progs
jorge@jorge-desktop:~$ 

```

Any idea?

---

### Post by PmDematagoda on 2008-02-09
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by PmDematagoda on 2008-02-09
Sorry, I made a bit of a typo previously, the command is:-
```
sudo apt-get install ntfsprogs
```

---

### Post by geo909 on 2008-02-09
Haha, yeah, I found it something like 1 minute before your post!! =D

Yes, that did the job. gparted works fine!!


I wonder if that fixes some other related problems I had... Hope it does!
Thanks a lot, PmDematagoda.

---

