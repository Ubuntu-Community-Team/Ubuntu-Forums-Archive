---
title: "Messed up perl - need help"
date: 2008-02-12
forum: General Help
---

### Post by Newbi on 2008-02-12
My problem is this:

my laptop has perl ver 5.7.7.x.ubuntu3 installed. I installed perl base 5.7.7.x.ubuntu3.1. Now synaptic shows an error. 

How do I down grade the package? Also muy laptop is not connected to internet. Where can I get the package from and how do I install it?

sudo apt-get install - f also doesn't work

Thanks a ton

---

### Post by zvacet on 2008-02-12
Wich version do you use?I ask you this because lower version I can find is 5.8.7-10ubuntu1.1 for Dapper.Anyway look in var/cache/apt/archives and see do you have both versions there.If you do go in synaptic and remove installed version.After that 

```
cd /var/cache/apt/archives
```

```
sudo dpkg -i lower version
```

**lower version**=exact name of package you want to install

---

