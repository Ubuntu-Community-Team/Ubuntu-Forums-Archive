---
title: "Unable to install software from source"
date: 2008-04-27
forum: General Help
---

### Post by funtime on 2008-04-27
I'm currently running Ubuntu 7.10 Gutsy Gibbon on my Dell XPS M1210 laptop, and I am unable to install any software from source. Whenever I attempt to install the software, I get the following error message.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

I do not know what software packages I may need to install in order to get this to work properly, but I really need to be able to install packages from source. Any help you can provide would be very appreciated.

Thank You,
Funtime

---

### Post by forrestcupp on 2008-04-27
Have you installed build-essential?
```
sudo apt-get install build-essential
```

---

### Post by ghost_ryder35 on 2008-04-27
> **forrestcupp said:**
> Have you installed build-essential?
```
sudo apt-get install build-essential
```
:guitar:  definetly going to need that

---

### Post by funtime on 2008-04-27
I tried to run the 'sudo apt-get install build-essential', and this is what I ended up getting. I may have accidentally deleted something that I need. Any other ideas?? Thanks for the help

////////////

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

////////////

---

### Post by zvacet on 2008-04-27
System>admin>software sources check all boxes under ubuntu software and updates tab.Reload.

```
sudo apt-get install build-essential
```

---

### Post by funtime on 2008-04-27
> **zvacet said:**
> System>admin>software sources check all boxes under ubuntu software and updates tab.Reload.

```
sudo apt-get install build-essential
```


I did this, and I still get the same thing when I try to install the build-essential. I don't think it has to do with my apt sources, but rather with certain software I have either installed, or uninstalled on my system.

---

### Post by forrestcupp on 2008-04-27
If you have all of your repos enabled, you might just need to do an update.
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by funtime on 2008-04-27
> **forrestcupp said:**
> If you have all of your repos enabled, you might just need to do an update.
```
sudo apt-get update
sudo apt-get install build-essential
```

I do an update everytime I install updates on my system.

```
sudo apt-get update
sudo apt-get upgrade
```

I don't know what else it could be. I may just need to re-install the entire OS. Do you think upgrading to the new one, 8.04, would help out?

---

### Post by oldos2er on 2008-04-27
Try running "sudo aptitude install -f"

---

### Post by zvacet on 2008-04-28
In system>softwae sources check/uncheck cdrom,so your cd will be one of sources in your source list.Now when you run 

```
sudo apt-get install build-essential
```

comp wil tell you to put CD in drive.Do that and install build-essential from CD.

---

