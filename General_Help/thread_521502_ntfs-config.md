---
title: "ntfs-config"
date: 2007-08-09
forum: General Help
---

### Post by cssutto on 2007-08-09
Nfst-config is not in my synaptic nor can apt-get install find it.

I am running 6.06.

I am having problems accessing a new external hard drive and need it.

It is a dual boot system, so I must use a Windoze friendly file system.

CSSJR

---

### Post by msergent on 2007-08-09
Have you tried looking at the following link:

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

---

### Post by g2g591 on 2007-08-09
you *can download and compile the [source]("http://flomertens.free.fr/ntfs-config/download/source/ntfs-config-1.0.1.tar.gz")*

---

### Post by g2g591 on 2007-08-09
oh and you're also gonna need ntfs-3g, that source is [here]("http://www.ntfs-3g.org/ntfs-3g-1.710.tgz")

---

### Post by merlinus on 2007-08-09
> 
Nfst-config is not in my synaptic nor can apt-get install find it.


You have misspelled the name.

```

sudo apt-get install ntfs-3g ntfs-config

```Copy-and-paste works best!

-merlin

---

### Post by stchman on 2007-08-09
> **cssutto said:**
> Nfst-config is not in my synaptic nor can apt-get install find it.

I am running 6.06.

I am having problems accessing a new external hard drive and need it.

It is a dual boot system, so I must use a Windoze friendly file system.

CSSJR

Yes, ntfs-config is available only in Feisty or later.

I personally don't use the that package as it is either all read/write or all read.  I have several NTFS partitions and I want to write to only one of them and not to the others.

---

### Post by stchman on 2007-08-09
> **merlinus said:**
> You have misspelled the name.

```

sudo apt-get install ntfs-3g ntfs-config

```Copy-and-paste works best!

-merlin

ntfs-3g is a dependency of ntfs-config.  You don't need to install ntfs-3g if you install ntfs-config, it gets installed automatically.

---

### Post by cssutto on 2007-08-09
I fixed it with the info here.

Thanks.

---

