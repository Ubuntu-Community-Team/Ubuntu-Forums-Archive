---
title: "HELP!! Edubuntu-docs/ubuntu-docs error"
date: 2008-03-19
forum: General Help
---

### Post by mopp4 on 2008-03-19
When Ii ran the updates this week I got an error (i cant really remember what it said), ever since, when I try to install anything or update anything on my daughters Edubuntu computer I get the following error:
```

Setting up ubuntu-docs (7.10.5) ...
dpkg: error processing ubuntu-docs (--configure):
subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of edubuntu-docs:
 edubuntu-docs depends on ubuntu-docs; 
however:
  Package ubuntu-docs is not configured yet.
dpkg: error processing edubuntu-docs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-docs
 edubuntu-docs
E:Sub-process /usr/bin/dpkg returned an error code (1)
```
I have tried everything i know:
```
sudo dpkg --configure -a
```
```
 sudo apt-get install ubuntu-docs edubuntu-docs --reinstall
```
and a whole slew of other commands from other posts.
 Nothing is working.
Its freezing periodically when she runs Firefox, GCompris, or TuxPaint. 

If I were home, by now I would have probably done a reinstall of  Edubuntu, but unfortuantly I wont be back in the States for a while. If at all possible I need to avoid a reinstall. I use a VNC client to remote in to her computer. 
Please Help.

Administrators: I have researched this issue, please don't think I'm just posting on a whim.

---

### Post by kesman on 2008-03-19
How about:
```

sudo apt-get clean
sudo apt-get update
sudo apt-get install --reinstall ubuntu-docs

```
if this doesn't work, try
```

sudo apt-get purge ubuntu-docs
sudo apt-get install ubuntu-docs

```
it took about 10min with my 1,6ghz laptop to set up ubuntu-docs, dunno why, you just have to wait.

---

