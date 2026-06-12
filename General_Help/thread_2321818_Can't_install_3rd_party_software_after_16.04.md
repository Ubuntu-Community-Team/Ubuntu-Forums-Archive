---
title: "Can't install 3rd party software after 16.04"
date: 2016-04-24
forum: General Help
---

### Post by David4321 on 2016-04-24
I just finished a clean install of 16.04 after some hardware changes, and I'm reconstructing system. Having trouble getting software center to install any 3rd party software, google chrome and teamviewer so far, I bet Skype will hang too. I checked all the obvious settings. I don't want to have to look up and add repositories one by one, I never had to do that before upgrade, and I try to minimize terminal use. What's the fix? Thanks!

---

### Post by truck87brp on 2016-04-25
install GDebi package installer...got some to work with it...this sucks!

---

### Post by QIII on 2016-04-25
There is no official guarantee that any third party repositories have been maintained, nor that a version compatible with Xenial has been produced.

Third party software is just that.

---

### Post by QDR06VV9 on 2016-04-25
Just encase to install Skype on Xenial
[https://linuxconfig.org/how-to-install-skype-on-ubuntu-16-04-xenial-xerus-linux-64-bit](https://linuxconfig.org/how-to-install-skype-on-ubuntu-16-04-xenial-xerus-linux-64-bit)
And I also agree with installing gdebi.
Regards

---

### Post by grahammechanical on 2016-04-25
Skype 4.3 is in the 16.04 repositories. So, is Google Chrome at version 50. Synaptic Package Manager shows both. But not Teamviewer. Was it ever in a Ubuntu software repository? Was it not always required to download from the Teamviewer web site?

Ubuntu Software Centre has been replaced by Gnome Software (re-branded Ubuntu software) and its software catalogue is still under construction. And we do need the partner repositories enabled.

Regards

---

### Post by Jack_Roman on 2016-04-25
I have the same problem as others mentioned here installing third party software. Funny thing, Ubuntu ver 15.04 never had this issue. As some have said, work around for now is using Gdebi Package Installer. Still, this is very frustrating for such a brand new release!

---

### Post by QIII on 2016-04-25
Again:  Canonical does not maintain 3rd party software.  Don't blame Ubuntu if the people who should be maintaining them don't.

---

### Post by Jack_Roman on 2016-04-26
That's not a helpful answer particularly when the Software Center in ver 15.04 never had this issue. By the way, I ran into the same problem trying to re-install the drivers for my Pantum wireless printer and had to find a workaround for that one as well. I feel for users of Ubuntu who may not be as resourceful in finding answers as some others have been. I do know there were several tickets created in Ubuntu bugzilla, most notably bug ticket#1573206 and a few others. So, this is an issue I am sure they're going to resolve.

---

### Post by QIII on 2016-04-26
What the software center did in 15.04 may or may not have any bearing whatsoever.

---

### Post by howefield on 2016-04-26
As posted by sahashinjan in another thread, [here is the relevant bug]("https://bugs.launchpad.net/ubuntustudio/+bug/1573206"). Go mark it as "affecting me too"  :)

---

### Post by QIII on 2016-04-26
Ah!  Then I retract my statements!

---

### Post by David4321 on 2016-04-26
Gdebi was good workaround, nice! Thanks for posting the bug howefield! 

For clarity, I was just talking about using software center to install 3rd party software which I downloaded myself, like it always used to. 

Delays on this stuff are understandable, no one is talking about guarantees or attacking Canonical. But *yuk* QIII, your responses sound like corporate blow-offs, no empathy. Please tone down the defensiveness, we're all just here trying to resolve our issues in community. Thanks.

---

### Post by stephanvaningen on 2016-04-27
I have also the problem that a lot of repositories are not consulted during an apt-get update, resulting in errors like "no installation candidate", even when installing someting trivial like php5.

I think the universe and mulitverse repos are not active in apt after clean install/upgrade??? How can I add them?

---

### Post by mc4man on 2016-04-27
> **stephanvaningen said:**
> I have also the problem that a lot of repositories are not consulted during an apt-get update, resulting in errors like "no installation candidate", even when installing someting trivial like php5.

I think the universe and mulitverse repos are not active in apt after clean install/upgrade??? How can I add them?

Check Software & Updates, do note there is no such package named php5

---

### Post by stephanvaningen on 2016-04-27
It's really odd, because my sources.list looks complete:
```
 # deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
# deb-src http://be.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
# deb-src http://be.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu xenial universe
# deb-src http://be.archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe
# deb-src http://be.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

But anyway, if I do apt-get update, I  get this result:

```
beheerder@drupal-sandbox:/etc/apt$ sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Hit:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                
Hit:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease [92,2 kB]
Fetched 92,2 kB in 0s (97,4 kB/s)                              
Reading package lists... Done
beheerder@drupal-sandbox:/etc/apt$ 

```

Am I missing something in my understanding here?

---

### Post by stephanvaningen on 2016-04-27
Thans for replying mc4man, I indeed see there is no such package, but in my previous installations I did have this package; and numerous other packages, which are now all just not available...

---

### Post by stephanvaningen on 2016-04-27
Ow man, it seems that php5 is replaced with php7; and packages which were dependant on php5 (i.e. drupal7) are not updated for php7 yet: so that is the explanation from my side... I'ld sugest to mark this thread as [solved]...
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#PHP_7.0](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#PHP_7.0)

---

### Post by Krause on 2016-04-27
> **stephanvaningen said:**
> I have also the problem that a lot of repositories are not consulted during an apt-get update, resulting in errors like "no installation candidate", even when installing someting trivial like php5.

I think the universe and mulitverse repos are not active in apt after clean install/upgrade??? How can I add them?

I've seen a few packages that were not in software center but were available for install via apt (steam for instance). I don't remember it being like that before.

---

### Post by stephanvaningen on 2016-04-28
Just for completeness; this article describes the bug that others in the thread have been experiencing. Expect a fix in a few days...
  [http://www.omgubuntu.co.uk/2016/04/ubuntu-16-04-deb-software-install-error](http://www.omgubuntu.co.uk/2016/04/ubuntu-16-04-deb-software-install-error)

---

### Post by Hewjr100 on 2016-04-28
No google chrome in ubuntu 16.04 software.

Henry

---

### Post by howefield on 2016-04-30
> **Hewjr100 said:**
> No google chrome in ubuntu 16.04 software.

Chrome has never been available from the Ubuntu repositories, the Chrome .deb package has to downloaded from the Chrome website, then it can be installed locally.

---

