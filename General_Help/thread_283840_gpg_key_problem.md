---
title: "gpg key problem?"
date: 2006-10-24
forum: General Help
---

### Post by K3WHO on 2006-10-24
I've had this problem now for quite a few weeks on both of the machines I have when I run apt-get update.

```
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems

```

I'm assuming it's a problem with the key I have...If so how do I get a new key? Any help is greatly appreciated :)

---

### Post by aktiwers on 2006-10-24
Check this post..  it will fix your problem
[http://www.ubuntuforums.org/showthread.php?t=279758](http://www.ubuntuforums.org/showthread.php?t=279758)

---

### Post by ~LoKe on 2006-10-24
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```

---

### Post by John.Michael.Kane on 2006-10-24
That is a PLF repo. you can look here [http://plf.zarb.org/index.php](http://plf.zarb.org/index.php) for a replacement repo

---

### Post by K3WHO on 2006-10-24
thanks for the quick help :) I got the one fixed but the other is giving me this...

```
Reading package lists... Done
W: GPG error: http://deb.opera.com etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: You may want to run apt-get update to correct these problems

```

I removed opera and rebooted and got the same message.

---

### Post by John.Michael.Kane on 2006-10-24
Have a look here [http://deb.opera.com/](http://deb.opera.com/)

---

### Post by dagnabit dang doohickey on 2006-10-24
You can find what you want here:
[http://doc.ubuntu-fr.org/doc/plf]("http://doc.ubuntu-fr.org/doc/plf")

---

