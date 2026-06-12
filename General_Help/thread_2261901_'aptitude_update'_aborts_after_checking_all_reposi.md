---
title: "'aptitude update' aborts after checking all repositories"
date: 2015-01-21
forum: General Help
---

### Post by mave-m on 2015-01-21
Anyone have an idea what might cause this as a result of using 'aptitude update'?
```
sh: line 1: 14645 Killed                  apt-show-versions -i
E: Problem executing scripts APT::Update::Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i'
E: Sub-process returned an error code
E: Couldn't rebuild package cache
```When i enter '[COLOR=#000000]apt-show-versions -i' it returns 'Killed' as result. 
Google isn't very helpful on this problem so i hope someone could help me solve this problem. I'm running Ubuntu Server 14.04 LTS x64.[/COLOR]

---

