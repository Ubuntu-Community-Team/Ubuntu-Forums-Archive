---
title: "tmux defaulting to /bin/sh"
date: 2016-06-14
forum: General Help
---

### Post by papibe on 2016-06-14
Hi all,

I wonder if anybody have experienced this.

Today initiated a tmux session and it is opening a /bin/sh shell instead of the usual /bin/bash.

Things that I've done to try to revert to the previous behavior and did not work:
Reconfigure the package:
```
sudo dpkg-reconfigure tmux
```
Purge and reinstall:
```
sudo apt-get purge tmux

sudo apt-get install tmux
```
I can force it back to bash putting this in my ~/.tmux.conf, but I wonder what's going on:
```
set-option -g default-shell /bin/bash
```
I appreciate any help you can give me.
Regards.

EDIT:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

uname -a
Linux vaughan 3.16.0-73-generic #95~14.04.1-Ubuntu SMP Thu Jun 9 08:00:04 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

$ apt-cache policy tmux 
tmux:
  Installed: 1.8-5
  Candidate: 1.8-5
  Version table:
 *** 1.8-5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

