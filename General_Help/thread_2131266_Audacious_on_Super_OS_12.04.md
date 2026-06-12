---
title: "Audacious on Super OS 12.04"
date: 2013-04-01
forum: General Help
---

### Post by Nikolai D. on 2013-04-01
Hi all,

Im trying to install audacious on Super OS 12.04.
What i get in terminal is the following:
ndo@ThinkSuper:~$ sudo apt-get install audacious audacious-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
audacious is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacious-plugins : Depends: libavcodec53 (>= 6:0.8.3-1~) but it is not going to be installed or
                              libavcodec-extra-53 (>= 6:0.8.5) but 4:0.8.5ubuntu0.12.04.1 is to be installed
                     Depends: libavformat53 (>= 6:0.8.3-1~) but it is not going to be installed or
                              libavformat-extra-53 (>= 6:0.8.5) but 4:0.8.5ubuntu0.12.04.1 is to be installed
                     Depends: libavutil51 (>= 6:0.8.3-1~) but it is not going to be installed or
                              libavutil-extra-51 (>= 6:0.8.5) but 4:0.8.5ubuntu0.12.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.
ndo@ThinkSuper:~$ 

Any suggestions? :)

Thanks is advance,
Nikolai

---

### Post by tgalati4 on 2013-04-01
You have a dependency issue.  Was there a PPA that you installed for audacious?

According to:

tgalati4@Mint14-Extensa ~ $ apt-cache policy libavcodec53
libavcodec53:
  Installed: 6:0.8.5-0ubuntu0.12.10.1
  Candidate: 6:0.8.5-0ubuntu0.12.10.1
  Version table:
 *** 6:0.8.5-0ubuntu0.12.10.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     6:0.8.3-6ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages


It looks like you have an *audacious* from 12.10 and you are trying to install on a 12.04 system.  That won't work.  Try looking for the 12.04 version of the package.  Remove any 12.10 references in your /etc/apt/sources.list.

---

### Post by Randymanme on 2013-04-23
[Nikolai D.]("http://ubuntuforums.org/member.php?u=462454")   May I ask how/where you got Super OS 12.04?  Did you just upgrade 11.10 with the Ubuntu Update Manager?

---

### Post by Randymanme on 2013-04-23
Never mind, I see now:  [http://ubuntuforums.org/showthread.php?t=2119226&highlight=super+os+12.04](http://ubuntuforums.org/showthread.php?t=2119226&highlight=super+os+12.04)

---

