---
title: "Is anyone else seeing these dpkg errors?"
date: 2007-05-18
forum: General Help
---

### Post by navneeth on 2007-05-18
Lately, I have not been able to install some programs, either via apt or with the source file (because I needed to get some dependencies via apt) because the installation process comes to a halt at a "dpkg error." I can not tell you what happened in the previous instances, but today, while trying to install Abode Reader via Automatix, the installation stopped because Acroread could not be installed. So, I did a apt-get -f install, and here's what followed. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  acroread
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/22.9MB of archives.
After unpacking 56.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 103911 files and directories currently installed.)
Unpacking acroread (from .../acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I had similar errors while installing a few other softwares, but it did not happen always. Also here's the output of dpkg --configure -a

```
dpkg: dependency problems prevent configuration of acroread-plugins:
 acroread-plugins depends on acroread (= 7.0.9-0.0.ubuntu0.7.04+medibuntu1); however:
  Package acroread is not installed.
dpkg: error processing acroread-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozilla-acroread:
 mozilla-acroread depends on acroread (>= 7.0); however:
  Package acroread is not installed.
dpkg: error processing mozilla-acroread (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acroread-plugins
 mozilla-acroread

```


Someone please help!!!:(

---

### Post by carlosqueso on 2007-05-18
try running ```
sudo apt-get install -f
``` to fix the broken packages.  It SHOULD install the acroread package, which SHOULD stop those errors.  If that doesn't work, post the results of ```
cat /etc/apt/sources.list
```

---

### Post by navneeth on 2007-05-18
> **carlosqueso said:**
> try running ```
sudo apt-get install -f
``` to fix the broken packages.  It SHOULD install the acroread package, which SHOULD stop those errors. 
I did just that. The result of that is posted in my first post. 

> If that doesn't work, post the results of ```
cat /etc/apt/sources.list
```

```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://kubuntu.org/packages/amarok-145 edgy main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://kent.dl.sourceforge.net/sourceforge/ skychart/

```

Apart from the usual Ubuntu repos(including universe multiverse), all I have are Amarok, Automatix and an astronomy program called Carted du Ciel(Sky Chart)

---

### Post by carlosqueso on 2007-05-18
Try adding the medibuntu repos with the following line to your sources.list ```
deb http://medibuntu.sos-sts.com/repo feisty free nonfree
``` and comment out the automatix repos. Then import the medibuntu key with ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
``` and try running sudo apt-get update and sudo apt-get install -f again.

---

### Post by navneeth on 2007-05-18
Hmm...all it seemed to have done was remove the plugins!

At the end of updating the repos, I got
```
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/Release  Unable to find expected entry  nonfree/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

And at the end of apt-get install -f AFTER the update

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  acroread-plugins mozilla-acroread
0 upgraded, 0 newly installed, 2 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 57.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 103910 files and directories currently installed.)
Removing acroread-plugins ...
Removing mozilla-acroread ...

```

---

### Post by carlosqueso on 2007-05-18
strange....I don' t get that error....did you try updating the repos a second time? and did it give you the erroer after you used apt-get install -f?

---

### Post by navneeth on 2007-05-18
The error after the update still appears. When I did a install -f earlier (after uninstalling the plugins) I had only 6 upgrades (nothing related to this), and those have been installed. 

Btw, just to reiterate what I said in the first post, this is something that I have seen at other instancees, too. I think I got the same dpkg error (post #1) while trying to install clisp. 

I really appreciate you for helping me solve this problem. :)

---

### Post by carlosqueso on 2007-05-18
Strange.....the first thing that I would do is comment out the repo I gave you as you seem to be having trouble with it....are you still showing partly installed packages....if you are we could try to use dselect to get rid of them....

---

### Post by Cappy on 2007-05-18
Maybe ```
sudo apt-get clean
``` and then trying to reinstall those packages. It says the packages are corrupt so maybe it needs to redownload them.

---

### Post by navneeth on 2007-05-18
> **Cappy said:**
> Maybe ```
sudo apt-get clean
``` and then trying to reinstall those packages. It says the packages are corrupt so maybe it needs to redownload them.

I can't say for sure, but that may have done the trick! 

carlosqueso,
             I commented out the repo you provided and installed 'acroread' directly from the terminal. It used one of the Automatix repos, but it did not download the plugins, just the reader. Now I have a pdf open in Adobe Reader. 

Cappy,
 I also tried what you suggested before installing acroread. I was also able to install clisp without any problem and install a program, which I had not been able to do in the past few days, because it depended on clisp.

Thank you very much for the timely help, carlosqueso and Cappy. :)

---

### Post by navneeth on 2007-05-18
Now, how do I mark this thread as resolved?

EDIT: Never mind. Marked.

---

### Post by tallgurl1337 on 2007-12-05
I'm seeing these errors, and I attempted to enter "sudo apt-get install -f" and I keep getting the same prompt.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

Except when I run 'dpkg --configure -a,' I get a lovely 

```
dpkg: requested operation requires superuser privilege
```


I'm sure it's something obvious that I'm missing. I'm new to ubuntu, so I would appreciate any input. :oops:

---

### Post by panda726 on 2007-12-05
I would expect that since you are running the original command with root privileges (by using sudo), the error assumes that you are working from root (not true.  You are working from a user account, given root privileges for the command only.)  Add sudo to the beginning of the command it told you to use, and see if that works.

```
sudo dpkg --configure -a
```

Hope this works,

Tor

---

### Post by soulful1 on 2007-12-06
I had the same problem when I was installing Java. Now that I've installed I'm stuck on the blue "Configuring sun-java6-bin" screen. What do I do after this? It seems like I'm stuck on this screen in the terminal

---

### Post by soulful1 on 2007-12-06
*bump*:)

---

### Post by panda726 on 2007-12-06
Can't help you there.  You might try a new thread, as this one was marked solved (may have been unmarked, although I don't know).  I happened to be interested in the thread and checked it for that reason.

Tor

---

### Post by rsambuca on 2007-12-06
> **soulful1 said:**
> I had the same problem when I was installing Java. Now that I've installed I'm stuck on the blue "Configuring sun-java6-bin" screen. What do I do after this? It seems like I'm stuck on this screen in the terminal

You have to use the tab or arrow keys to get to the bottom, and then toggle to the OK button and press enter if you agree to the terms.

---

