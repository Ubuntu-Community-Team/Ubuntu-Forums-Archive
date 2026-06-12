---
title: "Run command at system boot"
date: 2006-08-11
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-08-11
Hi, I need to be able to run hdparm and configure my harddisk right after the root file system is mounted. How can this be accomplished ? Thanks.

---

### Post by Ramses de Norre on 2006-08-11
This should do: ```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S20hdparm
```
Try giving a value lower then 20 when it needs to get loaded earlier (but be careful with it!), I've got 20 on my machine and that works perfect.

---

### Post by xXx 0wn3d xXx on 2006-08-11
> **Ramses de Norre said:**
> This should do: ```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S20hdparm
```
Try giving a value lower then 20 when it needs to get loaded earlier (but be careful with it!), I've got 20 on my machine and that works perfect.

Sorry, I made a mistake. I actually want to run a command using hdparm. Something like this:

> hdparm -u0 -M 254 -c3 -a 768 -m 16 /dev/hda

I'm sorry that I didn't make myself clear in my previous post. I just need to run that command during boot.

---

### Post by yopnono on 2006-08-12
> **xXx 0wn3d xXx said:**
> Sorry, I made a mistake. I actually want to run a command using hdparm. Something like this:



I'm sorry that I didn't make myself clear in my previous post. I just need to run that command during boot.

One way is to put the string in the /etc/rc.local file. Or in the hdparm.
Since the hdparm are loaded at boot aswell

---

### Post by Ramses de Norre on 2006-08-12
```
sudo vi /etc/hdparm.conf
```
Add this at the end:
```
command_line {
       hdparm -u0 -M 254 -c3 -a 768 -m 16 /dev/hda
}

```

---

