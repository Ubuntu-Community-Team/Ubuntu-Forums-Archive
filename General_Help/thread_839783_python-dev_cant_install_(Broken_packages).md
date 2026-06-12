---
title: "python-dev cant install (Broken packages)"
date: 2008-06-24
forum: General Help
---

### Post by genfly on 2008-06-24
UPDATE:  FIXED! it installed without errors with: smart package manager 0.52

[B]Hello,

i have a slight problem

trying to install python-dev but its not working...[/B]

genfly@genfly-laptop:~$ sudo apt-get install python-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  python-dev: Depends: python2.5-dev (>= 2.5.2) but it is not going to be installed
E: Broken packages

----
**here is my /etc/apt/sources.list**

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)


[B]I have no idea what to do. I downloaded the package manually (python_2.5.2-0ubuntu1_all.deb)  and it says its already installed.. reinstalled... however when i want to install my file (nautilus-play-amarok_0.1.1-1_all.deb) it says python-dev is not installed. Also when i check Synaptic Package manager it says its not installed...

Any help would be greatly appreciated.

Thanks in advance![/B]

---

### Post by spiderbatdad on 2008-06-24
I would open synaptic package manager. Fix any broken packages via the Edit menu. Make sure you have python, python2.5 installed then try installing python-dev through synaptic. It should also install python2.5-dev

---

### Post by genfly on 2008-06-24
thanks for the speedy reply.

Python, Python2.5, Python2.5-dbg are installed

Edit -> Fix Broken Packages   

does nothing :(

when i try and install Python2.5-dev it keeps saying

python2.5-dev:
  Depends: python2.5 (=2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 is to be installed

---

### Post by spiderbatdad on 2008-06-24
Hmm. I'm just not sure. It installed for me with no errors. You might try running: ```
sudo apt-get install -f
```See if that fixes any broken packages. The only other thing I'm wondering about is the fact that you have backports commented out in your sources  list.

---

### Post by genfly on 2008-06-24
no luck

genfly@genfly-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


restored my backports from an old sources.list_backup.. just to see if that did anything (since i dont have anything in backports). The dapper ones are just for some program i installed. removed them afterwards.

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe


no luck

---

### Post by spiderbatdad on 2008-06-24
> **genfly said:**
> no luck

genfly@genfly-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


restored my backports..
## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe


no luck

This is confusing:
 # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

From your original post, yet above shows "dapper-backports." Do you have more than one sources.list? Was this a clean hardy install or an upgrade from dapper?

---

### Post by genfly on 2008-06-24
downloaded python2.5 2.5.2-2ubuntu4 manually (python2.5_2.5.2.orig.tar.gz) and installed.

no luck python2.5-dev doesnt install..

next installed python2.5 2.5.2-2ubuntu5 manually

no luck python2.5-dev doesnt install..

---

### Post by genfly on 2008-06-24
those dapper backports are just something i used to have in my sources.list. I found it in sources.list_backup so i tried using that but no luck. Was a clean install. must have added the dapper-backports at some time to install some program or something and removed it afterwards. anyway i don't think thats the problem. sorry for being confusing



RE: This is confusing:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

From your original post, yet above shows "dapper-backports." Do you have more than one sources.list? Was this a clean hardy install or an upgrade from dapper?

---

### Post by genfly on 2008-06-24
FIXED!

it installed!

i used 

sudo smart --gui

(smart package manager 0.52)

found python-dev and installed it... no errors like in Synaptic package manager and apt-get install

i read somewhere that smart is a superior package manager so i tried it and well it fixed this problem anyway :)

Thanks to all that helped!!

---

### Post by spiderbatdad on 2008-06-24
I believe you may be missing a symlink in /usr/lib. I have had trouble with other dependencies in hardy due to broken links. Try creating the symlink manually. then seen if you can install python-dev

```
sudo ln -s /usr/lib/libpython2.5.so.1 /usr/lib/libpython2.5.so
```


Edit: Ah great!. Glad you found a solution.

---

### Post by rebeldevel on 2008-06-29
We need an "official" solution since smart is not default package manager. I installed Ubuntu last night and I am having issues to install python-dev.

python-dev:
 Depends: python2.5-dev but it is not going to be installed

python2.5-dev:
  Depends: python2.5 (=2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 is to be installed

python2.5 package had an update from 2.5.2-2ubuntu4 to 2.5.2-2ubuntu5, but other packages that depend on it didn't get updated as well.

The solution provided by spiderbatdad didn't worked.

I tried with different repositories, the issue persists. I will fill a bug report.

:mad: :mad: :mad:

---

### Post by rebeldevel on 2008-06-29
Bug report # 244110:

[https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/244110](https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/244110)

Please add comments if you are having the same issue.

---

### Post by makajawanjack on 2008-07-05
I've got the same problem. It seems like Ubuntu upgraded the python2.5 package to Ubuntu5 without changing the dependencies for python2.5-dev and that broke it, since it depends on version ubuntu4. Is there any way around this?

---

### Post by Zeike on 2008-07-13
As a temporary fix you can download the package file manually from packages.ubuntu.com, then run 

sudo dpkg -i --force-depends python2.5-dev*.deb

---

