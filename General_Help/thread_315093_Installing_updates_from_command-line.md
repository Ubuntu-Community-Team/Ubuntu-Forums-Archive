---
title: "Installing updates from command-line"
date: 2006-12-08
forum: General Help
---

### Post by navneeth on 2006-12-08
Simple: I have a bunch of updates waiting for to be downloaded. I want to install them with a simple command from the termial.

What command should I use?

---

### Post by tribaal on 2006-12-08
Easy enough:

"sudo apt-get update && sudo apt-get upgrade"

Shoud do the trick. You can of course substitute apt-get for aptitude, depending on what you're used to using.

- trib'

---

### Post by lhtown on 2006-12-08
If some file are held back after installing, you can try
```
sudo apt-get dist-upgrade
```

Also, you can use it instead of
```
sudo apt-get upgrade
```

---

### Post by navneeth on 2006-12-08
upgrade! I actually wanted to check what that would do...but didn't want to take a "risk"! :D

Thanks a bunch.

---

### Post by aysiu on 2006-12-08
I've been told the best way to do upgrades is ```
sudo apt-get dist-upgrade
``` or ```
sudo aptitude dist-upgrade
```

---

### Post by bettlebrox on 2006-12-08
use the "-u" flag to show what package to be updated:

apt-get -u upgrade
OR
apt-get -u dist-upgrade

---

### Post by navneeth on 2006-12-10
> **aysiu said:**
> I've been told the best way to do upgrades is ```
sudo apt-get dist-upgrade
``` or ```
sudo aptitude dist-upgrade
```
How are dist-upgrade and upgrade different? I've seen the former when 6.10 came out and people were upgrading from Dapper.

---

### Post by aysiu on 2006-12-10
> **navneeth said:**
> How are dist-upgrade and upgrade different? I've seen the former when 6.10 came out and people were upgrading from Dapper.
Read [this thread](http://ubuntuforums.org/showthread.php?t=86198).

---

### Post by navneeth on 2006-12-11
Thanks for the link, asiyu. Guess "I'll do dist-upgrades then!" :D

---

