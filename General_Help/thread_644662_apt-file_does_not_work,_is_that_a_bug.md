---
title: "apt-file does not work, is that a bug?"
date: 2007-12-19
forum: General Help
---

### Post by luqsim on 2007-12-19
Hallo everyone,

I am using Ubuntu Gutsy. After some update, I am not sure which one, the apt-file does not work any more. If you try this for example 
```
apt-file search sources.list 
```
The computer won't do anything. Then I have tried  
```
apt-file -v search sources.list
```
Here is the system output:
```
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy universe'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy universe'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse'
D: got 'deb http://archive.canonical.com/ubuntu gutsy partner'
D: kept 'deb http://archive.canonical.com/ubuntu gutsy partner'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse'
D: got 'deb http://www.getautomatix.com/apt gutsy main'
D: kept 'deb http://www.getautomatix.com/apt gutsy main'
D: got 'deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse'
D: regexp: ^(.*?sources\.list[^\s]*)\s+(\S+)\s*$
```
And also, you won't get the right result.
With ```
apt-file --version 
``` I know the version of apt-file is 2.0.8.2.
Is that a bug of apt-file? What should I do to repair it?
THX

---

### Post by mali2297 on 2007-12-19
Have you tried to rerun [FONT="System"]**apt-file update**[/FONT]?

---

