---
title: "apt-get upgrade (broken packages)"
date: 2006-12-12
forum: General Help
---

### Post by android6011 on 2006-12-12
i upgraded to the alpha of feisty and everything has been going good til this. I originally tried to install build-essential when i found that i was having problems with the below packages.


# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  cpp-4.1 gcc-4.1 gcc-4.1-base libgcc1 libstdc++6
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
# apt-get install cpp-4.1 gcc-4.1 gcc-4.1-base libgcc1 libstdc++6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libstdc++6: Depends: libgcc1 (>= 1:4.1.1-22) but 1:4.1.1-21ubuntu1 is to be installed
E: Broken packages

---

### Post by kd7swh on 2006-12-12
try using aptitude:

paste this:


sudo aptitude update;
sudo aptitude upgrade

aptitude does a good job at fixing broken packages

---

