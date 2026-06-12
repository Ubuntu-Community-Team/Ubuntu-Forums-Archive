---
title: "can not update software"
date: 2013-08-02
forum: General Help
---

### Post by dennisofnewport on 2013-08-02
When I try to update my software I get this message

The package system is broken 

Check if you are using third party repositories. If so disable them, since they are a common source of problems.  Furthermore run the following command in a Terminal: apt-get install -f

when I press details I get this

The following packages have unmet dependencies: 

wine1.6: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7.1 is installed 
         Depends: libc6 (>= 2.11) but 2.15-0ubuntu10.4 is installed 
         Depends: wine1.6-i386 (= 1.6~rc2-0ubuntu1~ppa4) but 1.6~rc2-0ubuntu1~ppa1 is installed 
wine1.6-i386: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.1.2ubuntu7.1 is installed 
              Depends: libc6 (>= 2.11) but 2.15-0ubuntu10.4 is installed 
              Depends: libglib2.0-0 (>= 2.12.0) but 2.32.3-0ubuntu1 is installed 
              Depends: libgphoto2-2 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed 
              Depends: libgphoto2-port0 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed 
              Depends: liblcms1 (>= 1.15-1) but 1.19.dfsg-1ubuntu3 is installed 
              Depends: libldap-2.4-2 (>= 2.4.7) but 2.4.28-1.1ubuntu4.2 is installed 
              Depends: libmpg123-0 (>= 1.6.2) but 1.12.1-3.2ubuntu1 is installed 
              Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is installed 
              Depends: libpulse0 (>= 1:0.99.1) but 1:1.1-0ubuntu15.3 is installed 
              Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.4 is installed 
              Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed 
              Depends: wine1.6 (= 1.6~rc2-0ubuntu1~ppa1) but 1.6~rc2-0ubuntu1~ppa4 is installed 

when I run   apt-get install -f

I get this

dennisofnewport@dennisofnewport-H61MLV:~$ apt-get install -f 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) 
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 
dennisofnewport@dennisofnewport-H61MLV:~$

---

### Post by deadflowr on 2013-08-02
Run the apt-get install -f command again with sudo in front.
It needs to be run as root.

---

### Post by ian-weisser on 2013-08-02
> **dennisofnewport said:**
> wine1.6: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7.1 is installed 

The system telling you that you seem to have a PPA enabled. 
A wine PPA.
An old wine PPA.
Disable it.
Go into your Software Sources (software-properties-gtk), look for the Other Software tab, find the wine PPAs and uncheck it (them).
If in doubt, uncheck *all* Other Software.

---

### Post by dennisofnewport on 2013-08-02
thanks for the help

I used the sudo command 
and got this 

dennisofnewport@dennisofnewport-H61MLV:~$ sudo apt-get install -f
[sudo] password for dennisofnewport: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  wine-gecko1.9
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.6 wine1.6-i386
Suggested packages:
  dosbox
The following packages will be upgraded:
  wine1.6 wine1.6-i386
2 upgraded, 0 newly installed, 0 to remove and 103 not upgraded.
2 not fully installed or removed.
Need to get 0 B/26.0 MB of archives.
After this operation, 1,034 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-i386 (= 1.6~rc2-0ubuntu1~ppa4); however:
  Version of wine1.6-i386 on system is 1.6~rc2-0ubuntu1~ppa1.
dpkg: error processing wine1.6 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of wine1.6-i386:
 wine1.6-i386 depends on wine1.6:any (= 1.6~rc2-0ubuntu1~ppa1); however:
  Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa4.
dpkg: error processing wine1.6-i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 wine1.6
 wine1.6-i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
dennisofnewport@dennisofnewport-H61MLV:~$ ^C


not sure what Software Sources (software-properties-gtk), is or how to get there.

---

### Post by GwL3eNC on 2013-08-02
Hi,

i think he means in the software-center menu. There you can add or delete repositorys.

---

### Post by dennisofnewport on 2013-08-08
thank you for your help. I am now able to update .  I still do not know how to change the headind of this post to SOLVED

---

### Post by Bashing-om on 2013-08-08
Thread Tools -top of post - drop-down -> Mark thread as solved.

Just try'n to help

---

### Post by deadflowr on 2013-08-08
After thought

> [COLOR=#000000]not sure what Software Sources (software-properties-gtk), is or how to get there.[/COLOR]

Typing software-properties-gtk in normal Ubuntu terminal will open the Software Sources application.
Not sure about Lubuntu, though. Never tried it.

---

