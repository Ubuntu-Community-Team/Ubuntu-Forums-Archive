---
title: "Can I erase ubuntu in dual boot ?"
date: 2008-05-25
forum: General Help
---

### Post by PC-Fool on 2008-05-25
:popcorn:

Well - Can I erase ubuntu again?
I installed in as dual boot (60%vista & 40%ubuntu)

From a Ubuntu 8.4.0 liveCD made as ISO.

I can not use my "Smart Restore" now in Packard Bell EasyNote,
after I installed it as dual boot.
:(:confused:

(Could do it before with wubi installation)
:KS

Will install ubuntu again, after using "Smart Restore"

---

### Post by h4mx0r on 2008-05-25
use a live cd and erase everything in the partition you don't want then resize it with gparted so your using it however you like. Just remember windows installs kills partitions.

---

### Post by PC-Fool on 2008-05-25
Hi h4mx0r;5037363

"use a live cd and erase everything in the partition you don't want then resize it with gparted so your using it however you like. Just remember windows installs kills partitions"

So I can erase ubuntu?
:confused:
Sorry but how exatly do I do it?
I am not familiar with it, yet.

---

### Post by TeoBigusGeekus on 2008-05-25
Go to 
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
and download the gparted live cd. Burn it and boot with it.
After boot up, choose your Ubuntu partition and delete it.
Then choose your window$ partition and resize it. 
You will confront problems with the grub loader after Ubuntu is deleted - go to this page 
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html")
to overcome them. 

[COLOR="Red"]Warning:
Unless you are absolutely certain to have understood all the above mentioned steps, don't proceed or else you won't be able to boot into either vista or linux. Make sure you have a vista installation dvd as well.[/COLOR]

---

