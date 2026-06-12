---
title: "[SOLVED] What is the APT line for Medibuntu??......"
date: 2007-07-22
forum: General Help
---

### Post by ReaderRat on 2007-07-22
I know HOW to add the APT line for a repository, but what is the proper line to add for Medibuntu?

---

### Post by Seisen on 2007-07-22
```
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```
then to add the key 

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

---

