---
title: "Help me! I can't install ANYTHING !!!"
date: 2006-11-02
forum: General Help
---

### Post by realtiger on 2006-11-02
After having a fresh install of Edgy, I can't install any new programs.
This error occurred any times I want to install a new package:

***files list file for package `xmodmap' is missing final newline***

Here is the full error message when I install build-essential:

```
root@tiger-lab:~# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/7930kB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-libc-dev_2.6.17-10.33_i386.deb (--unpack):
 files list file for package `xmodmap' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/linux-libc-dev_2.6.17-10.33_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thank you very much !!! :) :) :)

---

### Post by johnny9794 on 2006-11-02
Did ya add repositories?

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by realtiger on 2006-11-02
I can download package so I think repository is not the problem.
I think the problem is in this error message, but I don't understand.
[B][I]
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-libc-dev_2.6.17-10.33_i386.deb (--unpack):
 files list file for package `xmodmap' is missing final newline[/I][/B]

---

### Post by realtiger on 2006-11-02
Finally my problem is solved.
If someone has the same problem, here is the answer:
[http://ubuntuforums.org/showthread.php?t=214805](http://ubuntuforums.org/showthread.php?t=214805)

---

### Post by buckrodgers on 2006-12-22
try this:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
sudo gedit /var/lib/dpkg/status #look for the broken package and remove that package.
sudo rm /var/cache/apt/*.bin
sudo apt-get upgrade
sudo apt-get -f install

```

---

