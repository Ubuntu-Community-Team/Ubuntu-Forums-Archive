---
title: "Newbie here. How to fully remove uninstall Balena Etcher?"
date: 2023-05-20
forum: General Help
---

### Post by Advait on 2023-05-20
Ubuntu 22.04. I'm getting this error when I run sudo apt update:

```
E: Failed to fetch https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu/dists/jammy/InRelease  402  Payment Required [IP: 2600:9000:2149:4200:e:f4d2:20c0:93a1 443]
E: The repository 'https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

So how to get rid of Balena? It's a deb package.

I successfully ran the command:

[B]sudo apt-get remove balena-etcher-electron
and
sudo apt-get purge balena-etcher-electron[/B]

but it didn't work. Got the same error after again running sudo apt update.

```

advait@advait-Bravo-15-A4DDR:~$ sudo apt-get remove balena-etcher-electron
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'balena-etcher-electron' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

advait@advait-Bravo-15-A4DDR:~$ sudo apt-get purge balena-etcher-electron
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'balena-etcher-electron' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

advait@advait-Bravo-15-A4DDR:~$ sudo apt update
Err:1 https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy InRelease                                                                                                         
  402  Payment Required [IP: 2600:9000:2149:ee00:e:f4d2:20c0:93a1 443]
Hit:2 https://packages.microsoft.com/repos/edge stable InRelease                                                                                                                       
Hit:3 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                       
Hit:4 https://apt.syncthing.net syncthing InRelease
Hit:5 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:6 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:7 http://archive.ubuntu.com/ubuntu jammy-security InRelease
Hit:8 http://dl.google.com/linux/chrome/deb stable InRelease                                                             
Hit:9 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease                                            
Hit:10 https://ppa.launchpadcontent.net/thierry-f/fork-michael-gruz/ubuntu jammy InRelease
Hit:11 https://ppa.launchpadcontent.net/ubuntu-mozilla-security/ppa/ubuntu jammy InRelease
Reading package lists... Done
E: Failed to fetch https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu/dists/jammy/InRelease  402  Payment Required [IP: 2600:9000:2149:ee00:e:f4d2:20c0:93a1 443]
E: The repository 'https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
advait@advait-Bravo-15-A4DDR:~$

```

---

### Post by TheFu on 2023-05-20
```
Package 'balena-etcher-electron' is not installed, so not removed
```
You need to determine the correct name for the package.
Try 
```
sudo apt search '*etcher*'
```
Then purge that package and remove the PPA that you added.  **Synaptic** might be easier for all of this.  It is handy for a number things that newer tools have decided shouldn't be needed because the GUI designers dumbed down the interface just a little too far.

---

### Post by Advait on 2023-05-20
> **TheFu said:**
> You need to determine the correct name for the package.
Try 
```
sudo apt search '*etcher*'
```
Then purge that package and remove the PPA that you added.  **Synaptic** might be easier for all of this.  It is handy for a number things that newer tools have decided shouldn't be needed because the GUI designers dumbed down the interface just a little too far.

```
advait@advait-Bravo-15-A4DDR:~$ sudo apt search '*etcher*'
[sudo] password for advait: 
E: Regex compilation error
advait@advait-Bravo-15-A4DDR:~$ 

```

Someway to fix this error?

*balena-etcher-electron* is the only thing I find when I run **dpkg --get-selections**. No other instances of "etcher" or "balena".

Where else could this **balena** package be hiding? Is it like some kinda rootkit?

---

### Post by TheFu on 2023-05-20
Try a different search term.  Don't wait for me.

If you remove the PPA and the package isn't there anymore, it will be orphaned and could prevent other updates from being installed due to dependencies. If apt doesn't work to remove the package, I suppose you can use dpkg directly, but this shouldn't be the first method used.  Using dpkg for anything other than getting information can be dangerous.  Try apt, apt-get, aptitude, synaptic all first.  If those don't work, use dpkg and be prepared for other APT DB issues.

I haven't looked at Etcher in years.  Way too much bloat for just copying bits from A ---> B.  **cp** can do that.

---

### Post by Impavidus on 2023-05-20
Your problem is not with the package, but with the repository. Make sure all packages from that repository are gone (which may already be the case), then remove the repository.

---

### Post by Advait on 2023-05-21
> **Impavidus said:**
> Your problem is not with the package, but with the repository. Make sure all packages from that repository are gone (which may already be the case), then remove the repository.

Here's my apt policy results for balena:
```
 500 https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy/main i386 Packages
     release o=cloudsmith/balena/etcher,a=jammy,n=jammy,c=main,b=i386
     origin dl.cloudsmith.io
 500 https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy/main amd64 Packages
     release o=cloudsmith/balena/etcher,a=jammy,n=jammy,c=main,b=amd64
     origin dl.cloudsmith.io

```

So I ran these commands:

```
advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith/balena/etcher
[sudo] password for advait: 
Unable to handle repository shortcut 'ppa:cloudsmith/balena/etcher'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith/balena/etcher,a=jammy,n=jammy,c=main,b=amd64
Unable to handle repository shortcut 'ppa:cloudsmith/balena/etcher,a=jammy,n=jammy,c=main,b=amd64'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith/balena/etcher ,a=jammy,n=jammy,c=main,b=amd64
\^[[AUnable to handle repository shortcut 'ppa:cloudsmith/balena/etcher ,a=jammy,n=jammy,c=main,b=amd64'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith/balena/etcher ,a=jammy,n=jammy,c=main,b=amd64
Unable to handle repository shortcut 'ppa:cloudsmith/balena/etcher ,a=jammy,n=jammy,c=main,b=amd64'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith.io/public/balena/etcher/deb/
Unable to handle repository shortcut 'ppa:cloudsmith.io/public/balena/etcher/deb/'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith.io/public/balena/etcher/deb
Unable to handle repository shortcut 'ppa:cloudsmith.io/public/balena/etcher/deb'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith.io/public/balena/etcher
Unable to handle repository shortcut 'ppa:cloudsmith.io/public/balena/etcher'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:cloudsmith.io/public/balena/etcher/
Unable to handle repository shortcut 'ppa:cloudsmith.io/public/balena/etcher/'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:dl.cloudsmith.io/public/balena/etcher/deb/ubuntu
Unable to handle repository shortcut 'ppa:dl.cloudsmith.io/public/balena/etcher/deb/ubuntu'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:dl.cloudsmith.io/public/balena/etcher/deb/
Unable to handle repository shortcut 'ppa:dl.cloudsmith.io/public/balena/etcher/deb/'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:dl.cloudsmith.io/public/balena/etcher/deb
Unable to handle repository shortcut 'ppa:dl.cloudsmith.io/public/balena/etcher/deb'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:dl.cloudsmith.io/public/balena/etcher/
Unable to handle repository shortcut 'ppa:dl.cloudsmith.io/public/balena/etcher/'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:dl.cloudsmith.io/public/balena/etcher
Unable to handle repository shortcut 'ppa:dl.cloudsmith.io/public/balena/etcher'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:dl.cloudsmith.io/public/balena/
Unable to handle repository shortcut 'ppa:dl.cloudsmith.io/public/balena/'

advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository --remove ppa:dl.cloudsmith.io/public/balena
Unable to handle repository shortcut 'ppa:dl.cloudsmith.io/public/balena'

advait@advait-Bravo-15-A4DDR:~$ 

```

What's the error? How to fix?

---

### Post by Holger_Gehrke on 2023-05-21
> **Advait said:**
> ```
advait@advait-Bravo-15-A4DDR:~$ sudo apt search '*etcher*'
[sudo] password for advait: 
E: Regex compilation error
advait@advait-Bravo-15-A4DDR:~$ 

```

Someway to fix this error?


'apt search' does a full text search. If it finds any special characters in the search expression it expects a regular expression, not a glob. So it should either be 'apt search etcher' or "apt search '.*etcher.*'. Both are equivalent but the first - not having to bother using a regex parser - is a lot faster and gives the same results in this case.

And your problem with add-apt-repository is down to the fact that this isn't a PPA. If you use the 'ppa:x/y' notation, apt assumes it's an address on launchpad of the form 'https://ppa.launchpad.net/x/y/ppa/ubuntu'. To remove the repository you could try:
```

add-apt-repository -r https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu

```

Holger

---

### Post by qyot27 on 2023-05-21
The error is that you're using 'ppa:' on something that isn't a ppa.

Just go into the Software Sources GUI dialog and remove it from there.

---

### Post by Advait on 2023-05-21
> **qyot27 said:**
> The error is that you're using 'ppa:' on something that isn't a ppa.

Just go into the Software Sources GUI dialog and remove it from there.

You mean the "Other Software" tab in "Software and Updates"? There's nothing there that mentions "balena" or "etcher".

Please advise how to remove disconnect this Balena repository.

How do I find this "Software Sources GUI dialog"? Which app has it?

Balena etcher is not in any "installed software" list.

I found balena etcher in Synaptic. They are unckecked and the "Mark for Removal" option is greyed out not allowed. Please advise. I'm only allowed to mark them for installation.

---

### Post by Advait on 2023-05-21
> **Holger_Gehrke said:**
> 'apt search' does a full text search. If it finds any special characters in the search expression it expects a regular expression, not a glob. So it should either be 'apt search etcher' or "apt search '.*etcher.*'. Both are equivalent but the first - not having to bother using a regex parser - is a lot faster and gives the same results in this case.

And your problem with add-apt-repository is down to the fact that this isn't a PPA. If you use the 'ppa:x/y' notation, apt assumes it's an address on launchpad of the form 'https://ppa.launchpad.net/x/y/ppa/ubuntu'. To remove the repository you could try:
```

add-apt-repository -r https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu

```

Holger

Here's the result: (any way to fix the errors?) (Also, does the "402 Payment Required [IP: 2600:9000:2149:7400:e:f4d2:20c0:93a1 443]" line give a clue as to the real source of the problem?)

```
advait@advait-Bravo-15-A4DDR:~$ sudo add-apt-repository -r https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu
[sudo] password for advait: 
Repository: 'deb https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy main'
Description:
Archive for codename: jammy components: main
More info: https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu
Removing repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 https://packages.microsoft.com/repos/edge stable InRelease                                                                                                                                            
Err:3 https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy InRelease                                                                                                     
  402  Payment Required [IP: 2600:9000:2149:7400:e:f4d2:20c0:93a1 443]
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                                       
Hit:5 https://apt.syncthing.net syncthing InRelease                                                        
Get:6 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                                    
Hit:7 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease                   
Get:8 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]                        
Get:9 http://archive.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                       
Get:10 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [101 kB]
Hit:11 https://ppa.launchpadcontent.net/thierry-f/fork-michael-gruz/ubuntu jammy InRelease
Get:12 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [269 kB]            
Get:13 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]                                       
Get:14 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [8,000 B]
Get:15 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12.9 kB]                     
Get:16 http://archive.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [41.4 kB]                                               
Get:17 http://archive.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [18.5 kB]                                           
Hit:18 https://ppa.launchpadcontent.net/ubuntu-mozilla-security/ppa/ubuntu jammy InRelease                                               
Reading package lists... Done                                                                                                                                                                               
E: Failed to fetch https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu/dists/jammy/InRelease  402  Payment Required [IP: 2600:9000:2149:7400:e:f4d2:20c0:93a1 443]
E: The repository 'https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
advait@advait-Bravo-15-A4DDR:~$
```

---

### Post by Advait on 2023-05-21
Note: These errors are preventing me from updating pihole (installed on my laptop).

Is there some other way to update pihole? Normally I use "pihole -up" but that's not working cuz the PPA errors.

---

### Post by TheFu on 2023-05-21
> **Advait said:**
> Note: These errors are preventing me from updating pihole (installed on my laptop).

Is there some other way to update pihole? Normally I use "pihole -up" but that's not working cuz the PPA errors.

Why not just manually remove the problem URL from under /etc/apt/sources* ... it is probably in a subdirectory, but might be inside some other file.

After removing it, don't forget to 
**sudo apt update**

Are you running the pihole software on this same OS image?  You aren't using a Linux Container or VM ... following best practices?

---

### Post by Holger_Gehrke on 2023-05-21
It says it has removed it and then continues to look for the repository ??? That's a new one. Could be that it's in there multiple times. I guess we have to do it manually. Information about repositories is stored in the file /etc/apt/sources.list and in files in /etc/apt/sources.list.d/. If the repository in question is in the former, use sudoedit to edit the file and remove the line referencing that repository. If it's in the latter it's usually one file per repository. Check the files and remove the file for that one (or if there's multiple repos in one file, you can sudoedit that one ...). After you've done that try 'apt update' and 'apt upgrade' again.

Holger

---

### Post by jeremy31 on 2023-05-21
Try in terminal ```
sudo apt install inxi && inxi -r
```
That should show where another repo would be at

---

### Post by #&amp;thj^% on 2023-05-21
> **jeremy31 said:**
> Try in terminal ```
sudo apt install inxi && inxi -r
```
That should show where another repo would be at
+1
If nothing there is helpful 
I just use the appimage:
On mine most is found here:
```
ls /home/me/.config/balena-etcher/
 Cache            'Crash Reports'  'Network Persistent State'   blob_storage
'Code Cache'       Dictionaries     Preferences
 Cookies           GPUCache        'Session Storage'
 Cookies-journal  'Local Storage'   TransportSecurity

```
To Uninstall and this is from there Offical Git Hub:[https://github.com/balena-io/etcher#uninstall](https://github.com/balena-io/etcher#uninstall)
```

sudo apt remove --purge balena-etcher
apt clean
rm -rf /var/lib/apt/lists/*
sudo apt update
```
****But** before you run all those, please show us this:**
```
cat /var/lib/apt/lists/*
```

---

### Post by Advait on 2023-05-22
> **jeremy31 said:**
> Try in terminal ```
sudo apt install inxi && inxi -r
```
That should show where another repo would be at

I'm a newbie so I don't understand your post. Could you explain it in more detail and newbie friendly? I don't want to run a command until I have at least a vague idea what it does.

---

### Post by Advait on 2023-05-22
> **1fallen said:**
> ****But** before you run all those, please show us this:**
```
cat /var/lib/apt/lists/*
```

I ran the command and it gave about 50 or 60 pages of output text in the terminal. Looks like there's no way to Select All. The shortcut only selected one screen.

You know a way to Select All in the Linux terminal?

Is there a Terminal app that has a built-in Select All function?

---

### Post by #&amp;thj^% on 2023-05-22
> **Advait said:**
> I'm a newbie so I don't understand your post. Could you explain it in more detail and newbie friendly? I don't want to run a command until I have at least a vague idea what it does.
inxi is a tool that monitors your system IE:
```
inxi -r
Repos:
  Active pacman repo servers in: /etc/pacman.d/mirrorlist
    1: https://mirror.osbeck.com/archlinux/$repo/os/$arch
    2: https://mirror.lty.me/archlinux/$repo/os/$arch
    3: https://mirrors.n-ix.net/archlinux/$repo/os/$arch
    4: https://gluttony.sin.cvut.cz/arch/$repo/os/$arch
    5: https://mirror.dkm.cz/archlinux/$repo/os/$arch
    6: https://ftp.sh.cvut.cz/arch/$repo/os/$arch
    7: https://mirror.telepoint.bg/archlinux/$repo/os/$arch
    8: https://mirror.f4st.host/archlinux/$repo/os/$arch
    9: https://mirror.alwyzon.net/archlinux/$repo/os/$arch
    10: https://mirror.ubrco.de/archlinux/$repo/os/$arch
    11: https://mirror.sunred.org/archlinux/$repo/os/$arch
    12: https://mirror.cyberbits.eu/archlinux/$repo/os/$arch
    13: https://archlinux.mailtunnel.eu/$repo/os/$arch
    14: https://mirror.lcarilla.de/archlinux/$repo/os/$arch
    15: https://arch.mirror.zachlge.org/$repo/os/$arch
    16: https://mirrors.abhy.me/archlinux/$repo/os/$arch
    17: https://archlinux.thaller.ws/$repo/os/$arch
    18: https://archlinux.homeinfo.de/$repo/os/$arch
    19: https://dist-mirror.fem.tu-ilmenau.de/archlinux/$repo/os/$arch
    20: https://ftp.psnc.pl/linux/archlinux/$repo/os/$arch

```
That's for my Arch system, So is it a little clearer now?

> **Advait said:**
> I ran the command and it gave about 50 or 60 pages of output text in the terminal. Looks like there's no way to Select All. The shortcut only selected one screen.

You know a way to Select All in the Linux terminal?

Is there a Terminal app that has a built-in Select All function?

Please run it as:
```
cat /var/lib/apt/lists/* >apt-list.txt
```
Now you have a file in your home directory named "apt-list.txt"

---

### Post by Advait on 2023-05-22
> **1fallen said:**
> inxi is a tool that monitors your system IE:


Thanks for the further info. I did a search for "Ubuntu Linux system IE" and it was all links about internet explorer.

So what is "system IE"?

---

### Post by Advait on 2023-05-23
> **1fallen said:**
> Please run it as:
```
cat /var/lib/apt/lists/* >apt-list.txt
```
Now you have a file in your home directory named "apt-list.txt"

OK, I ran the command and I see the file. Here's the section about balena (see below). (The total file size is 205MB. The Ubuntuforums uploader was taking forever to upload it and I gave up. How would you like me to show you or send you the whole file?)

Do you have enough info now to give me a solution to my original problem? What other info you need?

PS: What is the single file size limit for Ubuntuforums attachments? What is the size limit for all Ubuntuforums attachments?

------------------- (no other instances of the text string "balena" outside the below block of text) ---------------------------------

Origin: cloudsmith/balena/etcher
Codename: jammy
Date: Tue, 14 Feb 2023 11:56:52 UTC
Architectures: amd64 arm64 armel armhf i386
Components: main
Suite: jammy
Acquire-By-Hash: yes
MD5Sum:
 b6ca35ad2be57220a72e58fa02d20aad 106 main/binary-amd64/Release
 761789b7f2d1f15aa7021f400427bcdd 9672 main/binary-amd64/Packages
 18ab7499be381314c8ee6395f7b8bb70 1681 main/binary-amd64/Packages.gz
 2754492c006df7cc6368c38a6a21ff3e 106 main/binary-arm64/Release
 d41d8cd98f00b204e9800998ecf8427e 0 main/binary-arm64/Packages
 d41d8cd98f00b204e9800998ecf8427e 0 main/binary-arm64/Packages.gz
 cb54b76fa431a281b2f64f1cb0f2e464 106 main/binary-armel/Release
 d41d8cd98f00b204e9800998ecf8427e 0 main/binary-armel/Packages
 d41d8cd98f00b204e9800998ecf8427e 0 main/binary-armel/Packages.gz
 2f7295d9a6377ca8997b996f35582acc 106 main/binary-armhf/Release
 d41d8cd98f00b204e9800998ecf8427e 0 main/binary-armhf/Packages
 d41d8cd98f00b204e9800998ecf8427e 0 main/binary-armhf/Packages.gz
 625a4e4904c8a26ba55768210cd54a22 105 main/binary-i386/Release
 9ba18012dc06df9ad9f50e03f746a384 6870 main/binary-i386/Packages
 331cbd6101f84bae796e3d5dfbaf0d2e 1363 main/binary-i386/Packages.gz
 58f47488b29892dd9ef252a48876e6a6 107 main/source/Release
 d41d8cd98f00b204e9800998ecf8427e 0 main/source/Sources
 d41d8cd98f00b204e9800998ecf8427e 0 main/source/Sources.gz
SHA1:
 4b60b64cc15ab7787795b9c5dd4c81ee97b7a026 106 main/binary-amd64/Release
 dd748a3b6680231239578f628871c5ef06216e29 9672 main/binary-amd64/Packages
 6c3d2f91ec532181b3248e75377ecc588d1107e9 1681 main/binary-amd64/Packages.gz
 7abaf869c8c20a9303da9c82157a97ed161a3354 106 main/binary-arm64/Release
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/binary-arm64/Packages
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/binary-arm64/Packages.gz
 16936a404088de7c68da15a62bd2449c658d23b1 106 main/binary-armel/Release
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/binary-armel/Packages
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/binary-armel/Packages.gz
 4bf99eac86965bb1a0cb605b91d0a1ae36f0cad3 106 main/binary-armhf/Release
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/binary-armhf/Packages
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/binary-armhf/Packages.gz
 acdeb342e7e66146714543c7bcfe23c91145da5c 105 main/binary-i386/Release
 45ad13369989854b680d2ef6d9ddeb7388c68f38 6870 main/binary-i386/Packages
 95f0d3183146733dd5163c367bfa162b58a7b98c 1363 main/binary-i386/Packages.gz
 dc84ff4f5e682c5ab0bf4dda90a1e70b4c22d3fb 107 main/source/Release
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/source/Sources
 da39a3ee5e6b4b0d3255bfef95601890afd80709 0 main/source/Sources.gz
SHA256:
 0e99f41f128075864757ac43f402054aa28527745bed90072041232f7f2a2333 106 main/binary-amd64/Release
 413da6a6aeb32fc9110481d49f94ab85aa08925819c38f52ad67b9429ae158b0 9672 main/binary-amd64/Packages
 fa8c7ad8338c465ebcc3b993085f5ddec9da47fe0a9674bbc41e87f6fad55524 1681 main/binary-amd64/Packages.gz
 b9f0c2b46cd57a843f51eb7e50820a4102c084582543031f83b472842d888877 106 main/binary-arm64/Release
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/binary-arm64/Packages
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/binary-arm64/Packages.gz
 6b1e86ebbf290fb4f13593c4b8a2b035f4d856b2cced55dd48df6ea4cdd38a7d 106 main/binary-armel/Release
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/binary-armel/Packages
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/binary-armel/Packages.gz
 5b925eae4e8beda9c3e1d791c1f3bb0c261cde5a856fd102ce926987574c6f1e 106 main/binary-armhf/Release
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/binary-armhf/Packages
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/binary-armhf/Packages.gz
 ec6950707fd1d41f81d88ce29a0e0a3149b38d841933f8075f0504a946cb3d94 105 main/binary-i386/Release
 b3a162f3d6478e6e38d5cc620a5c3192c47befd2869f0ae0f1a4cd67f9177b8e 6870 main/binary-i386/Packages
 6f5de28566df80cba017beaf6c11660ece0a30fe3c51afc0881ef31be2318ae5 1363 main/binary-i386/Packages.gz
 fb3a7968ac3379e5a0d553904519152655ffeff0156584cfddc5fad3140b1d90 107 main/source/Release
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/source/Sources
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 main/source/Sources.gz

-----END PGP SIGNATURE-----
Package: balena-etcher
Version: 1.13.3
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: amd64
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 220535
Depends: gconf-service, gconf2, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgbm1, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk-3-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Recommends: libappindicator3-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher_1.13.3/balena-etcher_1.13.3_amd64.deb
Size: 85250174
MD5Sum: d4f60961ae86b6eff52b1a15b5677cdf
SHA1: c40a953feeca6c143b3e1d115eac3379f854fae9
SHA256: 823636775fdd6408f3a2972f8e7c95c5fec71fbbd2d707c2b4a2a422ef2dd7c8

Package: balena-etcher
Version: 1.14.3
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: amd64
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 220856
Depends: gconf-service, gconf2, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgbm1, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk-3-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Recommends: libappindicator3-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher_1.14.3/balena-etcher_1.14.3_amd64.deb
Size: 85226398
MD5Sum: e2b4819b7e1c1c5ef8cd78afb94d0ccc
SHA1: ff161ba9af93f8a2e9aa1feceb994de9f11a7114
SHA256: 44f4c4eb3a802a7f73015842351fd1a0c33fa26413bfbe1dc0b9f8e4f03c727c

Package: balena-etcher-electron
Version: 1.5.117
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: amd64
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 225280
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.5.117_amd64.deb
Size: 86786746
MD5Sum: c2b6a28c89418af9deef263adb1c08af
SHA1: 7f6af40bd964e0078aeb14189a8ba5e3dac88df0
SHA256: 302e4c2c78c6fd5acfa013eb99da415129ac4abd1097a58966bb00f29c62dd0e

Package: balena-etcher-electron
Version: 1.7.2
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: amd64
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 222372
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.2/balena-etcher-electron_1.7.2_amd64.deb
Size: 86769044
MD5Sum: 599225303d1f60ba9235ffac1f11db22
SHA1: b67bb1a4c16e107e5efbe4e5bfd6401b03f4e384
SHA256: be4461d6e508ce918f02a947cd36640eca1a38b3b63226f9af213f23456cafbe

Package: balena-etcher-electron
Version: 1.7.3
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: amd64
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 222372
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.3/balena-etcher-electron_1.7.3_amd64.deb
Size: 86767448
MD5Sum: 7a7f4a1282b032a9c923f837743ef88f
SHA1: f88c8fc1872b7b1d70f7deb08072534f660522d9
SHA256: 53d8b363fdb45e92dfbe4dae2c16e57197e5e03c7157c9c5fe17db94d8f246fa

Package: balena-etcher-electron
Version: 1.7.7
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: amd64
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 222394
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.7/balena-etcher-electron_1.7.7_amd64.deb
Size: 86766826
MD5Sum: ba5a0b4b3ac95e5858f396397f21e490
SHA1: 43a3988fbc01a69472fedf970a2f1eb9c9d2685a
SHA256: 643303fc6692aad27678ecd6ceb57eddcb068e392797ad14a426431e637ec0fc

Package: balena-etcher-electron
Version: 1.7.9
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: amd64
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 222394
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.9/balena-etcher-electron_1.7.9_amd64.deb
Size: 86767140
MD5Sum: 9626211380e9d0043979bfa23b423e2d
SHA1: 0ded0a3bbc52d5da2c94aff93a1adce46eedcef5
SHA256: 941a03678408b67f7b2b6d3dad48a3e1070eadb53af561c292d7da93b26a91e5

Package: balena-etcher-electron
Version: 1.5.117
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: i386
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 208779
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.5.117_i386.deb
Size: 84962208
MD5Sum: 053fec9c39fd5c14a10e61d3bc07aa7f
SHA1: 643072ee042191fff5d79a0dd388d5b856b934b6
SHA256: a15e56b7748b3f36c54b08c585c3b21e0b608d95c09dc7fd95d620f07521de7c

Package: balena-etcher-electron
Version: 1.7.2
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: i386
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 205897
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.2/balena-etcher-electron_1.7.2_i386.deb
Size: 85027498
MD5Sum: 650de6eedee0a58df798250df5c9dbf2
SHA1: 6275c411425c02edf1089d1dd74ada71e26cc2d1
SHA256: ba7f03639f6413112ca80c1d5cb71f148622c3dfb7875a567614e5200a6fdeea

Package: balena-etcher-electron
Version: 1.7.3
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: i386
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 205897
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.3/balena-etcher-electron_1.7.3_i386.deb
Size: 85027840
MD5Sum: e1cc0285d346c1c71cfd29ccbfbd0e7c
SHA1: 99d19b03e4ffb3bddd6cf32cb7e96d88fe8b70a0
SHA256: bfee234c645c8f8b4dec586d1ebbb0ce4642857cedd960c84614cac03b66ad25

Package: balena-etcher-electron
Version: 1.7.7
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: i386
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 205930
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.7/balena-etcher-electron_1.7.7_i386.deb
Size: 85050446
MD5Sum: c4f277ff6e25d19cf60a4308ab4f446d
SHA1: cf2e9f30610b3df1e0f2b181f85118699f794bf0
SHA256: bcde1b126be3e4b725e77781b1955e6dc6b57853ae031e1e56e3419c8f478536

Package: balena-etcher-electron
Version: 1.7.9
License: Apache-2.0
Vendor: Balena Inc. <hello@etcher.io>
Architecture: i386
Maintainer: Balena Inc. <hello@etcher.io>
Installed-Size: 205930
Depends: gconf2, gconf-service, libasound2, libatk1.0-0, libc6, libcairo2, libcups2, libdbus-1-3, libexpat1, libfontconfig1, libfreetype6, libgcc1, libgconf-2-4, libgdk-pixbuf2.0-0, libglib2.0-0, libgtk2.0-0, liblzma5, libnotify4, libnspr4, libnss3, libpango1.0-0 | libpango-1.0-0, libstdc++6, libx11-6, libxcomposite1, libxcursor1, libxdamage1, libxext6, libxfixes3, libxi6, libxrandr2, libxrender1, libxss1, libxtst6, polkit-1-auth-agent | policykit-1-gnome | polkit-kde-1
Section: utils
Priority: optional
Homepage: [https://github.com/balena-io/etcher](https://github.com/balena-io/etcher)
Description: balenaEtcher is a powerful OS image flasher built with web technologies to ensure flashing an SDCard or USB drive is a pleasant and safe experience. It protects you from accidentally writing to your hard-drives, ensures every byte of data was written correctly and much more.
  Flash OS images to SD cards and USB drives, safely and easily.
Filename: pool/any-version/main/b/ba/balena-etcher-electron_1.7.9/balena-etcher-electron_1.7.9_i386.deb
Size: 85051786
MD5Sum: 84a68f0ca7031fe8013fb767bb159e2a
SHA1: 25d449359fd8e05e3151546070d55664a17b7cfa
SHA256: 458d138184d10783129af739452d3bfe01a37b37a96810e84407ce24412494ca

----------------------------- [[ no more instances of text string "balena" in the file. ]] --------------------------------

---

### Post by idmbe on 2023-05-23
follow this link hope will helpful for you:
[https://github.com/balena-io/etcher/issues/4034#issuecomment-1537215813](https://github.com/balena-io/etcher/issues/4034#issuecomment-1537215813)

---

### Post by Advait on 2023-05-23
> **idmbe said:**
> follow this link hope will helpful for you:
[https://github.com/balena-io/etcher/issues/4034#issuecomment-1537215813](https://github.com/balena-io/etcher/issues/4034#issuecomment-1537215813)

Thanks for the link. I looked at it and it's way above my skill level. 

Hopefully someone can offer a solution that a newbie could follow...?

---

### Post by idmbe on 2023-05-23
in simple way type this:
```
 sudo rm /etc/apt/sources.list.d/balena-etcher.list
```

then: 
```
 sudo apt-update
```

---

### Post by #&amp;thj^% on 2023-05-23
> **Advait said:**
> Thanks for the further info. I did a search for "Ubuntu Linux system IE" and it was all links about internet explorer.

So what is "system IE"?
My goodness IE is short for "an example" you do have much to learn, I'm not being rude just stating the obvious. ;)

> **Advait said:**
> OK, I ran the command and I see the file. Here's the section about balena (see below). (The total file size is 205MB. The Ubuntuforums uploader was taking forever to upload it and I gave up.**_ How would you like me to show you or send you the whole file?)_**


You should have compressed the that file. In other words Create an Archive with a simple right click on that file, then use the attachment tool in the thread to upload it.
But I've seen enough now and I hope you have a back-up of everything you need and want before running this now:
```
sudo apt clean
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```
Post back any errors shown.

---

### Post by Advait on 2023-05-23
> **1fallen said:**
> My goodness IE is short for "an example" you do have much to learn, I'm not being rude just stating the obvious. ;)

Please note that "IE" is incorrect. Correct spelling is "i.e." which is short for "that is". While "e.g." is short for "an example" or "for example".

So if you meant to write "an example", you should have used "e.g.", not IE.

Correct usage within a sentence is always lower case with periods. Never upper case without periods.

Please note this for future reference.

In my 50 years of reading text I've never seen i.e. written as IE. For the last 25 years or so, IE has almost always stood for Internet Explorer in tech circles.

---

### Post by QIII on 2023-05-24
OK.  Let's avoid the English lessons regarding abbreviations of Latin phrases.

I'll refrain from explaining z.B. and d.h.

---

### Post by Advait on 2023-05-24
> **QIII said:**
> OK.  Let's avoid the English lessons regarding abbreviations of Latin phrases.

I'll refrain from explaining z.B. and d.h.

If someone writes something here that's incorrect *and* confusing, I will always politely correct them. If they write something that's incorrect, but not so confusing and the correct meaning can still be discerned, I'll likely let it slide.

If I write something that's incorrect and confusing, I want people to correct me so I can learn.

As a Linux newb, I've been corrected quite a few times on this forum, and those corrections have helped me learn.

---

### Post by Advait on 2023-05-24
> **idmbe said:**
> in simple way type this:
```
 sudo rm /etc/apt/sources.list.d/balena-etcher.list
```

then: 
```
 sudo apt-update
```

(Note, I changed "apt-update" to "apt update")

Yay! It seemed to work. Thanks!

```
advait@advait-Bravo-15-A4DDR:~$ sudo rm /etc/apt/sources.list.d/balena-etcher.list
[sudo] password for advait: 
advait@advait-Bravo-15-A4DDR:~$ sudo apt update
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 https://packages.microsoft.com/repos/edge stable InRelease                                                                                                                                            
Hit:3 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                                       
Get:4 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                                                               
Hit:5 https://apt.syncthing.net syncthing InRelease                                                                  
Hit:6 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease                                        
Get:7 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]                        
Hit:8 https://ppa.launchpadcontent.net/thierry-f/fork-michael-gruz/ubuntu jammy InRelease
Get:9 http://archive.ubuntu.com/ubuntu jammy-security InRelease [110 kB]              
Get:10 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [609 kB]               
Hit:11 https://ppa.launchpadcontent.net/ubuntu-mozilla-security/ppa/ubuntu jammy InRelease     
Get:12 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [397 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [101 kB]
Get:14 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [906 kB]
Get:15 http://archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [612 kB]
Get:16 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [269 kB]
Get:17 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:18 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [7,976 B]                                                                                                                
Get:19 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [16.8 kB]                                                                                                            
Get:20 http://archive.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [41.6 kB]                                                                                                                 
Get:21 http://archive.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [18.5 kB]                                                                                                             
Fetched 3,316 kB in 7s (450 kB/s)                                                                                                                                                                           
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.
advait@advait-Bravo-15-A4DDR:~$
```

Also I was finally able to successfully update my pihole. Nice.

---

### Post by lazarushari on 2023-07-20
I have solved this issue in simple steps just go to /etc/apt/ there will be a directory name sources.list.d inside that you can find the balenaetcher.list delete that file and then run sudo apt update ,yeah you got it !!!!!

---

