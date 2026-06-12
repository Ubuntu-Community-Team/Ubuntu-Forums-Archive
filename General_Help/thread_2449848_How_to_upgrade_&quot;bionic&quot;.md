---
title: "How to upgrade &quot;bionic&quot;?"
date: 2020-09-03
forum: General Help
---

### Post by exhile on 2020-09-03
So when I type the following I get this:

```
exhile@XPS13:~$ apt list --upgradable -a
Listing... Done
dell-linux-assistant/bionic 2.2.0533 amd64 [upgradable from: 2.2.0220]
dell-linux-assistant/now 2.2.0220 amd64 [installed,upgradable to: 2.2.0533]

exhile@XPS13:~$ 
```

Can someone please instruct me what the command line is to do an upgrade of bionic 2.2.0220 amd64 to bionic 2.2.0553?

Much appreciated.

---

### Post by deadflowr on 2020-09-03
Run
```
sudo apt full-upgrade
```
to update the packages.

Note that
```
dell-linux-assistant/now 2.2.0220 amd64 [installed,upgradable to: 2.2.0533]

```is what you currently have.(That's what now means)
and
```
dell-linux-assistant/bionic 2.2.0533 amd64 [upgradable from: 2.2.0220]

```
is the available update

---

### Post by exhile on 2020-09-03
Thanks a lot! :D

Oops, typed too soon.

The full-upgrade didn't change anything.

```
exhile@XPS13:~$ sudo apt full-upgrade
Identified face as exhile
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb dctrl-tools dmraid gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 kpartx kpartx-boot libdebian-installer4
  libdmraid1.0.0.rc16 libllvm9 libtimezonemap-data libtimezonemap1 python3-icu python3-pam rdate
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
exhile@XPS13:~$ apt list --upgradable -a
Listing... Done
dell-linux-assistant/bionic 2.2.0533 amd64 [upgradable from: 2.2.0220]
dell-linux-assistant/now 2.2.0220 amd64 [installed,upgradable to: 2.2.0533]

exhile@XPS13:~$
```

---

### Post by deadflowr on 2020-09-03
Try
```
sudo apt install dell-linux-assistant
```

---

### Post by exhile on 2020-09-03
Okay, I typed that command and received the following:

```
exhile@XPS13:~$ sudo apt install dell-linux-assistant
Identified face as exhile
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 dell-linux-assistant : Depends: libssl1.0.0 (>= 1.0.2~beta3) but it is not installable
E: Unable to correct problems, you have held broken packages.
exhile@XPS13:~$ 



```

---

### Post by deadflowr on 2020-09-03
look at 
```
apt policy libssl1.0.0
```

---

### Post by exhile on 2020-09-03
```
exhile@XPS13:~$ apt policy libssl1.0.0
libssl1.0.0:
  Installed: (none)
  Candidate: (none)
  Version table:
exhile@XPS13:~$ 


```

---

### Post by exhile on 2020-09-03
Can anyone help?

---

### Post by deadflowr on 2020-09-03
> **exhile said:**
> ```
exhile@XPS13:~$ apt policy libssl1.0.0
libssl1.0.0:
  Installed: (none)
  Candidate: (none)
  Version table:
exhile@XPS13:~$ 


```

That's interesting.
My guess is your sources are out of whack.
What does
```
cat /etc/apt/sources.list
```
show?

---

### Post by exhile on 2020-09-03
Yes, I do believe what you say that my sources are out of whack.

```
exhile@XPS13:~$ cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://archive.ubuntu.com/ubuntu/ focal universe
deb http://archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal multiverse
deb http://archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse


exhile@XPS13:~$ 




```

---

### Post by ajgreeny on 2020-09-03
I can't see much wrong with your sources.list file but unless I've missed it, nobody has so far advised you to run command ```
sudo apt update
``` which is essential befor running the ```
sudo apt upgrade
``` command.

So before you get yourself too overwhelmed with this problem, try running both of those two actions as a single terminal command ```
sudo apt update && sudo apt full-upgrade
``` and post back here all terminal output from that using code-tags as you have before.

---

### Post by deadflowr on 2020-09-03
Okay, you're not running bionic, so that package shouldn't exist.
[s]Try this
```
sudo mv /var/lib/apt/list/ /var/lib/apt/lists-old
sudo apt clean
sudo apt update
apt list --upgradeable
```[/s]

On second thought...

I guess you had this ppa:
[https://launchpad.net/~somerville-dla-team/+archive/ubuntu/ppa]("https://launchpad.net/~somerville-dla-team/+archive/ubuntu/ppa")
Which actually has no support for focal.

Best option is to remove it and run
```
sudo add-apt-repository -r ppa:somerville-dla-team/ppa
sudo apt update
sudo apt full-upgrade
```

---

### Post by ajgreeny on 2020-09-03
Well I never! It just shows that sometimes I read what I expect to read and not what's actually written

Can you believe, I didn't even notice the discrepancy between what you were asking for and the fact that your sources.list file is for focal, not bionic.
Also I have no knowledge of the PPA that is necessary for Dell machines so I will leave it to others to deal with this in more detail.

---

### Post by exhile on 2020-09-03
> **ajgreeny said:**
> I can't see much wrong with your sources.list file but unless I've missed it, nobody has so far advised you to run command ```
sudo apt update
``` which is essential befor running the ```
sudo apt upgrade
``` command.

So before you get yourself too overwhelmed with this problem, try running both of those two actions as a single terminal command ```
sudo apt update && sudo apt full-upgrade
``` and post back here all terminal output from that using code-tags as you have before.

I typed the command you suggested and received the following:

```
exhile@XPS13:~$ sudo apt update && sudo apt full-upgrade
Identified face as exhile
Get:1 http://dl.google.com/linux/chrome/deb stable InRelease [1,811 B]
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]                                                                  
Hit:3 http://dell.archive.canonical.com focal InRelease                                                                                    
Hit:4 http://oem.archive.canonical.com focal InRelease                                                                                     
Get:5 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,160 B]                                                           
Hit:6 http://ppa.launchpad.net/boltgolt/howdy/ubuntu focal InRelease                                                                       
Hit:7 http://archive.ubuntu.com/ubuntu focal InRelease                                                                               
Hit:8 http://archive.canonical.com/ubuntu focal InRelease                                                      
Get:9 http://archive.ubuntu.com/ubuntu focal-updates InRelease [111 kB]                        
Hit:10 http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic InRelease
Get:11 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [174 kB]
Get:12 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [24.3 kB]
Get:13 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [4,504 B]
Get:14 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [56.0 kB]
Get:15 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [52.2 kB]    
Get:16 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [2,308 B]            
Get:17 http://archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]                         
Get:18 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [343 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [204 kB]
Get:20 http://archive.ubuntu.com/ubuntu focal-updates/main Translation-en [131 kB]
Get:21 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [204 kB]
Get:22 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [8,876 B]
Get:23 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [164 kB]
Get:24 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [90.0 kB]
Get:25 http://archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [86.7 kB]
Get:26 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [184 kB]
Get:27 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [5,404 B]
Get:28 http://archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:29 http://archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [1,976 B]
Fetched 2,058 kB in 6s (346 kB/s)                                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb dctrl-tools dmraid gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 kpartx kpartx-boot libdebian-installer4
  libdmraid1.0.0.rc16 libllvm9 libtimezonemap-data libtimezonemap1 python3-icu python3-pam rdate
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  firefox firefox-locale-en firefox-locale-zh-hans fonts-noto-mono python3-distupgrade ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 56.8 MB of archives.
After this operation, 123 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-release-upgrader-gtk all 1:20.04.25 [9,360 B]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-release-upgrader-core all 1:20.04.25 [23.7 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 python3-distupgrade all 1:20.04.25 [103 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 firefox amd64 80.0.1+build1-0ubuntu0.20.04.1 [55.3 MB]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 firefox-locale-en amd64 80.0.1+build1-0ubuntu0.20.04.1 [751 kB]            
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 firefox-locale-zh-hans amd64 80.0.1+build1-0ubuntu0.20.04.1 [525 kB]       
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 fonts-noto-mono all 20200323-1build1~ubuntu20.04.1 [80.6 kB]               
Fetched 56.8 MB in 27s (2,121 kB/s)                                                                                                        
(Reading database ... 223681 files and directories currently installed.)
Preparing to unpack .../0-ubuntu-release-upgrader-gtk_1%3a20.04.25_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:20.04.25) over (1:20.04.24) ...
Preparing to unpack .../1-ubuntu-release-upgrader-core_1%3a20.04.25_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:20.04.25) over (1:20.04.24) ...
Preparing to unpack .../2-python3-distupgrade_1%3a20.04.25_all.deb ...
Unpacking python3-distupgrade (1:20.04.25) over (1:20.04.24) ...
Preparing to unpack .../3-firefox_80.0.1+build1-0ubuntu0.20.04.1_amd64.deb ...
Unpacking firefox (80.0.1+build1-0ubuntu0.20.04.1) over (80.0+build2-0ubuntu0.20.04.1) ...
Preparing to unpack .../4-firefox-locale-en_80.0.1+build1-0ubuntu0.20.04.1_amd64.deb ...
Unpacking firefox-locale-en (80.0.1+build1-0ubuntu0.20.04.1) over (80.0+build2-0ubuntu0.20.04.1) ...
Preparing to unpack .../5-firefox-locale-zh-hans_80.0.1+build1-0ubuntu0.20.04.1_amd64.deb ...
Unpacking firefox-locale-zh-hans (80.0.1+build1-0ubuntu0.20.04.1) over (80.0+build2-0ubuntu0.20.04.1) ...
Preparing to unpack .../6-fonts-noto-mono_20200323-1build1~ubuntu20.04.1_all.deb ...
Unpacking fonts-noto-mono (20200323-1build1~ubuntu20.04.1) over (20200323-1) ...
Setting up fonts-noto-mono (20200323-1build1~ubuntu20.04.1) ...
Setting up firefox (80.0.1+build1-0ubuntu0.20.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up python3-distupgrade (1:20.04.25) ...
Setting up firefox-locale-en (80.0.1+build1-0ubuntu0.20.04.1) ...
Setting up ubuntu-release-upgrader-core (1:20.04.25) ...
Setting up ubuntu-release-upgrader-gtk (1:20.04.25) ...
Setting up firefox-locale-zh-hans (80.0.1+build1-0ubuntu0.20.04.1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for fontconfig (2.13.1-2ubuntu3) ...
exhile@XPS13:~$ 

```

---

### Post by exhile on 2020-09-03
> **deadflowr said:**
> Okay, you're not running bionic, so that package shouldn't exist.
[s]Try this
```
sudo mv /var/lib/apt/list/ /var/lib/apt/lists-old
sudo apt clean
sudo apt update
apt list --upgradeable
```[/s]

On second thought...

I guess you had this ppa:
[https://launchpad.net/~somerville-dla-team/+archive/ubuntu/ppa](https://launchpad.net/~somerville-dla-team/+archive/ubuntu/ppa)
Which actually has no support for focal.

Best option is to remove it and run
```
sudo add-apt-repository -r ppa:somerville-dla-team/ppa
sudo apt update
sudo apt full-upgrade
```

This is the output I get when I input your command.

```
exhile@XPS13:~$ sudo add-apt-repository -r ppa:somerville-dla-team/ppa
 
 More info: https://launchpad.net/~somerville-dla-team/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel removing it.

exhile@XPS13:~$ apt list --upgradable
Listing... Done
dell-linux-assistant/bionic 2.2.0533 amd64 [upgradable from: 2.2.0220]
N: There is 1 additional version. Please use the '-a' switch to see it
exhile@XPS13:~$ apt list --upgradable -a
Listing... Done
dell-linux-assistant/bionic 2.2.0533 amd64 [upgradable from: 2.2.0220]
dell-linux-assistant/now 2.2.0220 amd64 [installed,upgradable to: 2.2.0533]

exhile@XPS13:~$ 



```

---

### Post by deadflowr on 2020-09-03
That's not the commands I posted to run, only the first one.

---

### Post by exhile on 2020-09-03
> **deadflowr said:**
> That's not the commands I posted to run, only the first one.

Sorry. Here is the output with the commands you posted.

```
exhile@XPS13:~$ sudo add-apt-repository -r ppa:somerville-dla-team/ppa
Identified face as exhile
 
 More info: https://launchpad.net/~somerville-dla-team/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel removing it.

exhile@XPS13:~$ sudo apt update
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]                                                                  
Hit:3 http://ppa.launchpad.net/boltgolt/howdy/ubuntu focal InRelease                                                                       
Hit:4 http://archive.ubuntu.com/ubuntu focal InRelease                                                                                     
Hit:5 http://archive.canonical.com/ubuntu focal InRelease                                                                                  
Hit:6 http://dell.archive.canonical.com focal InRelease                                                                                    
Get:7 http://archive.ubuntu.com/ubuntu focal-updates InRelease [111 kB]                   
Get:8 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [24.2 kB]         
Hit:9 http://oem.archive.canonical.com focal InRelease                                                                              
Hit:10 http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic InRelease                                                     
Get:11 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [52.1 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]  
Get:13 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [204 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [343 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [204 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [90.0 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [164 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [184 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:20 http://archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [1,976 B]
Fetched 1,586 kB in 4s (378 kB/s)              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
exhile@XPS13:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb dctrl-tools dmraid gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 kpartx kpartx-boot libdebian-installer4
  libdmraid1.0.0.rc16 libllvm9 libtimezonemap-data libtimezonemap1 python3-icu python3-pam rdate
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
exhile@XPS13:~$ apt list --upgradable
Listing... Done
dell-linux-assistant/bionic 2.2.0533 amd64 [upgradable from: 2.2.0220]
N: There is 1 additional version. Please use the '-a' switch to see it
exhile@XPS13:~$ apt list --upgradable -a
Listing... Done
dell-linux-assistant/bionic 2.2.0533 amd64 [upgradable from: 2.2.0220]
dell-linux-assistant/now 2.2.0220 amd64 [installed,upgradable to: 2.2.0533]

exhile@XPS13:~$ 



```

---

### Post by deadflowr on 2020-09-03
Odd.
It's not removing the ppa.
You're pressing Enter and not ctrl+c?

You can try to remove it manually by deleting the ppa's source list file.
```
sudo rm somerville-dla-team-ubuntu-ppa-bionic.list
sudo apt update
```

---

### Post by exhile on 2020-09-04
> **deadflowr said:**
> Odd.
It's not removing the ppa.
You're pressing Enter and not ctrl+c?

You can try to remove it manually by deleting the ppa's source list file.
```
sudo rm somerville-dla-team-ubuntu-ppa-bionic.list
sudo apt update
```

Yes, I am pressing "Enter". Although the directory that you are specifying doesn't exist as the output shows below. 

```
exhile@XPS13:~$ sudo rm somerville-dla-team-ubuntu-ppa-bionic.list
rm: cannot remove 'somerville-dla-team-ubuntu-ppa-bionic.list': No such file or directory


```

---

### Post by deadflowr on 2020-09-04
hmm,
what does 
```
ls /etc/apt/sources.list.d
```
show?

---

### Post by exhile on 2020-09-04
> **deadflowr said:**
> hmm,
what does 
```
ls /etc/apt/sources.list.d
```
show?

```
exhile@XPS13:~$ ls /etc/apt/sources.list.dls
ls: cannot access '/etc/apt/sources.list.dls': No such file or directory


```

---

### Post by exhile on 2020-09-04
> **exhile said:**
> ```
exhile@XPS13:~$ ls /etc/apt/sources.list.dls
ls: cannot access '/etc/apt/sources.list.dls': No such file or directory


```

```
exhile@XPS13:~$ cd /etc/apt/
exhile@XPS13:/etc/apt$ ls -la
total 48
drwxr-xr-x   7 root root  4096 Aug 10 19:24 .
drwxr-xr-x 143 root root 12288 Sep  3 16:05 ..
drwxr-xr-x   2 root root  4096 Sep  3 00:21 apt.conf.d
drwxr-xr-x   2 root root  4096 Apr  9 03:21 auth.conf.d
drwxr-xr-x   2 root root  4096 Apr  9 03:21 preferences.d
-rw-r--r--   1 root root  2643 Sep  3 20:35 sources.list
-rw-rw-r--   1 root root  2642 Aug  9 08:10 sources.list~
drwxr-xr-x   2 root root  4096 Sep  3 16:08 sources.list.d
-rw-r--r--   1 root root  2643 Sep  3 20:35 sources.list.save
drwxr-xr-x   2 root root  4096 Aug 10 19:24 trusted.gpg.d
exhile@XPS13:/etc/apt$ ls /etc/apt/sources.list
/etc/apt/sources.list
exhile@XPS13:/etc/apt$ ls /etc/apt/sources.list.d
boltgolt-ubuntu-howdy-focal.list       google-chrome.list                    somerville-dla-team-ubuntu-ppa-bionic.list
boltgolt-ubuntu-howdy-focal.list.save  google-chrome.list.save               somerville-dla-team-ubuntu-ppa-bionic.list.save
focal-oem.list                         oem-somerville-melisa-meta.list       somerville-dla-team-ubuntu-ppa-focal.list
focal-oem.list.save                    oem-somerville-melisa-meta.list.save  somerville-dla-team-ubuntu-ppa-focal.list.save
exhile@XPS13:/etc/apt$ 



```

---

### Post by exhile on 2020-09-04
The file, "somerville-dla-team-ubuntu-ppa-bionic.list" shows in the directory "/etc/apt/sources.list.d" but I can't seem to delete it.

---

### Post by exhile on 2020-09-04
> **exhile said:**
> The file, "somerville-dla-team-ubuntu-ppa-bionic.list" shows in the directory "/etc/apt/sources.list.d" but I can't seem to delete it.

Actually, I was able to delete both files for some strange reason.

Problem fixed.

Thanks @deadflower.

---

### Post by deadflowr on 2020-09-04
Duh.
My bad. it should have been
```
sudo rm /etc/apt/sources.list.d/somerville-dla-team-ubuntu-ppa-bionic.list
```

Another option you might also try would be to run
```
sudo sed -i 's/deb/#deb/' /etc/apt/sources.list.d/somerville-*
```
this would manually disable the entries by commenting them out.

And another option, of course, is to disable them in Software and Updates if running the Desktop version.
(Software and Updates > Other Software tab and uncheck the entries listed for somerville.
This is probably the method we should have tried earlier, if possible)

---

