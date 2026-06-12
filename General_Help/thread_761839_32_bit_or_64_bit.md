---
title: "32 bit or 64 bit"
date: 2008-04-21
forum: General Help
---

### Post by MosMusy on 2008-04-21
how do I find out if my firefox is 32-bit or 64 bit?

---

### Post by kbless7 on 2008-04-21
Are you using 32 bit or 64 bit ubuntu. You can't run 64 firefox in 32 ubuntu. BTW flash is only 32 bit now...referring to your other thread.

---

### Post by MosMusy on 2008-04-21
How do I found out if I am using 32 bit or 64 bit for ubuntu then?

---

### Post by overdrank on 2008-04-21
> **MosMusy said:**
> How do I found out if I am using 32 bit or 64 bit for ubuntu then?

Use the command ```
 uname -a
``` in the terminal and this is a example
~$ uname -a
Linux overdrank-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 **x86_64** GNU/Linux

---

### Post by kbless7 on 2008-04-21
Did you install ubuntu marked as AMD 64 or just the regular x86?

---

### Post by MosMusy on 2008-04-21
> **overdrank said:**
> Use the command uname-a in the terminal and this is a example
~$ uname -a
Linux overdrank-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 **x86_64** GNU/Linux

the terminal does not recognize the command

---

### Post by kbless7 on 2008-04-21
copy this into the terminal exactly. don't change anything

```
uname -a
```

---

### Post by MosMusy on 2008-04-21
> **kbless7 said:**
> copy this into the terminal exactly. don't change anything

```
uname -a
```
:
I got this

Linux movses-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by lizzard on 2008-04-21
You have a 32 bit system (i686), that means your firefox is 32 bit too.

---

### Post by MosMusy on 2008-04-21
> **lizzard said:**
> You have a 32 bit system (i686), that means your firefox is 32 bit too.
in terms of getting the flash plugin, how does that affect me?

---

### Post by CREEPING DEATH on 2008-04-21
> **MosMusy said:**
> in terms of getting the flash plugin, how does that affect me?

Flash should "just work"

CD

---

### Post by phidia on 2008-04-21
> **MosMusy said:**
> in terms of getting the flash plugin, how does that affect me?

You should be able to use the [package manager]("https://help.ubuntu.com/community/SoftwareManagement") to install flash.

 [Your other thread]("http://ubuntuforums.org/showthread.php?t=761532&highlight=flash+plugin&page=2") on this problem contains a response with a method for getting flash installed. 
Apparently there are problems with flash because there has been a recent update (?) by adobe and they  don't consider compatibility for linux/unix users a high priority. 

The [adobe flash site]("http://www.adobe.com/shockwave/download/alternates/") does contain a linux download. Perhaps one of those methods will work?

---

### Post by MosMusy on 2008-04-21
> **phidia said:**
> You should be able to use the [package manager]("https://help.ubuntu.com/community/SoftwareManagement") to install flash.

 [Your other thread]("http://ubuntuforums.org/showthread.php?t=761532&highlight=flash+plugin&page=2") on this problem contains a response with a method for getting flash installed. 
Apparently there are problems with flash because there has been a recent update (?) by adobe and they  don't consider compatibility for linux/unix users a high priority. 

The [adobe flash site]("http://www.adobe.com/shockwave/download/alternates/") does contain a linux download. Perhaps one of those methods will work?

Thank you so much! The flash finally worked! Thanks for the adobe link. Pass that on so people like me don't pull hair#-o when trying to install flash. 

You made my day, thanks.=D>\\:D/

---

