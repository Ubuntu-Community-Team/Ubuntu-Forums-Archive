---
title: "Have two held back packages in the last update apport-kde and software-properties-kde"
date: 2018-09-07
forum: General Help
---

### Post by Butthead on 2018-09-07
Hi,

I have two held back packages (apport-kde and software-properties-kde) in the last upgrade I did (sudo apt update && sudo apt dist-upgrade), which I know are because of some newer python3 (apparently?) packages that were supposedly installed in the past.

Now my question is, should I wait to see if there is a future upgrade that fixes things again, or should I risk screwing up the system trying to roll back the python3 packages that are causing the grief (rendering the system unusable is a REAL possibility when I start trying to repair stuff). :eek: :mad:

Anyone else on the forum here run into this? :confused:

---

### Post by TheFu on 2018-09-08
If you install .deb files manually, outside the package management automatic download system, then in 3-6 months, this sort of dependency issue happens.   The solution is to remove those packages, do the update/upgrade and have allthe other stuff patched, then try to find a reputable, maintained, PPA for the packages you want and use that rather than manually installing .deb files.

A small problem won't get better, but you can wait 1 week to see if it does. Might get lucky.

I've seen that KDE has had lots of active updates recently. They've taken great steps for samba to work better, which will matter to many people.

---

### Post by Butthead on 2018-09-08
From what I can gather from the 1,000 commands I have run so far trying to get those two held back packages to install is that the two python3 files that are needed seem to be slightly old that are currently in the repository:

sudo apt --reinstall install apport-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apport-kde : Depends: python3-apport (>= 2.20.9-0ubuntu7.3) but 2.20.9-0ubuntu7.2 is to be installed
E: Unable to correct problems, you have held broken packages.


udo apt --reinstall install software-properties-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-properties-kde : Depends: python3-software-properties (= 0.96.24.32.5) but 0.96.24.32.4 is to be installed
E: Unable to correct problems, you have held broken packages.
  
I haven't really installed any external .deb files since online upgrading to Bionic 18.04 from Xenial 16.04, the only thing I can think of is that I messed up something somehow trying to remove those two defunct PPA's from Muon.

It's probably not that great an idea to run dist-upgrade either as part of the upgrade process.  I think that might cause a lot of unnecessary problems too.

Anyway, I'll just wait and see if it auto-corrects itself in a future update.  I had enough headaches dealing with it already.

---

### Post by TheFu on 2018-09-08
Pro tip ... try using **aptitude**.  It will try harder to find possible dependency solutions and offer them up.  You can refuse solutions you don't like and others will be presented.

dist-upgrade will install a newer kernel and libc, if available. It will also remove deprecated packages, which is important to counteracting package dependency problems.  upgrade alone will stay on the older kernel line.

From the apt-get manpage:```

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
```

---

### Post by Butthead on 2018-09-08
Thanks, I'll check into aptitude to see if it can fix things for me (maybe tomorrow?), so I won't mark this solved yet.  Someone else recommended it quite highly too, but I'm kind of scared that (in my many readings trying to correct the held back packages problem) it will try and remove python3 packages also (which can be disastrous).

Interesting to know that diet-upgrade seems to be relatively benign too.

Thank you again for all your assistance in this matter!

---

### Post by TheFu on 2018-09-08
If you don't have backups, then you should be scared, but not about aptitude.  At any instance, your system might crash. Without backups, all that data is gone. What happens then?

If you have backups and this technique doesn't work, then you can put things back and try something different. You've lost 30-45 min. Not a big deal.

---

### Post by Butthead on 2018-09-09
Well, since I did the upgrade online, I don't have a physical Kubuntu Bionic 18.04 DVD to reinstall stuff if things go south for me. :(

Probably will need a new Linux computer eventually anyway (running this one daily for 3+ years now for at least 3 hours a night), so I'll just wait until then to get the new software too.

Aptitude proved worthless for me.  It sees the two broken (held back) packages, but won't update or fix them for me.  I get an warning "python3-apport (>=2.20.9@ubuntu7.3) (UNAVAILABLE)" when clicking on one of them (software-properties-kde, I think?:confused:) trying to repair it, and (according to aptitude) "apport-kde" shows up as a Gnome file when you click on it trying to get it repaired too. :rolleyes:

I guess I just have to get used to seeing two held back files when I upgrade from now on.  Everything apparently still works, so... :mad::-\"

---

### Post by TheFu on 2018-09-10
It won't get better and will get worse.   Pay now or pay more later. More upgrades will fail and eventually no programs can be installed.

You can make a DVD or USB Flash drive with 18.04.1, if you like.  You said everything is working. Download the ISO file, have a USB port and 4G flash drive, and the 'dd' program (dd is part of EVERY base Unix distro that I know), then you can make the flash drive to boot.

I would install something like openbox, then remove KDE and all the dependencies for it, then reinstall it. That will likely leave you without a GUI at some point, but at the login screen, just choose openbox with the "gear" icon.  Most ISOs can be run in "repair" mode which will let you handle any that might be borked in an installation. This is a standard, fix anything, method.

BTW, this is mainly a KDE question. I don't use KDE (actually, I don't use any DE), so getting advise from the many people here who do run KDE be helpful. Hopefully, one of them will try to help.

---

### Post by Butthead on 2018-09-10
Naw, that's all too confusing for me.  I'll just order a Kubuntu 18.04 DVD off of EBay and just try reinstalling it.  If that craps out, it's probably time for a new computer + O.S. anyway. :lolflag:

I'm almost wondering now if the two held back packages I'm seeing are a false flag anyway (since all my python3 libraries seem to be the most current versions?).  I could have sworn remember reading somewhere years back that K/Ubuntu will sometimes complain of broken (held back) packages that don't really actually exist, and a fix (can't for the life of me find it now ](*,) :mad: ) that you run to correct it. :confused:

If it starts acting up any worse on me, I'll just be forced to go back to Windows. :eek: :eek: :P

Thanks again for all your help, TheFu.  I really do appreciate it! :guitar:

---

### Post by Butthead on 2018-09-10
Here's my last question about the problem that I hope some K/Ubuntu guru can answer for me:

Seems to (maybe?) fix my apport-kde being held back issues I need for python3-apport (>= 2.20.9-0ubuntu7.3) to be installed, but the Bionic repositories seem to only have python3-apport (>= 2.20.9-0ubuntu7.2) in them currently.

Same with software-properties-kde.  It depends on having python3-software-properties (= 0.96.24.32.5) installed, but the Bionic repositories only seem to have python3-software-properties (= 0.96.24.32.4) in them currently. 

So, my question is is that anyone else running Kubuntu 18.04.1 LTS have the two newer python3 libraries installed?

What could be causing this kerfluffle for me? :confused:

---

### Post by &amp;KyT$0P# on 2018-09-10
> **Butthead said:**
>  the Bionic repositories seem to only have python3-apport (>= 2.20.9-0ubuntu7.2) in them currently.

... the Bionic repositories only seem to have python3-software-properties (= 0.96.24.32.4) in them currently. 
Err, no, they shouldn't -
[https://packages.ubuntu.com/bionic-updates/python3-apport]("https://packages.ubuntu.com/bionic-updates/python3-apport")
[https://packages.ubuntu.com/bionic-updates/python3-software-properties]("https://packages.ubuntu.com/bionic-updates/python3-software-properties")

Please post the output from running this command in Terminal -
```
sudo apt-get update
```

---

### Post by TheFu on 2018-09-11
I've never seen APT get THAT confused as to report dependencies incorrectly unless there is a hardware problem too.
Buying a new computer every time something like this happens will be costly.

Dependency problems are usually cause by 
a) manually installing a .deb package
b) using an untrusted PPA

I find it extremely suspect if the python or python libraries on the system are the latest. That doesn't happen with any LTS without manual action.  And that manual action would likely break dependencies.  For most scripting languages, it is considered a best practice to only use the versions provided by the normal Canonical repos for most things, unless you are a programmer in the language, then you'd setup something like pyenv to keep your version of python separate from the OS version.  There are lots of questions about scripting languages and best practices in these forums.  More specific techniques are provided in those threads.

---

### Post by Butthead on 2018-09-11
> **halogen2 said:**
> Err, no, they shouldn't -
[https://packages.ubuntu.com/bionic-updates/python3-apport]("https://packages.ubuntu.com/bionic-updates/python3-apport")
[https://packages.ubuntu.com/bionic-updates/python3-software-properties]("https://packages.ubuntu.com/bionic-updates/python3-software-properties")

Please post the output from running this command in Terminal -
```
sudo apt-get update
```

Okay, I can do that. 

```
sudo apt update
[sudo] password for peteyd: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]        
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                 
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [6,820 B]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [9,088 B]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [11.3 kB]   
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 128x128 Icons [31.6 kB] 
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [159 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [157 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [278 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 128x128 Icons [667 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,096 B]
Fetched 1,574 kB in 1s (1,865 kB/s)                                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

> **TheFu said:**
> I've never seen APT get THAT confused as to report dependencies incorrectly unless there is a hardware problem too.
Buying a new computer every time something like this happens will be costly.

Dependency problems are usually cause by 
a) manually installing a .deb package
b) using an untrusted PPA

I find it extremely suspect if the python or python libraries on the system are the latest. That doesn't happen with any LTS without manual action.  And that manual action would likely break dependencies.  For most scripting languages, it is considered a best practice to only use the versions provided by the normal Canonical repos for most things, unless you are a programmer in the language, then you'd setup something like pyenv to keep your version of python separate from the OS version.  There are lots of questions about scripting languages and best practices in these forums.  More specific techniques are provided in those threads.

Well, the computer I'm using now was built by zareason (so if there are any hardware conflicts somewhere it's their fault :P ).  I haven't had 18.04 that long yet (only about a month now), and I don't remember installing that many (if any?) external *.deb files on it since then.  The only thing I can think of is farting around with Muon trying to remove those two old 16.04 PPA's from it's repository list.  Come to think of it, that's probably where the problems started.  I never really read of anyone having the exact problem I have (the two held back files I have), but in my readings trying to get things fixed, it seems that everyone who futzed around with Muon usually had python3 issues later. :(

---

### Post by &amp;KyT$0P# on 2018-09-11
> **Butthead said:**
> Okay, I can do that. 
[s]That output looks good.  Could you please post the output from running this? -
```
sudo apt-get dist-upgrade
```[/s]

* Oops, I missed that you don't have a line about bionic-updates/main in the output.  Can you please post the full contents of your [FONT=Courier New]/etc/apt/sources.list[/FONT] file?

---

### Post by Butthead on 2018-09-12
Here's what I have in there:

(I (carefully?) removed all references to Xenial after the upgrade to Bionic, so I hope that I didn't mess things up there myself?) :eek:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports multiverse universe restricted main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://security.ubuntu.com/ubuntu/ bionic-security restricted main
deb http://security.ubuntu.com/ubuntu/ bionic-security universe
deb http://security.ubuntu.com/ubuntu/ bionic-security multiverse

```

Thanks for assisting me with this, halogen2, I really do appreciate it! :guitar:

Don't worry if it doesn't get fixed though, I bought a Bionic 18.04 LTS off of EBay that'll I'll reinstall with.  I kinda prefer doing it that way anyway as compared to the online upgrade. :lolflag:

---

### Post by TheFu on 2018-09-12
> **Butthead said:**
> Well, the computer I'm using now was built by zareason (so if there are any hardware conflicts somewhere it's their fault :P ).  

I wasn't suggesting any HW conflict.  I was suggesting some sort of hardware failure, like a loose SATA cable or dying HDD or bad SATA port or disk controller.  Sometimes, things just break, but not necessarily completely. They sorta work before they fail.

---

### Post by &amp;KyT$0P# on 2018-09-12
Try adding this line to your sources.list -
```
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
```

Then run
```
sudo apt-get update
```

Does it work now?

---

### Post by Butthead on 2018-09-13
> **TheFu said:**
> I wasn't suggesting any HW conflict.  I was suggesting some sort of hardware failure, like a loose SATA cable or dying HDD or bad SATA port or disk controller.  Sometimes, things just break, but not necessarily completely. They sorta work before they fail.

That could very possibly be.  This computer is getting quite long in the tooth.  Sorry if I sounded snotty there.  Trying to figure out how to fix these two held back packages is making me testy sometimes. ):P 

> **halogen2 said:**
> Try adding this line to your sources.list -
```
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
```

Then run
```
sudo apt-get update
```

Does it work now?

Thank you, thank you!!!!!!  I believe that fixed things.  I had to run "upgrade" too (which downloaded and installed about 5,000 packages), but I think apport-kde and software-properties-kde finally upgraded (or whatever they do? :confused: ).  Thank you so much for your help, halogen2.  You really have saved what little bit of sanity I still had left. :guitar::guitar::guitar:

---

### Post by &amp;KyT$0P# on 2018-09-13
You're welcome! :KS

---

### Post by Butthead on 2018-09-13
Thank you so much again! :guitar:

---

