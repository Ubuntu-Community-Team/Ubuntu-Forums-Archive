---
title: "Very Old Version of Lazarus"
date: 2016-01-27
forum: General Help
---

### Post by gga96 on 2016-01-27
I have written Lazarus/FPC code on Windows using V1.4.4/2.6.4 and it is very good development package.

I have installed Ubuntu and would like to use Lazarus/FPC on this machine and move away from Windows. 
Unfortunately the available version of Lazarus on Ubuntu is very old and the package is streets behind the latest version.

I am new to Linux and do not understand why I cannot install the most up to date versions here?

Lazarus and Free Pascal are fine examples of Open Source software.

Can you help me to install version 1.4.4/2/6/4 on this Ubuntu machine or do I have to move to another distribution.

Hope to hear from you soon and thanks for you help.

Regards
Glen

---

### Post by Bucky Ball on 2016-01-27
*Thread moved to **General Help**.*

Have you done some research about this? There seems to be [a lot of how-tos]("https://duckduckgo.com/?q=lazarus+ubuntu+14") on how to install Lazarus on 14.04. Any clues there?

I just looked in the repos and on 14.04 I have Lazarus version 1.0.10 available. You don't say which release you are using but probably a newer version in a newer release of Ubuntu.

---

### Post by gga96 on 2016-01-27
Hi Bucky Ball

Thank you.

Yes my version of Ubuntu is 14.04 and both the Software Updater and Synaptic Package Manager both refer to Lazarus as version 1.0.10.  The stable release of Lazarus is now at 1.4.4 with 1.6 as a release candidate.

I would prefer to stay with 14.04 if possible, it is stable and I have MythTV 0.27 installed.

Being a novice to Linux I do not understand the prerequisites and dependencies involved. 

What are the problems of installing upgraded versions?

Thank you again.

Glen

---

### Post by gga96 on 2016-01-27
I am not on my own over this issue.

I found this link [https://github.com/ubuntu/ubuntu-make/issues/149](https://github.com/ubuntu/ubuntu-make/issues/149) it discusses the issue.

The 4th post:
```
                 **       [mdalacu]("https://github.com/mdalacu")     **      commented      [       on 12 Nov 2015     ]("https://github.com/ubuntu/ubuntu-make/issues/149#issuecomment-156046142")   

 
                             The debs are available on their website ([http://www.lazarus-ide.org/index.php?page=downloads](http://www.lazarus-ide.org/index.php?page=downloads)), but someone needs to remove the fpc conflicting package form Ubuntu repository.

       
     
    
 

```  

Is this not possible?

Glen

---

### Post by mastablasta on 2016-01-27
use a PPA: [https://launchpad.net/ubuntu/+source/lazarus](https://launchpad.net/ubuntu/+source/lazarus)

same method on their instructions:  [http://wiki.freepascal.org/Lazarus_release_version_for_Ubuntu](http://wiki.freepascal.org/Lazarus_release_version_for_Ubuntu)

---

