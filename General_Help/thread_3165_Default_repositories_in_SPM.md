---
title: "Default repositories in SPM?"
date: 2004-11-03
forum: General Help
---

### Post by Slovak on 2004-11-03
I accidently checked off all repositories, got side tracked and can't remember which ones are the defaults to use. Which should I use as default for SPM?

---

### Post by jdusablon on 2004-11-03
You could just replace the text (all or just what you need) in /etc/apt/sources.list with this```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu warty main restricted
deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu warty universe
deb-src http://archive.ubuntu.com/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted
```This is just the defaults + Universe.

---

### Post by Slovak on 2004-11-04
Hmm, that is exactly what mine shows in /etc/apt/sources.list, but when I launch SPM and go to Settings>repositories, I have something totally different   :shock: 
How can that be? It is similar, but yet different. How do I fix that?

---

