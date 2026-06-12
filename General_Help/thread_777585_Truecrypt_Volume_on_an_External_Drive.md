---
title: "Truecrypt Volume on an External Drive"
date: 2008-05-01
forum: General Help
---

### Post by natibo on 2008-05-01
I posted this in the truecrypt forums but got no response.

Hello. I am running Hardy 8.04 64-bit. I downloaded and installed the current version of truecrypt from the website. I was successful in creating a 10GB volume on my hard drive and it works great.

I am also trying to create a 10GB volume on a 500GB external drive so I can backup the encrypted files on my hard drive. There is plenty of room on the hard drive. However, when I try to create the volume it gets about 1/3 of the way through and then I get en error message saying the device is busy try again later.

I have tried restarting my machine and deleting any trash. Nothing seems to work. I am a relative newbie to linux so if you have a fix, please explain it in simple terms.

Thanks.

---

### Post by skywalkin1138 on 2008-05-15
What is the file system on the mounted USB drive?  NTFS?  FAT?

If it's NTFS, you may want to try upgrading the version of ntfs-3g which comes with Hardy to the latest (1.2506, I believe).

The downside is you would have to download it, compile it and install it.  Unless you've already installed things like "gcc", this could prove a bit daunting.  Not sure how much experience you have with software since you say you're a "Linux newbie".

---

