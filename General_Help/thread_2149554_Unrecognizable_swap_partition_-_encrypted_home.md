---
title: "Unrecognizable swap partition - encrypted /home"
date: 2013-05-29
forum: General Help
---

### Post by Juniorr on 2013-05-29
I have noticed that my swap partition is not recognizable, it's due to the /home encryption (see attachment bellow).
How does this affect the partition at all? How to know if it's actually being mounted?

If it's failing to mount, how to fix this?

---

### Post by dino99 on 2013-05-29
Seems that gparted miss luk support; maybe try with partedmagic instead

[http://askubuntu.com/questions/21662/can-i-use-gparted-to-resize-a-truecrypt-encrypted-partition](http://askubuntu.com/questions/21662/can-i-use-gparted-to-resize-a-truecrypt-encrypted-partition)
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)
[http://partedmagic.com/doku.php?id=news](http://partedmagic.com/doku.php?id=news)

---

### Post by HermanAB on 2013-05-29
Howdy,

Everything you ever wanted to know about swap is in the 'swapon' man page.  This totally non-obvious, so now you know.

---

### Post by Juniorr on 2013-05-29
> **dino99 said:**
> Seems that gparted miss luk support; maybe try with partedmagic instead

[http://askubuntu.com/questions/21662/can-i-use-gparted-to-resize-a-truecrypt-encrypted-partition](http://askubuntu.com/questions/21662/can-i-use-gparted-to-resize-a-truecrypt-encrypted-partition)
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)
[http://partedmagic.com/doku.php?id=news](http://partedmagic.com/doku.php?id=news)
But that doesn't mean it's not mounted, right?

---

### Post by Juniorr on 2013-05-29
> **HermanAB said:**
> Howdy,

Everything you ever wanted to know about swap is in the 'swapon' man page.  This totally non-obvious, so now you know.
Not everybody is a geek about everything, you know =)
Of course, this is also so not obvious.

---

### Post by dino99 on 2013-05-29
> **Juniorr said:**
> But that doesn't mean it's not mounted, right?

it is mounted, but gparted does not know about it (red icon flag)
there is nothing scary there; its only a morron gparted

---

### Post by ajgreeny on 2013-05-29
You can see if the system finds your swap and uses it with the command [B]free -m
[/B]The last line of output will say something similar to below.
```
             total       used       free     shared    buffers     cached
Mem:          7683       1412       6271          0         64        718
-/+ buffers/cache:        630       7053
Swap:         8198          0       8198

```

---

### Post by Juniorr on 2013-05-29
> **dino99 said:**
> it is mounted, but gparted does not know about it (red icon flag)
there is nothing scary there; its only a morron gparted
Oh, then it's OK =)

> **ajgreeny said:**
> You can see if the system finds your swap and uses it with the command [B]free -m
[/B]The last line of output will say something similar to below.
```
             total       used       free     shared    buffers     cached
Mem:          7683       1412       6271          0         64        718
-/+ buffers/cache:        630       7053
Swap:         8198          0       8198

```
junior@junior-desktop:~$  free -m
             total       used       free     shared    buffers     cached
Mem:          3954       1525       2428          0         69        617
-/+ buffers/cache:        838       3115
Swap:        10239          0      10239

---

### Post by ajgreeny on 2013-05-29
That is an enormous swap to have (10GB) when you have only about 4GB ram.  Any good reason for that?

I suspect you could shrink the ram partition to 4Gb and manage quite well, even if you like to hibernate.  However if you are not having any difficulties with lack of disk space, you might as well leave well alone, at least until you need to do a reinstallation.

---

### Post by Juniorr on 2013-05-29
> **ajgreeny said:**
> That is an enormous swap to have (10GB) when you have only about 4GB ram.  Any good reason for that?

I suspect you could shrink the ram partition to 4Gb and manage quite well, even if you like to hibernate.  However if you are not having any difficulties with lack of disk space, you might as well leave well alone, at least until you need to do a reinstallation.
I plan to upgrade from 4 to 8GB in a near future, that's why the 10GB partition =)

Well, all seems ok then. I'm marking this one as solved.

---

