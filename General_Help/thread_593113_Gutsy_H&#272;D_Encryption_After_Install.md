---
title: "Gutsy H&#272;D Encryption After Install?"
date: 2007-10-26
forum: General Help
---

### Post by zaphod777 on 2007-10-26
is there a way to encrypt the H&#272;D in gutsy after the install? I don't really want to do a fresh install.
Thanks,
Nick

---

### Post by mahousaru on 2007-10-26
This guide should still work

[http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml)

---

### Post by zaphod777 on 2007-10-26
thanks i hope i don't hose it.

---

### Post by mahousaru on 2007-10-26
Hee hee backup!!!!

---

### Post by zaphod777 on 2007-10-27
don't worry I have my *cough* videos on an external. :-P

does the size of the partitions particularly matter? i just went with the defaults before but the guide has them listed totally different.

---

### Post by mahousaru on 2007-10-27
No matter which type* of encryption you go for all you really need is an unencrypted boot, which I personally set at 200MB (either the ubuntu guide or one of the suse guides went for that and I blindly followed :p).

*The guide goes for single encrypted partitions, but you can also encrypt a LVM partition with all of your other partitions residing in it.  I'm not too sure about LVM to be honest, as a while back when I was looking at it, it was a bit of a pig to recover from a hdd corruption, but things change so quickly it could all be nice and easy.  Anyway the main rule of thumb I personally follow is I back up my encrypted laptop every chance I get, as encrypted data is too fragile.

---

### Post by zaphod777 on 2007-10-27
Okay this is my current partition setup which looks to not be optimal how would you suggest I adjusted this?

/dev/sda1/  EXT3        35.69 GB             Boot
/dev/sda3/  Extended        1.57 GB               
     /deev/sda5/ Linux-Swap  1.57 GB

---

### Post by mahousaru on 2007-10-27
If I read that correctly then I would say that 39 GB is rather excessive for boot.  I would stick with 200MB which should give u plenty of room for any kernel updates.  I am guessing the 39 GB with just what you had previously for / (root)

next u need to decide if you want to encrypt all your linux partitions with lvm and a single password.  or if you want to do partitions with their own passwords.  with lvm you only need a single password and you can resize the partitions residing within the lvm.  with single partitions that are encrypted it is easier to access data from a live cd or reinstall.  can't say for lvm as i haven't tried it yet.

I personally always have home split off from /.  depending on what you store under / you will need at least 3GB for it.  For example on my server I split off opt, tmp and var, which means unless i am installing lots of programs my / hardly grows on it.  but i think this is OTT for a desktop.

My lappie is as follows

/boot 200MB
/ 20 GB
/home 30 GB
swap 4GB
spare partition 25GB

My root fully installed is currently @2.9gb, but it will grow as tmp and var reside on this partition.

it really is up to your own personal preference.  The only hard rules are:

boot must come first (may no longer be the case, but i haven't tried otherwise) and must be un-encrypted.
at least 3GB for /
swap is recommended at double ram


if you have trouble deciding on sizes i recommend going for encrypted partition with lvm residing on it. that way u can resize as you wish at a later date.

I think it will be easier to do a reinstall then to try to re do your drives.

This link was recommended by someone on another thread which explains how to do encryption with lvm

[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

---

### Post by zaphod777 on 2007-10-27
yeah it looks like it will just start from scratch and do the encryption from the start. I can do that from the standard Gutsy live DVD Right? 

Backing up my data I pretty much backup Home right? have simple backup installed.

---

