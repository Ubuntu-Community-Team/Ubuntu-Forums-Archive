---
title: "Do you have to defragment ubuntu?"
date: 2006-08-02
forum: General Help
---

### Post by Athanasius on 2006-08-02
Is there something equivalent to defragmenting in Ubuntu?  Is it something that is even necessary?

---

### Post by fourchannel on 2006-08-02
no. the ext2 and ext3 filesystem do not need to be defragged, since they defragment themselves.

I'm not sure exactly how. But ext2/3 is much better about placing files to begin with so restructuring is not a big concern.

read a little into [this]("http://en.wikipedia.org/wiki/Ext3#Disadvantages") for some more info.

---

### Post by Hexx on 2006-08-03
> **Athanasius said:**
> Is there something equivalent to defragmenting in Ubuntu?  Is it something that is even necessary?

No, it's not necessary.

However, over time, your system may become a little messy from installing and uninstalling various packages. Sometimes when you uninstall a package, it will leave behind dependencies that are no longer necessary for you to have on your system. A way around this is installing and uninstalling using "aptitude" as opposed to "apt." For more info on this, [read this]("http://psychocats.net/ubuntu/aptitude.php").

Also, when you install packages, they get archived on your computer, in case you uninstall something, and then decide you want to install it again. To avoid having to download the same package(s), Ubuntu will use the archived files to install the program. The archive can be found under "/var/cache/apt/archives/" - although, Synaptic and apt-get will both look there first on their own. Anyway, this folder can get big after a while, so you may want to clean it out eventually.

Hope this helps.

---

### Post by amunimanghi on 2006-08-03
> Anyway, this folder can get big after a while, so you may want to clean it out eventually.

If you do that, does it affect your system in any way?

---

### Post by wylfing on 2006-08-03
Nope.

There are established ways to do this, however. Don't just go in there and 'rm' stuff. Instead, do this:
```
sudo apt-get clean
```
If I am not mistaken, Synaptic does this on its own.

---

