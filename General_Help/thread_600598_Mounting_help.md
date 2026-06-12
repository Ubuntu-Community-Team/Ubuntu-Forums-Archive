---
title: "Mounting help"
date: 2007-11-02
forum: General Help
---

### Post by Graeme2804 on 2007-11-02
How do I mount a .mds file?  I did it with daemon tools on windows, but i can't use daemon tools on ubuntu.

Any ideas?

---

### Post by bingoUV on 2007-11-02
> **Graeme2804 said:**
> How do I mount a .mds file?  I did it with daemon tools on windows, but i can't use daemon tools on ubuntu.

Any ideas?

I don't know about mds files, but I remember from my windows days that you use daemon tools to mount a cd image. If it is a cd/dvd image, use the following command :
```

sudo mkdir /media/mountMds
sudo mount -o loop yourfile.mds /media/mountMds

```

---

### Post by Graeme2804 on 2007-11-02
```
graeme@graeme:~$ sudo mkdir /media/mountMds
[sudo] password for graeme:
graeme@graeme:~$ sudo mount -o loop /home/graeme/Documents/Downloads/FM2008/FM2008.mds /media/mountMd
mount: mount point /media/mountMd does not exist
graeme@graeme:~$ sudo mount -o loop /home/graeme/Documents/Downloads/FM2008/FM2008.mds /media/mountMds
mount: you must specify the filesystem type
graeme@graeme:~$ 

```

where've I gone wrong?

---

### Post by Graeme2804 on 2007-11-02
anyone?

---

### Post by Steve1961 on 2007-11-02
Just done a quick google search and it seems the mds format is a proprietary format used by alcohol 120% in windows.  However, you can install a tool called mdf2iso that might be able to convert it to a normal iso image.  Just install it via synaptic and then do a quick man mdf2iso to find out how to use it.   Worth a try :)

---

### Post by hikaricore on 2007-11-02
In the future you should "backup" all of your legally purchased CD/DVDs to the industry standard ISO format.  ^_^

---

