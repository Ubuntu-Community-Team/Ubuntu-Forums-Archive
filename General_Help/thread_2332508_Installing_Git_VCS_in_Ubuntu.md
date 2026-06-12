---
title: "Installing Git VCS in Ubuntu"
date: 2016-08-01
forum: General Help
---

### Post by Enforcer83 on 2016-08-01
I attempted to install GIT using the following command at terminal so I can locally institute a version management system for several personal projects. 

```
sudo apt install git-all
```

During installation  I get the following error.  I am unable to figure out what I need to do.  I am currently running Ubuntu 16.04.1.

```
Setting up runit (2.1.2-3ubuntu1) ...
start: 
Unable to connect to Upstart: 
Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 
git-daemon-run depends on runit; however:
  
Package runit is not configured yet.

dpkg: error processing package git-daemon-run (--configure):
 
dependency problems - leaving unconfigured                       
Errors were encountered while processing:
 runit
 git-daemon-run
E: Sub-process /usr/bin/dpkg returned an error code (1)
 

```

---

