---
title: "Jockey finally kicks in on new 12.04.2 with JFS"
date: 2013-02-20
forum: General Help
---

### Post by ventrical on 2013-02-20
I had yet to see jockey actually work at all with nvidia drivers (and Ati for that matter also) , but, this time it actually worked after a clean install of 12.04.2 using the JFS file system  format. This is the first time I have seen this happen in a long time.

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

 I am just curious as to why it will not work with ext4 or other.

---

### Post by wildmanne39 on 2013-02-20
*Thread moved to **General Help**.*

---

### Post by ventrical on 2013-02-20
So we are no longer Beta testing 12.04.2?

---

### Post by dino99 on 2013-02-20
> **ventrical said:**
> So we are no longer Beta testing 12.04.2?

12.04 is not u+1 as i know nowadays  ):P so the move done  ;)

---

### Post by grahammechanical on 2013-02-21
@ventrical

I thought for a moment that you had been jailed. :) I am glad to see that you are still in circulation. It seems that the town marshals are very zealous.

I thought that we weren't using jockey any more.

[http://www.muktware.com/3952/new-interface-installing-drivers-ubuntu-1210]("http://www.muktware.com/3952/new-interface-installing-drivers-ubuntu-1210")

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html")

Regards.

---

### Post by kurt18947 on 2013-02-21
> I thought that we weren't using jockey any more.

I thought the same unless jockey were moved/renamed/blended into something else.  Its function is now in software sources > additional drivers.

---

### Post by dcstar on 2013-02-21
> **ventrical said:**
> I had yet to see jockey actually work at all with nvidia drivers (and Ati for that matter also) , but, this time it actually worked after a clean install of 12.04.2 using the JFS file system  format. This is the first time I have seen this happen in a long time.

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

 I am just curious as to why it will not work with ext4 or other.

Just worked perfectly for me on my existing 12.04 system - using EXT4, which is irrelevant to this function anyway - removing and installing FGLRX drivers.

---

