---
title: "How do I run testdisk on Ubuntu live CD?"
date: 2013-06-06
forum: General Help
---

### Post by xenoalien on 2013-06-06
I have searched and followed lots of tutorials and can't seem to run testdisk. I tried installing it with sudo apt-get install testdisk and I have made sure the services.list file doesn't have the universe repository reference commented out and even tried installing universe repository form the command line but I still get the cannot locate packed error: "E: Unable to locate package testdisk" when I try to install testdisk.

Basically what I would like to do is run testdisk from a live ubuntu cd. I am trying to recover files on a windows xp laptop.

---

### Post by oldfred on 2013-06-06
I assume you are running something newer than you signature - Ubuntu 6.10 Edgy? What version are you currently running as live installer. It needs to be current.

---

### Post by xenoalien on 2013-06-06
> **oldfred said:**
> I assume you are running something newer than you signature - Ubuntu 6.10 Edgy? What version are you currently running as live installer. It needs to be current.

Yes I  will get that updated. The version I am using is Ubuntu 12.04 LTS

---

### Post by oldfred on 2013-06-06
I have not tried testdisk from liveCD, but installed it with synaptic and I am using 12.04.

---

### Post by Cheesemill on 2013-06-07
Make sure you run...
```
sudo apt-get update
```
before running...
```
sudo apt-get install testdisk
```

---

