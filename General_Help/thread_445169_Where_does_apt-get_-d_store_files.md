---
title: "Where does apt-get -d store files?"
date: 2007-05-15
forum: General Help
---

### Post by loathsome on 2007-05-15
```
  -d  Download only - do NOT install or unpack archives
```

When I for example run a "apt-get -d bluefish"; Where does the bluefish files get stored?
Thanks!

---

### Post by zvacet on 2007-05-15
Everything you download with apt-get,aptitude or synaptic is stored in var/cache/apt/archives

---

### Post by doctorwho on 2007-09-03
In addition to /var/cache/apt/archives , I have found files downloaded by apt-get or Adept manager located in /etc/apt/cache/archives . What is the difference between these two directories? What is their relationship?

---

### Post by capink on 2007-09-04
> **zvacet said:**
> Everything you download with apt-get,aptitude or synaptic is stored in var/cache/apt/archives

That is correct only when you use apt-get install without the -d flag. However, when you use apt-get install -d, files are downloaded to the current directory, which is usually your home dir unless you changed that with cd command.


Edit: What I said above is wrong. I got confused between apt-get download and apt-get install -d. Apologies.

---

