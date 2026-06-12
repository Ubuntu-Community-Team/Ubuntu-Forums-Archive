---
title: "Youtube video screen disappears"
date: 2017-10-15
forum: General Help
---

### Post by satimis on 2017-10-15
Hi all,

Could you please explain how it would happen?

After installing the package "cpu-checker" playing youtube video on Firefox there is no video screen displayed, only sound.  There is no problem on Google Chrome.

After un-installing "cpu-checker" the video screen comes back again?

Why?

Thanks

Regards
satimis

---

### Post by Autodave on 2017-10-15
That is interesting. I do know that a not-too-long-ago release of Firefox caused various issues with sound mostly and some video. You should be runni9ng version 56.0 (or higher if it exists). If not, run in a terminal:

sudo apt-get update
sudo apt-get upgrade

That should give you the current one.

---

### Post by satimis on 2017-10-15
> **Autodave said:**
> That is interesting. I do know that a not-too-long-ago release of Firefox caused various issues with sound mostly and some video. You should be runni9ng version 56.0 (or higher if it exists). If not, run in a terminal:

sudo apt-get update
sudo apt-get upgrade

That should give you the current one.

Just ran
$ sudo apt update ; sudo apt upgrade```

..........
.........
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Firefox
51.0.1 (64-bit)

---

### Post by vasa1 on 2017-10-15
@satimis,

Please post the output of ```
apt policy firefox
```

---

### Post by Frogs Hair on 2017-10-15
Were there any packages removed in the process of installing cpu-checker ? This could happen if there is a conflict.

---

### Post by ajgreeny on 2017-10-15
Really Firefox 51.0.1?
What version of Ubuntu are you using?

---

### Post by satimis on 2017-10-15
> **vasa1 said:**
> @satimis,

Please post the output of ```
apt policy firefox
```

&#10219; apt policy firefox```

firefox:
  Installed: 51.0.1+build2-0ubuntu0.16.04.1
  Candidate: 51.0.1+build2-0ubuntu0.16.04.1
  Version table:
 *** 51.0.1+build2-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status
     44.0.2+build1-0ubuntu1 500
        500 http://ubuntu.01link.hk xenial/main amd64 Packages

```

satimis

---

### Post by satimis on 2017-10-15
> **Frogs Hair said:**
> Were there any packages removed in the process of installing cpu-checker ? This could happen if there is a conflict.

There was no specific warning during installing cpu-checker

Regards

---

### Post by satimis on 2017-10-15
> **ajgreeny said:**
> Really Firefox 51.0.1?

Yes.

I found it on
-> Help -> About Firefox

please refers to attached screenshot

> 
What version of Ubuntu are you using?

&#10219; lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

```

Edit
===
&#10219; firefox -v```

Mozilla Firefox 51.0.1

```


satimis

---

### Post by ajgreeny on 2017-10-16
Have you run ```
sudo apt-get autoremove
``` to also remove any dependencies of cpu-checker, and did you remove or purge the package?

If you use synaptic package manager search using that for firefox, as something is definitely wrong if FF-51 is the version available to you.

Let's also see the output of ```
cat /etc/apt/sources.list
``` to check the repos being searched.

---

### Post by satimis on 2017-10-16
> **ajgreeny said:**
> Have you run ```
sudo apt-get autoremove
``` to also remove any dependencies of cpu-checker, and did you remove or purge the package?

IIRC I only ran;```

sudo apt-get purge cpu-checker

``` 


> 
If you use synaptic package manager search using that for firefox, as something is definitely wrong if FF-51 is the version available to you.

Let's also see the output of ```
cat /etc/apt/sources.list
``` to check the repos being searched.

&#10219; cat /etc/apt/sources.list```

# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

deb http://ubuntu.01link.hk/ xenial main restricted
deb-src http://ubuntu.01link.hk/ xenial main restricted

deb http://ubuntu.01link.hk/ xenial-updates main restricted
deb-src http://ubuntu.01link.hk/ xenial-updates main restricted

deb http://ubuntu.01link.hk/ xenial universe
deb-src http://ubuntu.01link.hk/ xenial universe
deb http://ubuntu.01link.hk/ xenial-updates universe
deb-src http://ubuntu.01link.hk/ xenial-updates universe

deb http://ubuntu.01link.hk/ xenial multiverse
deb-src http://ubuntu.01link.hk/ xenial multiverse
deb http://ubuntu.01link.hk/ xenial-updates multiverse
deb-src http://ubuntu.01link.hk/ xenial-updates multiverse

deb http://ubuntu.01link.hk/ xenial-backports main restricted universe multiverse
deb-src http://ubuntu.01link.hk/ xenial-backports main restricted universe multiverse

deb http://ubuntu.01link.hk/ xenial-security main restricted
deb-src http://ubuntu.01link.hk/ xenial-security main restricted
deb http://ubuntu.01link.hk/ xenial-security universe
deb-src http://ubuntu.01link.hk/ xenial-security universe
deb http://ubuntu.01link.hk/ xenial-security multiverse
deb-src http://ubuntu.01link.hk/ xenial-security multiverse

```

Regards

---

### Post by ajgreeny on 2017-10-16
Stranger and stranger!

What does ```
apt search firefox
``` show you as output?

---

### Post by satimis on 2017-10-17
> **ajgreeny said:**
> Stranger and stranger!

What does ```
apt search firefox
``` show you as output?

On Terminal performed:
&#10219; apt search firefox >> firefox_output.txt

firefox_output.txt attached to this posting

Regards
satimis

---

### Post by vasa1 on 2017-10-17
I don't like the **[installed,local]** in```
firefox/now 51.0.1+build2-0ubuntu0.16.04.1 amd64 [installed,local]
  Safe and easy web browser from Mozilla
```

For comparison, please show the output from```
apt list --installed | grep -E "(google|firefox)"
```

---

### Post by satimis on 2017-10-17
> **vasa1 said:**
> I don't like the **[installed,local]** in```
firefox/now 51.0.1+build2-0ubuntu0.16.04.1 amd64 [installed,local]
  Safe and easy web browser from Mozilla
```

For comparison, please show the output from```
apt list --installed | grep -E "(google|firefox)"
```

&#10219; apt list --installed | grep -E "(google|firefox)"```


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

account-plugin-google/now 0.12+16.04.20160126-0ubuntu1 all [installed,local]
firefox/now 51.0.1+build2-0ubuntu0.16.04.1 amd64 [installed,local]
firefox-locale-en/now 51.0.1+build2-0ubuntu0.16.04.1 amd64 [installed,local]
google-chrome-stable/now 48.0.2564.82-1 amd64 [installed,local]
libaccount-plugin-google/now 0.12+16.04.20160126-0ubuntu1 amd64 [installed,local]
unity-scope-firefoxbookmarks/xenial,xenial,now 0.1+13.10.20130809.1-0ubuntu1 all [installed,automatic]

```

satimis

---

### Post by vasa1 on 2017-10-17
Even your google-chrome is way outdated! The current version is 61.0.3163.100 (Official Build) (64-bit).

I don't understand why you're seeing **[installed,local]** even for google-chrome. I see```
google-chrome-stable/stable,now 61.0.3163.100-1 amd64 [installed]
```and I don't have a single **[installed,local]** on my 16.04.

Can you try changing servers from "hk" or whatever it is you're using to the main server?

And please post the output from```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

I'm trying to find out why some packages are marked **[installed,local]** but I can't find a simple reason. Some point 
to a distro version upgrade, in your case 14.04 > 16.04, gone wrong 
or to an attempted downgrade of distro version
or to repositories not being found ... Synaptic Package Manager is said to show these as "local or obsolete".

As usual, I feel it will be best to back up your data and do a clean install of 16.04 :)

---

### Post by satimis on 2017-10-17
> **vasa1 said:**
>  - snip -

As usual, I feel it will be best to back up your data and do a clean install of 16.04 :)

This box has been running >5 years.  IIRC Ubuntu 16.04 desktop was upgraded from its previous version 14.04

Now I have a new 250G SSD and a new 2TB WD spinning HD ready for installing Ubuntu 16.04 desktop and KVM.  Please see another posting;

Android as guest on KVM
[https://ubuntuforums.org/showthread.php?t=2374318&p=13697879#post13697879](https://ubuntuforums.org/showthread.php?t=2374318&p=13697879#post13697879)

After finish I'll move all data on the current 1TB SSD including VMs to the new 2TB WD spinning HD.  Then I'll do a clean installation of Ubuntu 16.04 desktop including VirtualBox on the 1TB SSD.  Afterwards I'll move all VMs back to it.  All data including daily running data will be stored on the 2TB WD spinning HD.  The 1TB SSD will be only used for running Ubuntu 16.04 desktops and VirtualBox including VMs

Regards
satimis

---

### Post by ajgreeny on 2017-10-17
It might be worth purging both firefox and possibly google-chrome, then run sudo apt clean to clear the repository package cache, and finally install both browsers again, firefox from the main repos, as mentioned above by vasa1, and chrome in whatever is the usual manner (I don't use google-chrome so have no personal experience of how it's installed).

---

### Post by vasa1 on 2017-10-17
> **ajgreeny said:**
> ... (I don't use google-chrome so have no personal experience of how it's installed).
I get it by following the instructions in [https://www.google.com/chrome/browser/desktop/index.html](https://www.google.com/chrome/browser/desktop/index.html) and then install the deb using gdebi. The process automatically adds the ppa to ensure future updates.

---

### Post by deadflowr on 2017-10-17
> I don't understand why you're seeing [installed,local] even for google-chrome. I see

I believe installed,local means initial install.
Once you get an update, it should be just listed as installed.
So I think it means the system is not properly updating.
Firefox 51.0.1+build2-0ubuntu0.16.04.2 is the version that came with 16.04.2's iso.

---

### Post by satimis on 2017-10-17
> **ajgreeny said:**
> It might be worth purging both firefox and possibly google-chrome, then run sudo apt clean to clear the repository package cache, and finally install both browsers again, firefox from the main repos, as mentioned above by vasa1, and chrome in whatever is the usual manner (I don't use google-chrome so have no personal experience of how it's installed).
Hi,

If I understand your advice correctly, perform following steps;

1)```

$ sudo apt-get purge firefox

```

2)```

$ sudo apt-get purge chrome

```

3)```

$ sudo apt-get clean

```

4)```

$ sudo apt-get install firefox

```

5)
As advised by vasa1 in the posting below;
Download chrome on;
[https://www.google.com/chrome/browser/desktop/index.html](https://www.google.com/chrome/browser/desktop/index.html)

6)
Install chrome running;```

$ sudo dpkg -i chrome_deb_package.

```

If I'm wrong please correct me.  Thanks

Regards
satimis

---

### Post by satimis on 2017-10-17
> **deadflowr said:**
> I believe installed,local means initial install.
Once you get an update, it should be just listed as installed.
So I think it means the system is not properly updating.
Firefox 51.0.1+build2-0ubuntu0.16.04.2 is the version that came with 16.04.2's iso.
Performed update and upgrade

&#10219; sudo apt update ; sudo apt upgrade```

Hit:1 http://ubuntu.01link.hk xenial InRelease
Hit:2 http://ubuntu.01link.hk xenial-updates InRelease
Hit:3 http://ubuntu.01link.hk xenial-backports InRelease
Hit:4 http://ubuntu.01link.hk xenial-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Ubuntu 16.04 is up-to-date

satimis

---

### Post by deadflowr on 2017-10-17
> If I'm wrong please correct me. Thanks

Typically chrome might require dependencies not installed.
(since you had chrome previously, that's not much of a problem)
But you can install chrome, and it's dependencies with
```
sudo apt install ~/Downloads/google-chrome_some-version-name/nuber.deb
```
Otherwise to install with dpkg you need to run
```
cd Downloads
sudo dpkg -i google-chrome-some-version-name/number.deb
sudo apt-get install -f
```
You run the install -f command because dpkg does not handle dependencies so the system would otherwise consider the installation broken.
Which the install -f command goes ahead and fixes.

Again, though, since you have previously installed chrome, the need to install it's needed dependencies should be moot.


Edit:

> Ubuntu 16.04 is up-to-date

We know that's not true.

Looking at the mirror:
[https://launchpad.net/ubuntu/+mirror/ubuntu.01link.hk-archive]("https://launchpad.net/ubuntu/+mirror/ubuntu.01link.hk-archive")
it shows it has not been verified for over a year now.
Might be that it's frozen.

My suggestion would be to try another mirror.

Easiest method is to open Software and Updates
Go down to download Form: toggle the dropdown bar and select Other.
Then go to the top right of the new window and hit Select Best Server and let it run; it'll find the fastest server to your machine based on current speeds.
Then hit Choose server.
Close software and updates; it should automatically run a reload, that's an apt-get update.

if all works as expected you might get a Software Updates are available message.
That would mean the updater works properly now.
Install the updates and profit.

Godd Luck

---

### Post by satimis on 2017-10-17
> **deadflowr said:**
>  - snip -

My suggestion would be to try another mirror.

Easiest method is to open Software and Updates
Go down to download Form: toggle the dropdown bar and select Other.
Then go to the top right of the new window and hit Select Best Server and let it run; it'll find the fastest server to your machine based on current speeds.
Then hit Choose server.
Close software and updates; it should automatically run a reload, that's an apt-get update.

if all works as expected you might get a Software Updates are available message.
That would mean the updater works properly now.
Install the updates and profit.

Godd Luck

Start "Software and Updates"
-> Choose a Download Server
there are only 3 mirrors under "Hong Kong"
(please see attached screenshot)

Is there anyway to check which of the other two is reliable?

satimis

---

### Post by deadflowr on 2017-10-17
the ftp.cuhk.edu.hk mirror is an Official mirror, so it should be up-to-date.
I would try that one.

---

### Post by vasa1 on 2017-10-18
> **deadflowr said:**
> I believe installed,local means initial install.
Once you get an update, it should be just listed as installed.
So I think it means the system is not properly updating.
Firefox 51.0.1+build2-0ubuntu0.16.04.2 is the version that came with 16.04.2's iso.@deadflowr, please see [https://github.com/Debian/apt/blob/1d9e29c9e2a5591b42a99a721b901fc003ed9149/apt-private/private-output.cc#L273](https://github.com/Debian/apt/blob/1d9e29c9e2a5591b42a99a721b901fc003ed9149/apt-private/private-output.cc#L273) which explains matters in a very technical way!

---

### Post by satimis on 2017-10-19
> **deadflowr said:**
> the ftp.cuhk.edu.hk mirror is an Official mirror, so it should be up-to-date.
I would try that one.
Hi,

Thanks for your advice.


Performed following steps:

On Terminal
$ cd /etc/apt
$ sudo cp sources.list sources.list_old_20171019

Start Software & Updates
-> Download from: Server for Hong Kong

Remark:```

Just finished installing Ubuntu 16.04 desktop on a new 250G SanDisk SSD
Download from: Server for Hong Kong

```

login "To change sofware repository settings, you need to authenticate"
-> Authenticate

-> Close

```

The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.

```

On Terminal run;
&#10219; sudo apt update ; sudo apt upgrade```

....
....
Setting up update-notifier (3.168.5) ...
Setting up update-manager (1:16.04.9) ...
Setting up flashplugin-installer (27.0.0.170ubuntu0.16.04.1) ...
Setting up libpurple0 (1:2.10.12-0ubuntu5.2) ...
Setting up libpurple-bin (1:2.10.12-0ubuntu5.2) ...
Setting up liboxideqtcore0:amd64 (1.21.5-0ubuntu0.16.04.1) ...
Setting up liboxideqtquick0:amd64 (1.21.5-0ubuntu0.16.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.21.5-0ubuntu0.16.04.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-97-generic
Processing triggers for systemd (229-4ubuntu19) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ca-certificates (20170717~16.04.1) ...
Updating certificates in /etc/ssl/certs...
WARNING: Skipping duplicate certificate UbuntuOne-Go_Daddy_Class_2_CA.pem
WARNING: Skipping duplicate certificate UbuntuOne-Go_Daddy_Class_2_CA.pem
17 added, 42 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
Processing triggers for resolvconf (1.78ubuntu4) ...

```

&#10219; systemctl reboot

After booting:-
&#10219; lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

```

&#10219; firefox -v```

Mozilla Firefox 56.0

```

&#10219; google-chrome --version```

Google Chrome 48.0.2564.82 

```

Is it the latest version for Ubuntu 16.04 ?

&#10219; ls /etc/apt/```

apt.conf.d     sources.list.d             sources.list.save  trusted.gpg~
preferences.d  sources.list.distUpgrade   trustdb.gpg        trusted.gpg.d
sources.list   sources.list_old_20171019  trusted.gpg

```

&#10219; cat /etc/apt/sources.list >> sources_list_20171019.txt

sources_list_20171019.txt attached.

Any further step is needed?  Thanks


Edit
====
$ sudo apt update ; sudo apt dist-upgrade
$ sudo apt autoremove


Regards
satimis

---

### Post by vasa1 on 2017-10-19
I've already told you that your Google Chrome is very, very old. It's now v62. Google Chrome isn't present by default in any Ubuntu flavor.

And what about the output from **uname -a**?

---

### Post by deadflowr on 2017-10-19
Well chrome is old and not the latest version.
What does the chrome ppa/repo entry say?
(It should be listed in the /etc/apt/sources.list.d directory as something like google-chrome.list)
The proper entry should be something like
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
You might check if the entry is either disabled (with a # at the beginning) or if the whole file is disabled (the name would end with a .save, typically)
You can run
```
ls /etc/apt/sources.list.d/
```
to see all the files in the directory.

If either the entry or the filename is marked as disabled, simply try removing the # or .save , then try running another update.

If that makes sense.

---

### Post by satimis on 2017-10-19
> **vasa1 said:**
> I've already told you that your Google Chrome is very, very old. It's now v62. Google Chrome isn't present by default in any Ubuntu flavor.

OK I'll reinstall google-chrome later.

> 
And what about the output from **uname -a**?
&#10219; uname -a```

Linux ub1604ssd1tb 4.4.0-97-generic #120-Ubuntu SMP Tue Sep 19 17:28:18 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

satimis

---

### Post by satimis on 2017-10-19
> **deadflowr said:**
> Well chrome is old and not the latest version.
What does the chrome ppa/repo entry say?
(It should be listed in the /etc/apt/sources.list.d directory as something like google-chrome.list)
The proper entry should be something like
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
You might check if the entry is either disabled (with a # at the beginning) or if the whole file is disabled (the name would end with a .save, typically)
You can run
```
ls /etc/apt/sources.list.d/
```
to see all the files in the directory.

If either the entry or the filename is marked as disabled, simply try removing the # or .save , then try running another update.

If that makes sense.
&#10219; ls /etc/apt/sources.list.d```

google-chrome.list              peterlevi-ppa-trusty.list
google-chrome.list.distUpgrade  peterlevi-ppa-trusty.list.distUpgrade
google-chrome.list.save         peterlevi-ppa-trusty.list.save

```

&#10219; cat /etc/apt/sources.list.d/google-chrome.list | grep deb```

# deb http://dl.google.com/linux/chrome/deb/ stable main

```

I'll reinstall google-chrome later

Thanks

satimis

---

### Post by deadflowr on 2017-10-19
No need to reinstall chrome, you just need to remove the # from the line and also add the [arch=amd64] entry to it
from
```
# deb http://dl.google.com/linux/chrome/deb/ stable main
```
to 
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
then a usual update you do for Ubuntu will update chrome.

---

### Post by satimis on 2017-10-19
> **deadflowr said:**
> No need to reinstall chrome, you just need to remove the # from the line and also add the [arch=amd64] entry to it
from
```
# deb http://dl.google.com/linux/chrome/deb/ stable main
```
to 
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
then a usual update you do for Ubuntu will update chrome.

Hi,

Performed following steps:-

&#10219; sudo nano /etc/apt/sources.list.d/google-chrome.list
uncomment the line;```

# deb http://dl.google.com/linux/chrome/deb/ stable main

```

and change it to read as;```

deb [arm=amd64] http://dl.google.com/linux/chrome/deb/ stable main

```

&#10219; sudo apt update```

......
......
W: GPG error: http://dl.google.com/linux/chrome/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551
E: The repository 'http://dl.google.com/linux/chrome/deb stable Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

&#10219; wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -```

OK

```

&#10219; sudo apt update```

Hit:1 http://hk.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 http://hk.archive.ubuntu.com/ubuntu xenial-security InRelease
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease
Get:6 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]
Get:7 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]
Get:8 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,367 B]
Fetched 2,186 B in 0s (3,172 B/s)     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

&#10219; apt list --upgradable```

Listing... Done
google-chrome-stable/stable 62.0.3202.62-1 amd64 [upgradable from: 48.0.2564.82-1]
initramfs-tools/xenial-updates,xenial-updates 0.122ubuntu8.9 all [upgradable from: 0.122ubuntu8.8]
initramfs-tools-bin/xenial-updates 0.122ubuntu8.9 amd64 [upgradable from: 0.122ubuntu8.8]
initramfs-tools-core/xenial-updates,xenial-updates 0.122ubuntu8.9 all [upgradable from: 0.122ubuntu8.8]

```

&#10219; sudo apt upgrade
&#10219; sudo apt dist-upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

&#10219; google-chrome --version```

Google Chrome 62.0.3202.62 

```

google-chrome is now upgraded to the latest version.

&#10219; sudo apt install cpu-checker

Start Youtube video
It is OK now with screen and sound.

Lot of thanks to all of you for your advice and time spent to help me.

Regards
satimis

---

