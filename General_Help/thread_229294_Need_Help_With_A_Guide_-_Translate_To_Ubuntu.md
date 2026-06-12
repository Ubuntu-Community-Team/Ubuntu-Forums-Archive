---
title: "Need Help With A Guide - Translate To Ubuntu"
date: 2006-08-04
forum: General Help
---

### Post by OffHand on 2006-08-04
Hi all,

I have tried the following guide to use xmms infopipe with bmp (beep media player).

[http://www.beastwithin.org/users/wwwwolf/code/xmms/xmms-infopipe-1.3-for-beepmp.patch.gz](http://www.beastwithin.org/users/wwwwolf/code/xmms/xmms-infopipe-1.3-for-beepmp.patch.gz)

Yet I am already stuck at the second step: - Apply this patch.

Could anyone translate this guide into a Dapper guide?

---

### Post by Ramses de Norre on 2006-08-04
Just do what they say.. You should have a file xmms-infopipe-1.3-for-beepmp.patch.gz and you need to execute those commands with the right path to that file.

---

### Post by OffHand on 2006-08-04
> **Ramses de Norre said:**
> Just do what they say.. If that worked I wouldn't post here for help ;)

---

### Post by Ramses de Norre on 2006-08-04
Then tell us what goes wrong when you execute the commands..

---

### Post by OffHand on 2006-08-04
~$ cd xmms-infopipe-1.3
xxxxx@dapper:~/xmms-infopipe-1.3$ gunzip ../xmms-infopipe-1.3-for-beepmp.patch.gz
gunzip: ../xmms-infopipe-1.3-for-beepmp.patch.gz: No such file or directory

---

### Post by wombat20 on 2006-08-04
Looks like you've got too many dots at the start of your command. try this:
```
gunzip ./xmms-infopipe-1.3-for-beepmp.patch.gz
```

../ means "in the parent of this directory", whereas:
./ means "in THIS directory".

Hope that helps.

---

### Post by OffHand on 2006-08-04
> **wombat20 said:**
> Looks like you've got too many dots at the start of your command. try this:
```
gunzip ./xmms-infopipe-1.3-for-beepmp.patch.gz
```

../ means "in the parent of this directory", whereas:
./ means "in THIS directory".

Hope that helps.
Nope, same error. I cannot find the dam file.

---

### Post by wombat20 on 2006-08-04
Are there any .gz files in the directory that look similar - could you try those?  Do a search for *.gz or just type ls in the directory.

---

### Post by OffHand on 2006-08-04
I managed to get it working with bmp  :)
I can write a how-to if anyone is interested?  :-P

---

