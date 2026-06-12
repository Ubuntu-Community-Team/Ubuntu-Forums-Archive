---
title: "tomcat installection ?????"
date: 2007-11-30
forum: General Help
---

### Post by myharshdesigner on 2007-11-30
when i try this :-

[PHP]
sudo apt-get install tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
[/PHP]

after this i got en error :-

[PHP]
harsh@harsh-laptop:~$ sudo apt-get install tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
[sudo] password for harsh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libtomcat5.5-java
Suggested packages:
  libapache-mod-jk libapache2-mod-jk
The following NEW packages will be installed:
  libtomcat5.5-java tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
0 upgraded, 4 newly installed, 0 to remove and 121 not upgraded.
Need to get 0B/5108kB of archives.
After unpacking 14.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libtomcat5.5-java.
(Reading database ... 104433 files and directories currently installed.)
Unpacking libtomcat5.5-java (from .../libtomcat5.5-java_5.5.25-1ubuntu1_all.deb) ...
Selecting previously deselected package tomcat5.5.
Unpacking tomcat5.5 (from .../tomcat5.5_5.5.25-1ubuntu1_all.deb) ...
Selecting previously deselected package tomcat5.5-admin.
Unpacking tomcat5.5-admin (from .../tomcat5.5-admin_5.5.25-1ubuntu1_all.deb) ...
Selecting previously deselected package tomcat5.5-webapps.
Unpacking tomcat5.5-webapps (from .../tomcat5.5-webapps_5.5.25-1ubuntu1_all.deb) ...
Setting up libtomcat5.5-java (5.5.25-1ubuntu1) ...
Setting up tomcat5.5 (5.5.25-1ubuntu1) ...
Adding system user `tomcat55' (UID 110) ...
Adding new user `tomcat55' (UID 110) with group `nogroup' ...
Not creating home directory `/usr/share/tomcat5.5'.
 * no JDK found - please set JAVA_HOME
invoke-rc.d: initscript tomcat5.5, action "start" failed.
dpkg: error processing tomcat5.5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tomcat5.5-admin:
 tomcat5.5-admin depends on tomcat5.5 (>= 5.5.25-1ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-admin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tomcat5.5-webapps:
 tomcat5.5-webapps depends on tomcat5.5 (>= 5.5.25-1ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-webapps (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tomcat5.5
 tomcat5.5-admin
 tomcat5.5-webapps
E: Sub-process /usr/bin/dpkg returned an error code (1)
harsh@harsh-laptop:~$ 
[/PHP]

---

### Post by myharshdesigner on 2007-11-30
any one can solve the problem ?

---

### Post by sgordon on 2007-12-03
Should go ok if you have set your java to something up to date.

I would use:
sudo apt-get remove tomcat5.5
(remove broken package)
sudo apt-get install sun-java6-jdk
(install latest JDK from Sun)
sudo update-java-alternatives -s java-6-sun
(set this to be the default for java commands)

Although, can also (or, in addition):
vi /etc/profile
and add

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00/
export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.00/

```
near the end

I think just setting the java alternatives was enough.

Let me know how it goes.

   Si

---

### Post by giacomo on 2007-12-25
it was very useful
thanks

---

