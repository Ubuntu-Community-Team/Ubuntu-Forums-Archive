---
title: "Can't update  : W:GPG error: http://deb.opera.com stable Release"
date: 2012-11-27
forum: General Help
---

### Post by A.Zan on 2012-11-27
Don't know what i have to do please give me some advices

> 
W:GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AAFF4A5B336064B5, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.I'm using 11.04 (32 bit)

also I haven't Opera on my computer

---

### Post by oldos2er on 2012-11-27
Add the key ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AAFF4A5B336064B5

sudo apt-get update
```

---

### Post by A.Zan on 2012-11-29
I get [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

---

### Post by plucky on 2012-11-29
> **A.Zan said:**
> I get [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

[Natty](https://help.ubuntu.com/community/CommonQuestions)(11.04)
 reached End Of Life on the 28th October and so the repositories have been closed.

Remove the **extras** repository from your Software Sources or if you are running Natty,think about upgrading.

Good Luck

---

