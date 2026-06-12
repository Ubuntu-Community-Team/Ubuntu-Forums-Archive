---
title: "Cannot install boot repair"
date: 2012-12-16
forum: General Help
---

### Post by GreatScott10 on 2012-12-16
I have a dual boot Windows 8/Ubuntu 12.04, which was working fine until win8 stopped booting up (came up with automatic repair, which did nothing). I'm hoping boot repair will help solve the problem but I can't get it to install. 

I ran the following command 

```
 sudo apt-get install -y boot-repair 
```and got the output:
```
 The following packages have unmet dependencies:
boot-repair : Depends: boot-sav (>=3.196) but 3.196~ppa3~precise is to be installed
Recommends: gawk
Recommends: pastebinit but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by 3v3rgr33n on 2012-12-16
> **GreatScott10 said:**
> 
...
I ran the following command 

```
 sudo apt-get install -y boot-repair boot-sav
``` ...


Just curious---What is boot-sav and why are you installing it?

---

### Post by GreatScott10 on 2012-12-16
My mistake, I entered the command without the boot-sav part. I've googled boot-sav and so far I can't figure out what it's for.

---

### Post by forkandles on 2012-12-16
Visit here:

[https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)

Add the PPA to your repository list and then download and install the boot repair for your particular Ubuntu 12.04 edition.

You may need to open Synaptic > Custom Filters > Broken 

to get further help.

---

### Post by YannBuntu on 2012-12-16
> **GreatScott10 said:**
> boot-repair : Depends: boot-sav (>=3.196) but 3.196~ppa3~precise is to be installed

[https://bugs.launchpad.net/boot-repair/+bug/1090841](https://bugs.launchpad.net/boot-repair/+bug/1090841)

---

