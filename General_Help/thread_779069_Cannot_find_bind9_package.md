---
title: "Cannot find bind9 package"
date: 2008-05-02
forum: General Help
---

### Post by spark01 on 2008-05-02
I am trying to use the command apt-get install bind9 and I keep getting this error.

root@susy-desktop:/home/susy# apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bind9 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  dnsutils
E: Package bind9 has no installation candidate

I have also tried looking in the synaptic package manager but I cannot find it there either. I did find bind9-host, is this the same as the bind9 package at all?

---

### Post by honeydew on 2008-05-02
thats strange, what are your repositories like(/etc/apt/sources.list)?  are you using hardy?

austin@underling:~$ aptitude search bind
p   authbind                                                                - Allows non-root programs to bind() to low ports                                  
p   bibindex                                                                - Fast lookup in BibTeX bibliography data bases                                    
p   bind9                                                                   - Internet Domain Name Server                                                      
p   bind9-doc                                                               - Documentation for BIND                                                           
i   bind9-host                                                              - Version of 'host' bundled with BIND 9.X   

as you can see.. I am using default repositories and it is available...

---

### Post by spark01 on 2008-05-02
I am running Gusty and this is what my sources.list file looks like:

root@susy-desktop:/var/lib/apt/lists# cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Monicker on 2008-05-02
Seems like there have been some issues with ca.archive.ubuntu.com

[http://ubuntuforums.org/showthread.php?t=775729]("http://ubuntuforums.org/showthread.php?t=775729")


I would try an update, and see if you can get a better listing of packages from them:

```
sudo apt-get update
```


If that does not help then you may want to try a different repository.

---

### Post by spark01 on 2008-05-02
I have already tried doing an update with no luck :( Any other idea's?

---

### Post by Monicker on 2008-05-02
> **spark01 said:**
> I have already tried doing an update with no luck :( Any other idea's?

Did you try a different repository?  There should be others to choose from in Synaptic.

---

### Post by spark01 on 2008-05-02
Sorry 
I am very new to linux and ubuntu...how do I try different repositories?

---

### Post by Monicker on 2008-05-02
> **spark01 said:**
> Sorry 
I am very new to linux and ubuntu...how do I try different repositories?


System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.

Click to the right of "Download from" and select Other.  Then you can scroll to the section for Canada and pick one of the other repositories.

Or you can try the "Select Best Server" option after you have done "Other" from above, and let it pick one for you.

---

### Post by honeydew on 2008-05-02
or you can sudo gedit /etc/apt/sources.list 

then use the search and replace feature to change all of the ca. to us.

---

### Post by sanjayak on 2011-01-31
This happen to me too. But when I did "sudo apt-get update" it got fixed.

---

