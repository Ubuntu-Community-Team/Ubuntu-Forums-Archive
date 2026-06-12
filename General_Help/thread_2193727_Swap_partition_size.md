---
title: "Swap partition size"
date: 2013-12-14
forum: General Help
---

### Post by garyzw on 2013-12-14
I have 8GB of RAM how big should the swap partition be?

---

### Post by bapoumba on 2013-12-14
There are many threads related to this here on the forums. A recent one for ex : [http://ubuntuforums.org/showthread.php?t=2087889](http://ubuntuforums.org/showthread.php?t=2087889)
Please have a look here too : [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by garyzw on 2013-12-14
Thanks for the reply but i did search the forum and could not get a direct answer. the link you gave says  "25% larger than your actual ram" another response is "At 8 GB, you really don't even need a swap unless you intend on having a dozen major apps open at once or wish to work on huge graphics files." another is "double your installed ram"

I don't plan on hibernating my system, or mess with huge graphic files or have tons of apps open.

---

### Post by bapoumba on 2013-12-14
From the older days, I usually set it up to the RAM size (twice the RAM size for 1GB or less). I've not really bothered trying differently. I suppose you do have a drive big enough not to consider 8GB being lost space :)

---

### Post by Impavidus on 2013-12-14
If you want to hibernate, your swap should be at least the size of your ram (mind the difference between GB and GiB). If not, you're unlike to ever need it. Most people never fill 8 GB ram. On the other hand, your hard disk is probably so large that a few GB more or less don't matter.

---

### Post by philinux on 2013-12-14
> **garyzw said:**
> I have 8GB of RAM how big should the swap partition be?

Do you intend to hibernate?

See this too.

[https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007)


I don't use hibernate. Got 2 gig ram and 2 gig swap. Some say if you not intending to hibernate and you have say 4 gig ram that you dont even need swap.

---

### Post by garyzw on 2013-12-14
> **philinux said:**
> Do you intend to hibernate?

See this too.

[https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007)


I don't use hibernate. Got 2 gig ram and 2 gig swap. Some say if you not intending to hibernate and you have say 4 gig ram that you dont even need swap.

I don't use hibernate. The link you gave says for 8GB I need 8GB of swap. I also read that if I have 8GB then I do not need swap. My hard drive is 2TB so I guess 8GB of swap will not kill me- but then I hate to assign 8GB if it will never be used.

---

### Post by philinux on 2013-12-14
As always the choice is yours.

Another take on this. 

[http://arstechnica.com/civis/viewtopic.php?f=16&t=1208699](http://arstechnica.com/civis/viewtopic.php?f=16&t=1208699)

---

### Post by Topsiho on 2013-12-14
If you have a HDD of 2 TB, which is 2000 GB, or see next, what is the problem of assigning 8+ GB to a swap partition?

If you hate to lose the minute 8+ GB, have you ever wondered about the difference between 2 TB and 2 TiB? The first is decimal, the second is binary, 1024  (2^10) bytes in stead of 1000 bytes, 1024^2 bytes in stead of 1000^2 bytes, so you may calculate yourself how many TiB your HDD really has (far less than 2). The capacity of HDD's are (nearly?) always expressed in decimal.

I only write this to put everything in the real perspective, there really is no problem.

Howgh

Topsiho

---

### Post by garyzw on 2013-12-14
Thanks for all the replies. i willl make it 8GB

---

