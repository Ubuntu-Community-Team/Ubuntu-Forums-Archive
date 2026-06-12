---
title: "apt - Why does package libnvidia-gl-440:i386 points towards the 450 version?"
date: 2021-07-16
forum: General Help
---

### Post by maxander42 on 2021-07-16
I have noticed something strange in the official ubuntu repo.

Here's the install candidates for `libnvidia-gl-440:i386`


[HTML] 
$ apt-cache policy libnvidia-gl-440:i386
libnvidia-gl-440:i386:
  Installed: (none)
  Candidate: 450.119.03-0ubuntu0.18.04.1
  Version table:
     450.119.03-0ubuntu0.18.04.1 500
        500 http://ee.archive.ubuntu.com/ubuntu bionic-updates/restricted i386 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/restricted i386 Packages
[/HTML]


And if I have a look at the ubuntu repo website : [https://packages.ubuntu.com/bionic/libnvidia-gl-440](https://packages.ubuntu.com/bionic/libnvidia-gl-440)

It points to the version [FONT=lucida console]450.119.03-0ubuntu0.18.04.1[/FONT] : 
>  Package: libnvidia-gl-440 (450.119.03-0ubuntu0.18.04.1) [security] [restricted] 

Is it normal ? How can you explain this ? 

Does it mean it will always try to switch the the 450 version ?

Thanks !

---

### Post by Yellow Pasque on 2021-07-16
> Does it mean it will always try to switch the the 450 version ?
Yes. It's a transitional package, which means it will point to the newer version. There shouldn't be a need to use an older nvidia driver unless you need a legacy one.

---

