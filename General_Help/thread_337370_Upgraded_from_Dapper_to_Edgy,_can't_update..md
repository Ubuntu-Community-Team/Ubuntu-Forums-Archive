---
title: "Upgraded from Dapper to Edgy, can't update."
date: 2007-01-12
forum: General Help
---

### Post by tsav87 on 2007-01-12
I am having a trouble updating with the update manger.  One, I am only able to install one of the upgrades, the vmware, but I get an error at the end of the install.

I did just upgrade to Edgy from Dapper.  Everything else seems to be working fine.

Here are some screen shots of the error and the bug report.

---

### Post by obsidion on 2007-01-12
> **tsav87 said:**
> I am having a trouble updating with the update manger.  One, I am only able to install one of the upgrades, the vmware, but I get an error at the end of the install.

I did just upgrade to Edgy from Dapper.  Everything else seems to be working fine.

Here are some screen shots of the error and the bug report.


  First thing I would try is from a terminal sudo apt-get update and see if it throws any errors at you.

   IF it does or doesn't you need to see where and at what your /etc/apt/sources.list points. It may be that for some reason this has been overwritten or just not point at the right repos.

---

### Post by tsav87 on 2007-01-12
here's what the source list looks like.
```

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main

# deb http://wine.lowvoice.nl/apt dapper main

deb http://www.getautomatix.com/apt dapper main

# deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
#AUTOMATIX REPOS END


```

---

### Post by obsidion on 2007-01-12
You didn't say you had automatix installed, that has borked 3 installs I have done on my computers and a few others on other peoples that I have had to fix because of it. Sorry you are on your own, I won't touch  an install using that anymore.

---

### Post by tsav87 on 2007-01-12
Should I remove it and the repos?

---

### Post by obsidion on 2007-01-12
> **tsav87 said:**
> Should I remove it and the repos?


  I would at least until you get things back on an even keel.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

  You could try installing a new repo list using this tool to generate it.

---

### Post by arnieboy on 2007-01-15
> **obsidion said:**
> You didn't say you had automatix installed, that has borked 3 installs I have done on my computers and a few others on other peoples that I have had to fix because of it. Sorry you are on your own, I won't touch  an install using that anymore.
good for you sir. surely you didnt try and figure out what **REALLY** broke your upgrades before giving such great advice.

---

### Post by arnieboy on 2007-01-15
> **tsav87 said:**
> I am having a trouble updating with the update manger.  One, I am only able to install one of the upgrades, the vmware, but I get an error at the end of the install.

I did just upgrade to Edgy from Dapper.  Everything else seems to be working fine.

Here are some screen shots of the error and the bug report.

The other person who gave you such great advice on what to do obviously does not have a clue about what exactly went wrong.
The issue you are facing is because of a broken vmware-player package in Ubuntu Multiverse which the package maintainer has not bothered fixing in 4 months (so much for another n00b blaming automatix for it).  
Just do the following to fix the issue:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postinst
sudo apt-get remove vmware-player
```
and check to see if the error appears again.
If its **not fixed**, try the following:```

sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo apt-get remove vmware-player
```

---

### Post by saultpastor on 2007-01-16
Tried both fixes, still no joy :( 

I can't uninstall it and I can't install it both give me errors and it has broken my updates.

Any other ideas?

thanks

---

### Post by arnieboy on 2007-01-16
> **saultpastor said:**
> Tried both fixes, still no joy :( 

I can't uninstall it and I can't install it both give me errors and it has broken my updates.

Any other ideas?

thanks

paste the errors from
```
sudo apt-get update
```

---

### Post by saultpastor on 2007-01-16
Thx

No errors though?

---

### Post by arnieboy on 2007-01-16
huh?
if there are no errors then the issue is fixed.
The package itself is broken as I mentioned previously.

---

### Post by saultpastor on 2007-01-16
```
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

This from update manager

running sudo apt-get install -f
 it wants to install vmware-player :( 

it seems I'm stuck

---

### Post by obsidion on 2007-01-16
> **arnieboy said:**
> good for you sir. surely you didnt try and figure out what **REALLY** broke your upgrades before giving such great advice.

  Well yes I did and managed to fix the faults however after being bitten 3 times by it on different systems I will not use it again. If you want to call me a noob because I prefer to do things myself and won't use a noob tool like automatix then it is hardly skin off my nose. However since I have been using linux as my full time OS for 6 years so I am hardly a noob. Keep your insults and your noob tool to yourself it isn't for me. 

  I wasn't insulting to your precious tool so don't be insulting to me by calling me noob when you know nothing of me or my linux experiance.

---

### Post by arnieboy on 2007-01-16
> **saultpastor said:**
> ```
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

This from update manager

running sudo apt-get install -f
 it wants to install vmware-player :( 

it seems I'm stuck
what does
```
sudo apt-get remove vmware-player
```
give?

---

### Post by saultpastor on 2007-01-16
> Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

Same error

---

### Post by saultpastor on 2007-01-16
maybe if I reinstall dpkg?

---

### Post by arnieboy on 2007-01-16
> **obsidion said:**
> Well yes I did and managed to fix the faults however after being bitten 3 times by it on different systems I will not use it again. If you want to call me a noob because I prefer to do things myself and won't use a noob tool like automatix then it is hardly skin off my nose. However since I have been using linux as my full time OS for 6 years so I am hardly a noob. Keep your insults and your noob tool to yourself it isn't for me. 

  I wasn't insulting to your precious tool so don't be insulting to me by calling me noob when you know nothing of me or my linux experiance.

The fact that you are a newbie is obvious from the fact that you refuse to step down from your opinion that automatix broke your upgrades. If you had really investigated the cause, you would have found broken packages from unsafe third party and Ubuntu official repositories. 

I have noticed you giving unqualified opinions about automatix with gay abandon in many threads (not just this one). You can very well choose to do whatever you want and not use Automatix but its not very mature to dissuade others from using something which is making Ubuntu as popular as it is just because you think you should do things manually. Linux is about choice. Let them choose what they want. You do not need to press down your ill-formed opinion on them.

I am not insulting you. Everyone starts somewhere. However, being deeply opinionated and slighting others efforts never achieves much. When your upgrades broke, you should have probably emailed me or someone on the Automatix Team and we would have helped you confirm the real reason of the breakage.

---

### Post by arnieboy on 2007-01-16
> **saultpastor said:**
> maybe if I reinstall dpkg?

no that wont help
paste the result of the following command:
```
ls /var/lib/dpkg/info/*vmware*
```

---

### Post by saultpastor on 2007-01-16
> paste the result of the following command:

```
/var/lib/dpkg/info/vmware-player.conffiles
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.list
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.md5sums
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.postinst
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.postrm
/var/lib/dpkg/info/vmware-player.list
/var/lib/dpkg/info/vmware-player.md5sums
/var/lib/dpkg/info/vmware-player.preinst
/var/lib/dpkg/info/vmware-player.prerm
/var/lib/dpkg/info/vmware-player.templates
/var/lib/dpkg/info/xserver-xorg-video-vmware.list
/var/lib/dpkg/info/xserver-xorg-video-vmware.md5sums

```

---

### Post by arnieboy on 2007-01-16
alright try the following:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo apt-get remove vmware-player
```

---

### Post by saultpastor on 2007-01-16
First one worked

Everything working fine no more errors!

Thanks much arnieboy You da man!:)

---

### Post by arnieboy on 2007-01-16
> **saultpastor said:**
> First one worked

Everything working fine no more errors!

Thanks much arnieboy You da man!:)

glad to have been of help.

---

### Post by obsidion on 2007-01-16
>The fact that you are a newbie is obvious from the fact that you refuse to step down from your opinion that >automatix broke your upgrades. If you had really investigated the cause, you would have found broken >packages from unsafe third party and Ubuntu official repositories. 

  Yes like automatix, ie a third party package.
Yes I did and fixed it myself without help from your precious automatic system breaker


>I have noticed you giving unqualified opinions about automatix with gay abandon in many threads (not just >this one). 

My opinions are from personal experience and therefore qualified.
I notice you and others telling all and sundry that the answer to all their install problems and failure to get things working is automatix, does that make you right and me wrong ?

>You can very well choose to do whatever you want and not use Automatix but its not very mature to >dissuade others from using something which is making Ubuntu as popular as it is just because you think >you should do things manually. 

  Nor is it mature to insist that it is a wonder tool and will fix all codecs without ever making the effort to read what the problem is for that person as I have seen many times in these forums.


>I am not insulting you. Everyone starts somewhere.

  Calling me a noob is insulting to me. While I am no expert and don't claim to be calling me a noob, because from personal experience your tool broke some sytems I know of and have used, doesn't say much for your ability to accept that your tool can be at fault. 
  Maybe your tool has advanced since I last used it and I admire your persiverence with it, it really isn't the answer to all problems and can cause more than it fixes.


> However, being deeply opinionated and slighting others >efforts never achieves much. When your >upgrades broke, you should have probably emailed me or >someone on the Automatix Team and we would >have helped you confirm the real reason of the breakage.

  Yes emailed you with the problems on the first machine and you tried to tell me that my sources list was pointing at an unsafe 3rd party repo. It wasn't and I told you this and then got no further answer.


  It is precious people like you that seem to infest ubutu that is quickly turning me off this distro.
I won't let you do that instead I will probably just leave thes forums and let you and your broken software turn more people awy from the distro. There that insulting enough for you.

---

### Post by arnieboy on 2007-01-16
> **obsidion said:**
>   Yes like automatix, ie a third party package.
Yes I did and fixed it myself without help from your precious automatic system breaker
Childish rant.

> **obsidion said:**
> My opinions are from personal experience and therefore qualified.
We often form wrong opinions from events in our personal lives because we arent keen enough to figure out the real reasons. Hence our opinions dont amount to much. 
> **obsidion said:**
> I notice you and others telling all and sundry that the answer to all their install problems and failure to get things working is automatix, does that make you right and me wrong ?
I do not personally tell anyone to use automatix. Automatix gets recommended by the community because of overwhelmingly positive feedback.

> **obsidion said:**
> Nor is it mature to insist that it is a wonder tool and will fix all codecs without ever making the effort to read what the problem is for that person as I have seen many times in these forums.
As I said.. I never made any blind recommendations. However, most new users have found Automatix to be a panacea as opposed to following poorly written  and often incorrect wiki articles.

> **obsidion said:**
> Calling me a noob is insulting to me. While I am no expert and don't claim to be calling me a noob, because from personal experience your tool broke some sytems I know of and have used, doesn't say much for your ability to accept that your tool can be at fault. 
  Maybe your tool has advanced since I last used it and I admire your persiverence with it, it really isn't the answer to all problems and can cause more than it fixes.
same baseless rant continuing. I apologize for calling you a "n00b" but you do come across as an extremely green user who is also extremely confident about his opinions. 

 > **obsidion said:**
> Yes emailed you with the problems on the first machine and you tried to tell me that my sources list was pointing at an unsafe 3rd party repo. It wasn't and I told you this and then got no further answer.
You seem to have joined in December 2006. I do not remember having received any email from you. Please resend me the email. 


 > **obsidion said:**
> It is precious people like you that seem to infest ubutu that is quickly turning me off this distro.
I won't let you do that instead I will probably just leave thes forums and let you and your broken software turn more people awy from the distro. There that insulting enough for you.

MORE infantile ranting..

---

### Post by obsidion on 2007-01-16
It wasn't to you personaly I used you in the collective term as in the manufacturers. This was months ago btw.
 It was thrice bitten twice shy so to speak. I won't be using it again and again I didn't mean you as in you personally reccomending it but as a collective term for those adherents of it. However you last post has done the trick. Ubuntu is gone, have your satifaction and keep your politically correct distro I've had enough of it and these forums.

---

### Post by arnieboy on 2007-01-16
> **obsidion said:**
> Ubuntu is gone, have your satifaction and keep your politically correct distro I've had enough of it and these forums.
good luck.

---

### Post by darweth on 2007-01-16
> **obsidion said:**
> It wasn't to you personaly I used you in the collective term as in the manufacturers. This was months ago btw.
 It was thrice bitten twice shy so to speak. I won't be using it again and again I didn't mean you as in you personally reccomending it but as a collective term for those adherents of it. However you last post has done the trick. Ubuntu is gone, have your satifaction and keep your politically correct distro I've had enough of it and these forums.

This post shows us where you are coming from.  I personally have no use for Automatix and would never recommend it to anyone, but to drop an entire OS due to a dispute on the forums with someone who has nothing to do with anything... wow.  [-( [-(

---

