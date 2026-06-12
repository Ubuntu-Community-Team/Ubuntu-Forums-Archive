---
title: "Repositories Problem"
date: 2006-12-13
forum: General Help
---

### Post by ofir_k on 2006-12-13
Hello,

I encountered a weird problem which getting worse and worse.

My problem started immediately after I changed beryl repository from "deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy-main main" to "deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main". Since then, I can't update my system, download applications and reload repositories applications.

**_I get the following messages:_**
_When opening Synaptic_
> E: Malformed line 39 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

_When reloading the packages information_
1.
> Could not download all repository indexes
-----------------------------------------
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

2.
> E: Malformed line 39 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory

_When opening update manager_
The update manager just open and then immediately closing.

**_sources.list file:_**
> 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy-main main

Thanks in advance.

Regards,
Ofir

P.S
Just for the protocol, I searched the forums (more then one time!).

---

### Post by Johan! on 2006-12-13
The last line of the sources.list file has to be blank.
So open the file in gedit or nano, go to the end of the file, and press Enter  one or more times.

---

### Post by jocko on 2006-12-13
>  			 				E: Malformed [COLOR=Red]**line 39**[/COLOR] in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory

I think I see your error.
If I'm not mistaken this is your line 39 (the bottom of your file)
```
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy-main main
```
This is wrong. It should be:
```
 deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
```

---

### Post by ofir_k on 2006-12-13
I followed your instructions (added a new line at the end of the file and replaced the last line), and I still get the same problem:
> E: Malformed line 39 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by jocko on 2006-12-13
edit: I didn't read properly, forget this post...

---

### Post by igknighted on 2006-12-13
Could a lockfile still be open somewhere so even if it gets repaired it wont work?

---

### Post by ofir_k on 2006-12-13
> **igknighted said:**
> Could a lockfile still be open somewhere so even if it gets repaired it wont work?

What do you mean? What is it lockfile?

---

### Post by jocko on 2006-12-13
**NOW** I found your problem.
the second to last line is wrong:
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR=Red]edgy[/COLOR]
```I tried putting it in my sources.list and got the same error as you. There should be something after "[COLOR=Red]edgy[/COLOR]" (i.e. main restricted multiverse universe). Just remove/comment that line and you should be fine.

---

### Post by ofir_k on 2006-12-13
Thanks jocko! I just deleted that entry (deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy), as you instructed me, and it works.

I have one more question: Will all applications remain or some of them will gone?

And thanks again!!!

---

### Post by ofir_k on 2006-12-13
BTW, I also get the error below each time I install, delete or reinstall packages:
> E: graphviz-cairo: subprocess post-installation script returned error exit status 127

What is it graphviz-cairo and why am I getting this error?

Regards,
Ofir

---

### Post by jocko on 2006-12-13
> **ofir_k said:**
> Thanks jocko! I just deleted that entry (deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy), as you instructed me, and it works.

I have one more question: Will all applications remain or some of them will gone?

And thanks again!!!

You're welcome! I'm glad I could help.

I think your problem was that part of that line was accidentally deleted, so you probably want to find out which repo it was and add it again. It looks like what's missing is  "multiverse"

A tip: If the "[il.archive.ubuntu.com]("http://il.archive.ubuntu.com/ubuntu/")"  mirror is the fastest for you, you can replace your entire list with this (it has all the same repos as your old one, as far as I can see):
```

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy-main main

```This way you have all the repos from the fastest mirror instead of having some of them from the "il" mirror and some others from the international mirror, and you get back the one that seems to be lost. If you find the international mirror is faster, just change all "[http://il.archive.]("http://il.archive.ubuntu.com/ubuntu/")" to "[http://archive.]("http://il.archive.ubuntu.com/ubuntu/")".

---

### Post by ofir_k on 2006-12-13
Ok... The whole system seems to work. I hope that I won't encounter more problems.

Thanks again for your instance help!

---

### Post by TooRight on 2006-12-15
nevermind, wrong thread :D

---

### Post by Cariboo1938 on 2007-01-10
When I reload my repositories in -->Synaptic Package Manager -->Settings -->Repositories I get the following error message:> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[COLOR="Red"][http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)[/COLOR] I never know if my updates are complete or faulty. What is wrong? Here is my sources.list
> ### Original /etc/apt/sources.list ###  
### added Automatix Repos. November 2006 ###
### added KDE.org Repositories. November 2006 ###
### added Beryl-Project.org Repos. December 2006
#
### Ubuntu MAIN ###
#
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
#
### Ubuntu BUG FIX UPDATES ###
#
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
#
### Ubuntu UNIVERSE ###
#
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
#
### Ububtu BACKPORTS ###
#
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
#
### Ubuntu SECURITY UPDATES ###
#
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#
### Kubuntu.org repositories. Packages for the latest KDE version ###
#
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main
deb [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) edgy main
# deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main
#
### Ubuntu BERYL- PROJECT ###
#
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
#
### AUTOMATIX REPOS START ###
#
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#
### AUTOMATIX REPOS END ###


---

### Post by Cariboo1938 on 2007-01-12
Bummmm...](*,) 
Any reply or opinion on that issue is highly appreciated...
Thanks

---

