---
title: "unmet dependency python-pkg-resources"
date: 2014-05-23
forum: General Help
---

### Post by nickstu-hotmail on 2014-05-23
I'm trying to install ROS, and I get some missing dependencies. I tracked them down to this one which says:
```

tesi@VisionServer:~$ sudo apt-get install python-setuptools --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 python-setuptools : Depends: python-pkg-resources (= 0.6.16-1) but 0.6.16-1ubuntu0.1 is to be installed
E: Unable to correct problems, you have held broken packages.



```

it seems to me that the right package is installed but it is not recognized as such...

---

### Post by mc4man on 2014-05-23
You seem to be have an 11.10 install which is EOL. If wishing to continue with it then look into switching your sources to the old-release repos

As far as python-setuptools & python-pkg-resources, - they have to be the same version (exactly
You can find them here - 
[https://launchpad.net/ubuntu/+source/distribute/0.6.16-1ubuntu0.1/+build/3219554](https://launchpad.net/ubuntu/+source/distribute/0.6.16-1ubuntu0.1/+build/3219554)
or if desired the last version built for 11.10 seems to be this - 
[https://launchpad.net/ubuntu/+source/distribute/0.6.16-1ubuntu0.2/+build/3311315](https://launchpad.net/ubuntu/+source/distribute/0.6.16-1ubuntu0.2/+build/3311315)

---

