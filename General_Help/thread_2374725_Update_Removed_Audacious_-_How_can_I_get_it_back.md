---
title: "Update Removed Audacious - How can I get it back?"
date: 2017-10-18
forum: General Help
---

### Post by Rick St. George on 2017-10-18
After update/ugrade/autoremove ... it removed Audacious a program I needed to stream a special news platform.
Synaptic now reports the following.

```

audacious:
 Depends: gtk2-engines-pixbuf but it is not going to be installed
  Depends: libaudcore3 (=3.6.2-2) but 3.7.2-2-1~webupd8~xenial1 is to be installed

```

How do I get Audacious back? Synaptic shows some parts are installed such as "libaudcore" and "audacious-plugins".

Thanks!

---

### Post by HermanAB on 2017-10-18
apt --reinstall install audacious

---

### Post by Rick St. George on 2017-10-18
Output:

```

sudo apt --reinstall install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package audacious is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  audacious-plugins

E: Package 'audacious' has no installation candidate

```

The "audacious-plugins" are already installed and showing in Synaptic Pkg Mgr. But it will do no good if Audacious can no longer be installed after recent updates!

Ran it again after selecting "universe" and "multiverse";

```

sudo apt --reinstall install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacious : Depends: audacious-plugins (>= 3.6.2) but it is not going to be installed
             Depends: libaudcore3 (= 3.6.2-2) but 3.7.2-2-1~webupd8~xenial1 is to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by vasa1 on 2017-10-18
Maybe start with the basics by posting the full output of *sudo apt-get update* and *sudo apt-get upgrade* as well as the output of```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by Rick St. George on 2017-10-18
> **vasa1 said:**
> Maybe start with the basics by posting the full output of *sudo apt-get update* and *sudo apt-get upgrade* as well as the output of```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

```

Reading package lists... Done
Building dependency tree        Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  audacious greybird-gtk-theme gtk2-engines-pixbuf openshot
  ubuntustudio-desktop ubuntustudio-desktop-core
The following NEW packages will be installed:
  linux-headers-4.4.0-97 linux-headers-4.4.0-97-lowlatency
  linux-image-4.4.0-97-lowlatency
The following packages will be upgraded:
  libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin linux-headers-lowlatency
  linux-image-lowlatency linux-lowlatency
7 upgraded, 3 newly installed, 6 to remove and 0 not upgraded.
Need to get 70.9 MB of archives.
After this operation, 238 MB of additional disk space will be used.
Do you want to continue? [Y/n]

```

After YES above, that is when it removed Audacious. Here is other output requested;

```

 grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*

/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
/etc/apt/sources.list:deb http://download.virtualbox.org/virtualbox/debian xenial contrib
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list.d/opera.list:deb http://deb.opera.com/opera-stable/ stable non-free
/etc/apt/sources.list.d/opera.list.save:deb http://deb.opera.com/opera-stable/ stable non-free
/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main

```

---

### Post by vasa1 on 2017-10-18
Did you run *sudo apt-get update* before you ran *sudo apt-get upgrade*?

And did you at some point remove a ppa? I ask because of```
             Depends: libaudcore3 (= 3.6.2-2) but 3.7.2-2-1~**webupd8**~xenial1 is to be installed
```in post #3.

Why is your system thinking that a package from **webupd8** is involved?

What does```
/etc/apt/sources.list.d
```show?

---

### Post by vasa1 on 2017-10-18
What does```
apt list --installed | grep -E "local\]$"
```show? If all is well, there should be no output.

---

### Post by Rick St. George on 2017-10-18
> **vasa1 said:**
> Did you run *sudo apt-get update* before you ran *sudo apt-get upgrade*?

And did you at some point remove a ppa? I ask because of```
             Depends: libaudcore3 (= 3.6.2-2) but 3.7.2-2-1~**webupd8**~xenial1 is to be installed
```Why is your system thinking that a package from **webupd8** is involved?

What does```
/etc/apt/sources.list.d
```show?

YES. And here is output;

```

ls /etc/apt/sources.list.d

bitdefender.list
bitdefender.list.distUpgrade
bitdefender.list.save
jfi-ppa-trusty.list
jfi-ppa-trusty.list.distUpgrade
jfi-ppa-trusty.list.save
jitsi.list
jitsi.list.save
kdenlive-ubuntu-kdenlive-stable-xenial.list
kdenlive-ubuntu-kdenlive-stable-xenial.list.save
linphone-release-trusty.list
linphone-release-trusty.list.save
muravjov-il-ubuntu-ppa-xenial.list
muravjov-il-ubuntu-ppa-xenial.list.save
nilarimogard-ubuntu-webupd8-xenial.list
nilarimogard-ubuntu-webupd8-xenial.list.save
openshot_developers-ubuntu-ppa-xenial.list
openshot_developers-ubuntu-ppa-xenial.list.save
opera.list
opera.list.save
opera-stable.list
opera-stable.list.distUpgrade
opera-stable.list.save
pipelight-stable-trusty.list
pipelight-stable-trusty.list.distUpgrade
pipelight-stable-trusty.list.save
pipelight-ubuntu-stable-xenial.list
pipelight-ubuntu-stable-xenial.list.save
skellat-ubuntu-flow1-xenial.list
skellat-ubuntu-flow1-xenial.list.save
sunab-kdenlive-release-trusty.list
sunab-kdenlive-release-trusty.list.distUpgrade
sunab-kdenlive-release-trusty.list.save
tails-team-ubuntu-tails-installer-xenial.list
tails-team-ubuntu-tails-installer-xenial.list.save
team-xbmc-ubuntu-ppa-xenial.list
team-xbmc-ubuntu-ppa-xenial.list.save
ubuntu-sdk-team-ppa-trusty.list
ubuntu-sdk-team-ppa-trusty.list.distUpgrade
ubuntu-sdk-team-ppa-trusty.list.save
ubuntu-sdk-team-ubuntu-ppa-xenial.list
ubuntu-sdk-team-ubuntu-ppa-xenial.list.save
venerix-pkg-trusty.list
venerix-pkg-trusty.list.save
virtualbox.list
virtualbox.list.distUpgrade
virtualbox.list.save
webupd8team-java-trusty.list
webupd8team-java-trusty.list.distUpgrade
webupd8team-java-trusty.list.save

```

Webupd8team is leftover, and from upgrade from trusty! Can I just delete those entries in that directory?

---

### Post by vasa1 on 2017-10-18
Could you deactivate _all_ your ppas and then try a vanilla *sudo apt-get update* and *sudo apt-get upgrade*?

And please post the output of```
apt list --installed | grep -E "local\]$"
```

---

### Post by Rick St. George on 2017-10-18
Tried to Reply to vasa1 request, but Vbulletin crashed twice. Output too long perhaps, and cut off at top - don't know why. But upgrade did show something about "xorg" updating. Does this help? 

Apparently it is getting updates for Audacious from the "webupd8" team.

---

### Post by mc4man on 2017-10-18
Post 
```
apt-cache policy audacious libaudcore* audacious-plugins
```

---

### Post by Rick St. George on 2017-10-18
> **mc4man said:**
> Post 
```
apt-cache policy audacious libaudcore* audacious-plugins
```

Ouput:

```

apt-cache policy audacious libaudcore* audacious-plugins

audacious:
  Installed: (none)
  Candidate: (none)
  Version table:
libaudcore1:
  Installed: 3.4.3-1
  Candidate: 3.4.3-1
  Version table:
 *** 3.4.3-1 100
        100 /var/lib/dpkg/status
libaudcore3:
  Installed: 3.7.2-2-1~webupd8~xenial1
  Candidate: 3.7.2-2-1~webupd8~xenial1
  Version table:
 *** 3.7.2-2-1~webupd8~xenial1 100
        100 /var/lib/dpkg/status
audacious-plugins:
  Installed: 3.7.2-2-1~webupd8~xenial1
  Candidate: 3.7.2-2-1~webupd8~xenial1
  Version table:
 *** 3.7.2-2-1~webupd8~xenial1 100
        100 /var/lib/dpkg/status

```

---

### Post by mc4man on 2017-10-18
The ppa's version is now audacious 3.9.3, libaudcore5,  but you don't show that.. Do you ever run ?
sudo apt update 

I'd do that & recheck
Otherwise purge out existing packages, i.e.
```
sudo apt purge libaudcore1 libaudcore3 audacious-plugins
```
Then ```
sudo apt update && sudo apt install audacious
```

---

### Post by again? on 2017-10-18
> **mc4man said:**
> The ppa's version is now audacious 3.9.3, libaudcore5,  but you don't show that.. Do you ever run ?
sudo apt update 

Probably used the webupd8 ppa at some stage but now disabled.
I have no problem with the ppa in Xenial and installing audacious.

I would suggest re-enable the webupd8 ppa, update and try to install audacious again.

---

### Post by ian-weisser on 2017-10-18
> **guber2 said:**
> I would suggest re-enable the webupd8 ppa, update and try to install audacious again.

The other gurus in this thread are advising the OP to do the opposite - to eliminate the webupd8 packages and downgrade the relevant packages back to stock Ubuntu.

EDIT: Your solution also solves the immediate problem. I point out the difference only to avoid confusion.

I think the revert-to-stock-Ubuntu advice is sound. The shockingly high number of non-Ubuntu sources on this system, and the package conflicts they inevitably drag in, have already broken apt functionality and will almost certainly prevent a successful release-upgrade...leading to an eventual (unnecessary) reinstall unless cleaned up.

---

### Post by again? on 2017-10-18
> **ian-weisser said:**
> The other gurus in this thread are advising the OP to do the opposite - to eliminate the webupd8 packages and downgrade the relevant packages back to stock Ubuntu.

Their advice is sound. The shockingly high number of non-Ubuntu sources on this system, and the package conflicts they inevitably drag in, have already broken apt functionality and will almost certainly prevent a successful release-upgrade...leading to an eventual (unnecessary) reinstall unless cleaned up.
...and I gave my experience with that ppa and another solution if the OP requires the version of audacious in the webupdate repository. :P

---

### Post by vasa1 on 2017-10-18
> **vasa1 said:**
> Could you deactivate _all_ your ppas and then try a vanilla *sudo apt-get update* and *sudo apt-get upgrade*?

And please post the output of```
apt list --installed | grep -E "local\]$"
```

> **Rick St. George said:**
> Tried to Reply to vasa1 request, but Vbulletin crashed twice. Output too long perhaps, and cut off at top - don't know why. ...I think the "output too long" maybe possibly be because of a very large number of hits. To confirm that, please run ```
apt list --installed | grep -Eic "local\]$"
```and```
apt list --installed | grep -Eic "\[installed"
```

In both cases, you'll just get the total number of matches and not long lists that could break your post. Ideally, the number produced by the first code should be much, much lower than that produced by the second code.

---

### Post by Rick St. George on 2017-10-18
Output shows only this;

```

$ apt list --installed | grep -Eic "local\]$"

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
1147

$ apt list --installed | grep -Eic "\[installed"

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
2925

```

---

### Post by Rick St. George on 2017-10-18
Followed Mc4man's advice in post 13, after allowing "universe" and "multiverse" to install audacious, here is the output;

```

Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
stephen@stephen-evo-5723:~$ sudo apt install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacious : Depends: audacious-plugins (>= 3.6.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Still stumped. Maybe I should just forget it. And Weiser's post 15 is disturbing. I only allow Canonical, proprietary drivers, and source code in Software & Updates / Settings. There are only a few programs I've allowed to be installed other than what comes allready installed. Such as Opera browser, Kodi, KdenLive and VirtualBox. Not sure what he means by "shockingly high number of non-Ubuntu sources", as I've printed out the List of Sources, and have removed / cleaned up sources.list.d folder. 

It now ONLY shows;

```

ls /etc/apt/sources.list.d

kdenlive-ubuntu-kdenlive-stable-xenial.list
kdenlive-ubuntu-kdenlive-stable-xenial.list.save
opera.list
opera.list.save
opera-stable.list
opera-stable.list.distUpgrade
opera-stable.list.save
team-xbmc-ubuntu-ppa-xenial.list
team-xbmc-ubuntu-ppa-xenial.list.save
ubuntu-sdk-team-ubuntu-ppa-xenial.list
ubuntu-sdk-team-ubuntu-ppa-xenial.list.save
virtualbox.list
virtualbox.list.distUpgrade
virtualbox.list.save

```

---

### Post by vasa1 on 2017-10-19
I'm sorry but your system is quite complicated by the fact that
you upgraded with several hangover ppas
you installed additional ppas
you removed ppas, possibly without removing the packages they installed.
you have 1147 "local" packages indicating that the system may not know how to deal with them.
Hence the conflicts.

In future, please be careful while installing ppas especially if they're pulling in packages that are of versions higher or lower than what your distro provides by default.

All the best!

---

### Post by mc4man on 2017-10-19
If you wish to solve this shouldn't be hard to do (tonight)
ck.
```
apt-cache policy libavcodec*
```

---

### Post by Rick St. George on 2017-10-19
> **mc4man said:**
> If you wish to solve this shouldn't be hard to do (tonight)
ck.
```
apt-cache policy libavcodec*
```

OUTPUT:

```

$ apt-cache policy libavcodec*

libavcodec-extra:
  Installed: 7:2.8.11-0ubuntu0.16.04.1
  Candidate: 7:2.8.11-0ubuntu0.16.04.1
  Version table:
 *** 7:2.8.11-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status
libavcodec54:
  Installed: (none)
  Candidate: (none)
  Version table:
libavcodec-extra-54:
  Installed: 6:9.18-0ubuntu0.14.04.1
  Candidate: 6:9.18-0ubuntu0.14.04.1
  Version table:
 *** 6:9.18-0ubuntu0.14.04.1 100
        100 /var/lib/dpkg/status
libavcodec-ffmpeg56:
  Installed: (none)
  Candidate: (none)
  Version table:
libavcodec-ffmpeg-extra56:
  Installed: 7:2.8.11-0ubuntu0.16.04.1
  Candidate: 7:2.8.11-0ubuntu0.16.04.1
  Version table:
 *** 7:2.8.11-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status

```


Looks like "libavcodec-extra-54" was installed for the previous version of UbuntuStudio v14.04. Don't know if this was left over from upgrading and Ubuntu failed to also update it, or if it is was failed to be updated by a PPA belonging to some "extra" program such as OpenShot or KdenLive as I've had problems getting any Video Editing program to keep from crashing during rendering. 

Does this help?
Thanks!

---

### Post by ian-weisser on 2017-10-19
> **Rick St. George said:**
> Looks like "libavcodec-extra-54" was installed for the previous version of UbuntuStudio v14.04. Don't know if this was left over from upgrading and Ubuntu failed to also update it

That particular package was orphaned after 14.04, and should be safe to uninstall.
Normally, such packages are automatically uninstalled during a release-upgrade...it's presence indicates that your upgrade to 16.04 may have been incomplete or otherwise broken. That's bad.

---

### Post by Rick St. George on 2017-10-19
According to Synaptic Pkg Mgr, Removing it will also remove the following;

libavdevice-extra-53
libavdevice53
libavfilter-extra-3
libavfilter3
libavformat-extra-54
libavformat54
libmediastreamer-base3
libwxsvg0

Under Properties it shows that it conflicts with "libavcodec54". I am assuming it will be safe to Uninstall all the above! True or False?
And is this what is Broken? preventing me from installing Audacious? 
Thanks!

---

### Post by vasa1 on 2017-10-19
You still haven't posted, IIRC, the output of```
sudo apt-get update
```

---

### Post by Rick St. George on 2017-10-19
> **vasa1 said:**
> You still haven't posted, IIRC, the output of```
sudo apt-get update
```

Not a Vanilla, so shows Repos ... Output;

```

Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]      
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:4 http://download.virtualbox.org/virtualbox/debian xenial InRelease        
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Get:6 http://deb.opera.com/opera-stable stable InRelease [2,592 B]             
Get:7 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [60.2 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.1 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:10 http://deb.opera.com/opera-stable stable/non-free amd64 Packages [1,827 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [213 kB]
Hit:12 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease
Hit:13 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease          
Fetched 849 kB in 6s (141 kB/s)                                                
Reading package lists... Done

```

I wonder how Mc4man suggest we fix this tonight? (see post 21 above)

---

### Post by vasa1 on 2017-10-19
In any case, now would be a nice time to back-up all your important data :)

---

### Post by Rick St. George on 2017-10-19
> **vasa1 said:**
> 
In future, please be careful while installing ppas especially if they're pulling in packages that are of versions higher or lower than what your distro provides by default.
 

Please for future reference ...

And how does one go about knowing what PPAs will be "pulling in"?? Do we not have to have some kind of faith in the programmers to know what they are doing since they obviously released their pkg for say "trusty" or "xenial" etc.?

---

### Post by vasa1 on 2017-10-19
Adding a ppa, per se, shouldn't cause a problem. The issue arises when you install software provided by the ppa. At that time, if you use the terminal, you should be told which packages or dependencies will be replaced.

I had an experience with Firejail: I installed the ppa and then when I ran the command to install firejail itself, I saw what existing software was going to be replaced. I backed away then.```
$ sudo apt-get install firejail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  firejail-profiles python-cairo python-gi python-gi-cairo
Recommended packages:
  xpra | xserver-xephyr | xvfb
The following packages will be REMOVED:
  **xorg xserver-xorg-hwe-16.04**
The following NEW packages will be installed:
  firejail firejail-profiles python-cairo python-gi python-gi-cairo
0 upgraded, 5 newly installed, **2 to remove** and 0 not upgraded.
Need to get 504 kB of archives.
After this operation, 1,936 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

BTW, if you're still intent on salvaging your existing system, I suggest you pipe the list of packges listed as"[installed,local]" to a file and upload that to pastebin so that people can know just how much unsupported software there is to deal with.

---

### Post by Rick St. George on 2017-10-19
> **vasa1 said:**
> 
BTW, if you're still intent on salvaging your existing system, I suggest you pipe the list of packges listed as"[installed,local]" to a file and upload that to pastebin so that people can know just how much unsupported software there is to deal with.

Thanks! Posted to;
[https://en.pastebin.ca/3891991](https://en.pastebin.ca/3891991)

---

### Post by mc4man on 2017-10-19
The ppa's you show installed seem not to be a factor here at first glance. Because apt isn't always verbose I'd install aptitude.
Then try,
```
sudo aptitude install audacious-plugins
```
What you are looking for is 
1. will audacious-plugins install
2. If not, why.
So if it doesn't  install aptitude will present you with some options. You can answer No (n) then it'll give you you another one. Answer  no then quit (q). Copy and post complete output.

---

### Post by Rick St. George on 2017-10-19
Thanks Mc4Man, but I have it installed now and working. It seems removing "libavcodec-extra-54" (see post 22, pg 3) did the trick. Did you see my post 30 (bottom of pg 3)? 

I have gone through Synaptic Pkg Mgr, looked at Manual install, selected a lot that were not supported and didn't seem likely needed, and Removed them. Also deleted all thumbnails, Removed old/unused Deb pkgs., Ran autoclean, autoremove, update, upgrade, dist-upgrade. Rebooted and all seems fine. Not sure how else to "clean up" system.

Unless you have any other input, I will consider this case closed / solved.  Thanks a Million to all ! ! !

---

### Post by mc4man on 2017-10-19
> **Rick St. George said:**
> Thanks Mc4Man, but I have it installed now and working. It seems removing "libavcodec-extra-54" (see post 22, pg 3) did the trick. Did you see my post 30 (bottom of pg 3)? 

I have gone through Synaptic Pkg Mgr, looked at Manual install, selected a lot that were not supported and didn't seem likely needed, and Removed them. Also deleted all thumbnails, Removed old/unused Deb pkgs., Ran autoclean, autoremove, update, upgrade, dist-upgrade. Rebooted and all seems fine. Not sure how else to "clean up" system.

Unless you have any other input, I will consider this case closed / solved.  Thanks a Million to all ! ! !
No, I must have missed it. It did seem that the plugin package & ffmpeg libs were at the root of your problem.
As far as the use of ppa's, they can provide great advantage, those that take a sky is falling position are just plain misinformed.
I'd assume you're back on the 16.04 version, if ever inclined to use the newer audacious let me know & I'll set you up...

---

### Post by vasa1 on 2017-10-20
Just to be clear, I absolutely do use ppas. I have the following on one system or the other:```
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial main
/etc/apt/sources.list.d/kubuntu-ppa-ubuntu-backports-xenial.list:deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ xenial main   
/etc/apt/sources.list.d/libreoffice-ubuntu-libreoffice-5-2-xenial.list:deb http://ppa.launchpad.net/libreoffice/libreoffice-5-2/ubuntu/ xenial main 
/etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-xenial.list:deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu/ xenial main 
/etc/apt/sources.list.d/mc3man-ubuntu-mpv-tests-xenial.list:deb http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu/ xenial main 
/etc/apt/sources.list.d/mkusb-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/mkusb/ppa/ubuntu/ xenial main 
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main   

```But I also keep ppa-purge just in case!

---

### Post by mc4man on 2017-10-20
In general when upgrading an install to next release the  best practice is to 1st use ppa-purge on existing ppa's before starting the upgrade process. For some ppa's it's absolutely required & the ppa page usually states that.

Also to note that when removing a ppa from the sources one should consider using ppa-purge before doing so. ( Not required but some thought should be given... 
Synaptic package manager  is well advised for ppa users as it's Origin tab will show  all installed from that ppa,  what is available & what is an upgrade

---

### Post by Rick St. George on 2017-10-20
> **mc4man said:**
>  ... if ever inclined to use the newer audacious let me know & I'll set you up...

I was interested until I took VASA's advice and watched what may be "replaced" during an upgrade. Webup8team was replacing 3 or 4 files and I didn't want to chance another corruption. But I'll look at any advice you have for me.

Thanks!

](*,)

---

### Post by vasa1 on 2017-10-20
> **Rick St. George said:**
> I was interested until I took VASA's advice and watched what may be "replaced" during an upgrade. Webup8team was replacing 3 or 4 files and I didn't want to chance another corruption. But I'll look at any advice you have for me.

Thanks!

](*,)
mc4man is totally qualified to guide you about audacious provided you follow his instructions! He's got audacious here:  [https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media](https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media)

---

