---
title: "Where to get Beryl 0.1.2 ?"
date: 2006-12-13
forum: General Help
---

### Post by trailer on 2006-12-13
I have upgraded Beryl 0.1.3 on my laptop and since then it is not working properly. Because Beryl 0.1.2 worked fine for me I want to go back to Beryl 0.1.2.

How can I get Beryl 0.1.2 back? In Synaptic only verion 0.1.3 shows up.

Thanks in advance.

---

### Post by Sqwishy on 2006-12-13
do you have amd/intel? ati/nvidia? dapper/edgy?

---

### Post by trailer on 2006-12-13
Intel Mobile, Intel 915 Graphics and Edgy.
I installed Beryl with AIGLX.

---

### Post by Sqwishy on 2006-12-13
> **trailer said:**
> Intel Mobile, Intel 915 Graphics and Edgy.
I installed Beryl with AIGLX.
alright, try this repo...
```
deb http://beryl-mirror.lupine.me.uk/ edgy all
```
and get this thingy
```
wget http://beryl-mirror.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add -
```
and remove the previous beryl 0.1.3 reposotorie so it shouldn't show up in synaptic
dont forget
```
sudo apt-get update
sudo apt-get upgrade
```
:D

---

