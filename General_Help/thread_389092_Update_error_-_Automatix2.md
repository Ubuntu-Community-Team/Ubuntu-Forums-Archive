---
title: "Update error - Automatix2"
date: 2007-03-20
forum: General Help
---

### Post by geovino on 2007-03-20
I'm getting this error when trying to update Automax2:

W: Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.30-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.30-6.10edgy_i386.deb)
  MD5Sum mismatch

is this a temporary thing? try again tomorrow?

---

### Post by taurus on 2007-03-20
Try something like these from a terminal.

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by geovino on 2007-03-20
Did $ sudo aptitude clean  and it got an error message saying temporarily unavailable. I'll wait a couple days and try again.

Thanks

---

### Post by geovino on 2007-03-23
I'm still getting this message:

W: Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.30-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.30-6.10edgy_i386.deb)
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.95), connection timed out

How can I solve this problem?

---

### Post by geovino on 2007-03-23
> **taurus said:**
> Try something like these from a terminal.

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

when I get to update I get this:
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.95)]                       
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg         
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.95), connection timed out
99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.95)]

should I reinstall Automatix?

 
how can I solve this?

---

### Post by jackrobinson on 2007-03-23
> **geovino said:**
> when I get to update I get this:
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.95)]                       
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg         
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.95), connection timed out
99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.95)]

should I reinstall Automatix?

 
how can I solve this?

ask on the automatix forums:
[www.getautomatix.com/forum](www.getautomatix.com/forum)

---

### Post by geovino on 2007-03-24
> **jackrobinson said:**
> ask on the automatix forums:
[www.getautomatix.com/forum](www.getautomatix.com/forum)

Did that and got it working! They were working on their servers for 5 days. Thanks.

Had to run:
$ apt-get update
$ apt-get upgrade

Problem Solved :)

---

