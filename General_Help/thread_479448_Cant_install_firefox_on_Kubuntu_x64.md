---
title: "Cant install firefox on Kubuntu x64"
date: 2007-06-20
forum: General Help
---

### Post by Cogman on 2007-06-20
Hello all, Im having a problem installing firefox on Kubuntu. When I try it I get this error message:
```
cogman@cogman-desktop:~$ sudo apt-get install firefox
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnspr4 libnss3
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox libnspr4 libnss3
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1044kB/11.5MB of archives.
After unpacking 37.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  firefox
Install these packages without verification [y/N]? y
Get:1 http://security.ubuntu.com feisty-security/main libnspr4 2:1.firefox2.0.0.4+1-0ubuntu1 [173kB]
Get:2 http://security.ubuntu.com feisty-security/main libnss3 2:1.firefox2.0.0.4+1-0ubuntu1 [871kB]
Fetched 1045kB in 9s (110kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox2.0.0.4+1-0ubuntu1_amd64.deb  Size mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox2.0.0.4+1-0ubuntu1_amd64.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
cogman@cogman-desktop:~$
```

I've tried changing respritories to no avail, but if you still think thats the problem Im willing to give it another shot. (im almost ready to just download the source and install it, but it would be better if kubuntu installed it)

---

### Post by Happy_Man on 2007-06-20
Hmm... I think it's because Firefox doesn't support x86_64 systems that you are having this problem. I suggest Swiftfox; it's an optimized build of Firefox for different processors. Gives you a nice speed boost too.

---

### Post by kuja on 2007-06-20
Load of FUD, it's supported just fine.
This looks like a repository issue. Try switching mirrors if possible, or try again later.

---

### Post by Cogman on 2007-06-21
I tried switching mirrors to no avail (and kept trying). I ended up getting swiftfox x32 from a post in the X64 section (opps, probably should have put this there) It is working fine for me right now. I hope the firefox thing gets fixed though as I don't want to have to download a third-party script everytime I do a x64 install on a computer.

---

### Post by kuja on 2007-06-21
As of five minutes ago, using the main security updates mirror (which is the one you would have had to switched, none of the others mattered), on a similar configuration:

~$ install firefox
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libhunspell-1.1-0 libnspr4 libnss3
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox libhunspell-1.1-0 libnspr4 libnss3
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.5MB/11.6MB of archives.
After unpacking 37.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libnspr4 2:1.firefox2.0.0.4+1-0ubuntu1 [173kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libnss3 2:1.firefox2.0.0.4+1-0ubuntu1 [872kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main firefox 2.0.0.4+1-0ubuntu1 [10.4MB]
Fetched 11.5MB in 2m14s (85.0kB/s)                                             `
Selecting previously deselected package libhunspell-1.1-0.
(Reading database ... 81722 files and directories currently installed.)
Unpacking libhunspell-1.1-0 (from .../libhunspell-1.1-0_1.1.4-7_amd64.deb) ...
Selecting previously deselected package libnspr4.
Unpacking libnspr4 (from .../libnspr4_2%3a1.firefox2.0.0.4+1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libnss3.
Unpacking libnss3 (from .../libnss3_2%3a1.firefox2.0.0.4+1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_2.0.0.4+1-0ubuntu1_amd64.deb) ...
Setting up libhunspell-1.1-0 (1.1.4-7) ...

Setting up libnspr4 (1.firefox2.0.0.4+1-0ubuntu1) ...

Setting up libnss3 (1.firefox2.0.0.4+1-0ubuntu1) ...

Setting up firefox (2.0.0.4+1-0ubuntu1) ...
Please restart any running Firefoxes, or you will experience problems.

---

### Post by Cogman on 2007-06-21
very very strange, Mine is set to archive.ubuntu.com instead of security.ubuntu.com like yours, for what reason I don't exactly know but it worked all the same. humm very strange. Ohh well, thanks for the help.

---

