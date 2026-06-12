---
title: "MD5sum security...?"
date: 2013-06-03
forum: General Help
---

### Post by KingNeil on 2013-06-03
I'm downloading the Wubi installer for Ubuntu 12.04.... and I've gone to the Ubuntu website to check the MD5 sum and SHA1 sum for the file.

I was just wondering... what is the security quality of MD5, and also, of SHA1

According to Wikipedia, MD5 isn't entirely secure.

What is the best way to ensure that the file that I'm downloading from Ubuntu.com will not be tampered with...?

---

### Post by sudodus on 2013-06-03
I checked that the wiki page with the md5sums of Ubuntu iso files is write protected (only very few people have write permission), so it is rather reliable. I recommend that you connect to it with [FONT=courier new]**https**[/FONT]

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Of course nothing is 100% secure, but I think that the md5sum check is a good way to check that

1. the downloading process was successful (technically)

2. the file was downloaded from a correct copy.

---

### Post by sudodus on 2013-06-03
> **KingNeil said:**
> I'm downloading the Wubi installer for Ubuntu 12.04....

Maybe it is worth mentioning that wubi is being abandoned. It will stay in the versions where it is. But it's absent in 13.04 because it was not possible to get it working with UEFI, and I think it will not come back in 13.10 or 14.04 LTS.

Anyway if you install with wubi, regard it as a test system and be prepared to migrate to a regular installation (typically dual boot with Windows).

---

