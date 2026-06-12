---
title: "What are some program(s) recommended for ripping audio CD's to FLAC?"
date: 2008-02-15
forum: General Help
---

### Post by jbcaprell on 2008-02-15
I understand that Exact Audio Copy will run under WINE, but I prefer using something that will run natively if it can be helped. Any suggestions are appreciated.

---

### Post by vambo on 2008-02-15
asunder will rip and encode to FLAC - it's in the repos

---

### Post by jbcaprell on 2008-02-15
I can't seem to find it in the repository, though I've found a program named asunder [here]("http://littlesvr.ca/asunder/"). I am running amd64 gutsy if that makes a difference.

---

### Post by vambo on 2008-02-15
It's definitely in the repos. Make sure you have them all enabled. Yes, that link is for the same program, and it runs under 64-bit - that's what I'm using

---

### Post by Technophobia on 2008-02-15
A program called "Sound Converter" believe it or not does the job. 

goto

Applications > Add/Remove (at the bottom)

and then search for Sound Converter.

---

### Post by jbcaprell on 2008-02-15
Though I've since downloaded the program from its website, the fact that I can't find it in the repositories troubles me. Here's my /etc/apt/sources.list:

```
## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu/ gutsy partner
deb-src http://archive.canonical.com/ubuntu/ gutsy partner

deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free
```

Any apparent reason it might not be showing up?

---

### Post by vambo on 2008-02-15
Nothing obvious. Have you tried looking for it using Synaptic?
Or, via command line

```
aptitude search asunder
```

---

### Post by jbcaprell on 2008-02-15
```
jonathan@sirius:~$ aptitude search asunder

```

Doesn't return anything. Neither does searching Add/Remove Programs for that matter.

Synaptic doesn't seem to list it either.

---

### Post by vambo on 2008-02-15
Well the only difference is my sources.list is pointing to the main server, i.e., archive.ubuntu.com as opposed to us.archive.ubuntu.com, which I assume is the US mirror.

---

### Post by oldb0y on 2008-02-15
I use Sound Juicer CD-ripper, it works great, and is also in the repos.

---

