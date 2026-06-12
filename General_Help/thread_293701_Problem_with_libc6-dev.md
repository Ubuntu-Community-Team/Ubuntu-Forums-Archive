---
title: "Problem with libc6-dev"
date: 2006-11-05
forum: General Help
---

### Post by SupremePiracy on 2006-11-05
Today I tried to install beryl. But it didn't work, I got frustrated by several problems and now I want to remove it. But, when trying to use sudo apt-get remove beryl I get the following problem. 

tobbe@dammburk:~$ LANG=en_GB.UTF8 sudo apt-get remove beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  beryl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  beryl
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 24.6kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing beryl (--remove):
 files list file for package `libc6-dev' contains empty filename
Errors were encountered while processing:
 beryl
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've checked synaptic, there's no broken packages. I've tried removing and reinstalling the libc6-dev but then I get the following error: 

tobbe@dammburk:~$ LANG=en_GB.UTF8 sudo apt-get remove libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  g++-4.1 g++ linux-libc-dev libstdc++6-4.1-dev dpkg-dev libc6-dev
  build-essential
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 24.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing build-essential (--remove):
 files list file for package `libc6-dev' contains empty filename
Errors were encountered while processing:
 build-essential
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Some help would be appreciated... because I can't install anything at the moment.

---

### Post by SupremePiracy on 2006-11-05
I've got some help on this problem and now it complains about another file. linux-libc-dev

The same error but with a different package. He also told me that something was terrible wrong and he recommended me to reinstall everything. But hey, I just reinstalled ubuntu... I don't want to go thrue that process again... I will loose a lot of files. please, there's got to be someway to fix this? 

](*,)

---

