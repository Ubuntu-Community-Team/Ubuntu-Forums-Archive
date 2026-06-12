---
title: "Issue installing Jenkins  and get &quot;Depends: daemon but it is not installable&quot;"
date: 2017-06-05
forum: General Help
---

### Post by sfenech2 on 2017-06-05
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial


Version of installed Java
openjdk version "1.8.0_131"
OpenJDK Runtime Environment (build 1.8.0_131-8u131-b11-0ubuntu1.16.04.2-b11)
OpenJDK 64-Bit Server VM (build 25.131-b11, mixed mode)


How I installed Jenkins 
Example 1:  [https://tecadmin.net/install-jenkins-in-ubuntu/](https://tecadmin.net/install-jenkins-in-ubuntu/)
Example 2:  [https://pkg.jenkins.io/debian/](https://pkg.jenkins.io/debian/)




1.  I following the instructions located at the above sites.  
2.  Ran apt-get install jenkins and got the following error.  




Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 jenkins : Depends: daemon but it is not installable
E: Unable to correct problems, you have held broken packages.


Can someone help me with this please?

---

### Post by again? on 2017-06-05
Jenkins installs fine here using the repository or a downloaded deb, pulling in the daemon dependency.
daemon should be in the official repositories.
```
glen@Xen2:~$ **lsb_release -a**
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

glen@Xen2:~$ **java -version**
openjdk version "1.8.0_131"
OpenJDK Runtime Environment (build 1.8.0_131-8u131-b11-0ubuntu1.16.04.2-b11)
OpenJDK 64-Bit Server VM (build 25.131-b11, mixed mode)

```

```
glen@Xen2:~$ **apt policy jenkins**
jenkins:
  Installed: 2.64
  Candidate: 2.64
  Version table:
 *** 2.64 100
        100 /var/lib/dpkg/status

glen@Xen2:~$ **apt policy daemon**
daemon:
  Installed: 0.6.4-1
  Candidate: 0.6.4-1
  Version table:
 *** 0.6.4-1 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
```

If at any stage you downloaded a jenkins deb file and installed using "**sudo dpkg -i jenkins_2.[COLOR="#A9A9A9"]xx[/COLOR]_all.deb**", you will see that type of error as
dpkg doesn't resolve dependencies.
It will leave jenkins in an unconfigured state until the dependency issue is fixed with
```
sudo apt install -f
```
If a dependency is unavailable it will ask to remove jenkins.

I prefer gdebi to install deb files as it resolves dependencies.

---

### Post by sfenech2 on 2017-06-06
Looks like the Daemon dependency is the issue.  I can't find anythign on Google that matches my issue.   Any idea?




I tried the following based on what you said.  Thanks for the help by the way.  


1.  Ran apt-get -f install 
 
2. dpkg -i jenkins_2.64_all.deb


Preparing to unpack jenkins_2.64_all.deb ...
Unpacking jenkins (2.64) over (2.64) ...
dpkg: dependency problems prevent configuration of jenkins:
 jenkins depends on daemon; however:
  Package daemon is not installed.


dpkg: error processing package jenkins (--install):
 dependency problems - leaving unconfigured
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 jenkins




3.  apt-get install gdebi-core


4.  apt-get -f install


5.  gdebi jenkins_2.64_all.deb


Error
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: daemon

---

### Post by sfenech2 on 2017-06-06
One more note.

When I run apt policy daemon I get the following.

daemon:
  Installed: (none)
  Candidate: (none)
  Version table:


I tried apt-get install daemon but got the following error.  Know the name of the package I need?  

Package daemon is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'daemon' has no installation candidate

---

### Post by sfenech2 on 2017-06-06
Issue resolved  

I ran grep universe /etc/apt/sources.list and it was blank so ran add-apt-repository universe then had the following.  After that my issue was fixed.   


/etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted univers
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe


Ran apt-get install jenkins worked.

---

### Post by again? on 2017-06-06
Good... you can mark the thread as solved by clicking on "Thread Tools"
Odd that the universe repo was not enabled. Thought it was enabled by default.

---

