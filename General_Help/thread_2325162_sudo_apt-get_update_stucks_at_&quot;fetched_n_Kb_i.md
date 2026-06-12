---
title: "sudo apt-get update stucks at &quot;fetched n Kb in ms&quot;"
date: 2016-05-19
forum: General Help
---

### Post by Nahua_Kang on 2016-05-19
Today I have been trying to install vim and vim-go for using Golang and have made a few mistakes along the way. 
When I tried to do ```
sudo apt-get update
``` it seems that the terminal is always stuck at the "fetched n Kb in ms" and does not finish (see below the picture in attachment). 
So if I do ```
sudo apt-get update && apt-get upgrade
```, I cannot even get to upgrade as it's stuck at fetched how many Kb in how many seconds.

May I ask if anyone has any idea why this is happening? Many thanks ahead of time!

**UPDATE:** [https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712/comments/24](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712/comments/24) this post solves my issue.

---

### Post by Bashing-om on 2016-05-19
Nahua_Kang; Hello;

Maybe take a look at what the package manager is attempting to connect to for the updates.
Post back - between code tags - the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
We make sure it is not a bad URL that is at play here .

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by Nahua_Kang on 2016-05-19
Hi Bashing-om, thanks for your response!
For sources.list:
```
~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     6	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team, and may not be under a free licence. Please satisfy yourself as to
    15	## your rights to use the software. Also, please note that software in
    16	## universe WILL NOT receive any review or updates from the Ubuntu security
    17	## team.
    18	deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
    19	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
    20	deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    21	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    22	
    23	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24	## team, and may not be under a free licence. Please satisfy yourself as to 
    25	## your rights to use the software. Also, please note that software in 
    26	## multiverse WILL NOT receive any review or updates from the Ubuntu
    27	## security team.
    28	deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    29	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    30	deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    31	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    32	
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    39	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	# deb http://archive.canonical.com/ubuntu xenial partner
    46	# deb-src http://archive.canonical.com/ubuntu xenial partner
    47	
    48	deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    49	# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    50	deb http://security.ubuntu.com/ubuntu xenial-security universe
    51	# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    52	deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    53	# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    54	deb http://download.virtualbox.org/virtualbox/debian xenial contrib

```

for the second command:
```

tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/system76-dev-ubuntu-stable-xenial.list <==
deb http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial main
# deb-src http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial main


==> /etc/apt/sources.list.d/system76-dev-ubuntu-stable-xenial.list.save <==
deb http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial main
# deb-src http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial main


==> /etc/apt/sources.list.d/teejee2008-ubuntu-ppa-xenial.list <==
deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial main


==> /etc/apt/sources.list.d/virtualbox.list <==
deb http://download.virtualbox.org/virtualbox/debian xenial contrib non-free


==> /etc/apt/sources.list.d/virtualbox.list.save <==
deb http://download.virtualbox.org/virtualbox/debian xenial contrib non-free

```

Please let me know if you have any idea why my update cannot proceed further from fetched... Thanks again!

---

### Post by kev16 on 2016-05-19
I have the same problem here. The only external repositories I added are Docker and Chrome.

---

### Post by Bashing-om on 2016-05-19
Nahua_Kang; Well......

I see no fault with the sources !

What results:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com
ping -c3 us.archive.ubuntu.com

``` see if we have a connectivity issue.

[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT]

---

### Post by Nahua_Kang on 2016-05-19
Here are the results. Seems to me that there is no connectivity issue? I am not sure why it won't finish the update, and I wonder if it has to do with me deleting two files right before I found out about this issue, not that they should in anyway (files were ~/.linuxbrew and ~/.rstudio-desktop)?

```

~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=21.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=22.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=21.5 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 21.566/21.803/22.185/0.272 ms

```
```

ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=53 time=56.7 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=53 time=57.0 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=53 time=56.8 ms


--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 56.733/56.886/57.090/0.150 ms

```

```

ping -c3 us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.91.26) 56(84) bytes of data.
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=1 ttl=52 time=139 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=2 ttl=52 time=154 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=3 ttl=52 time=176 ms


--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 139.375/156.867/176.811/15.384 ms

```

```

sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://download.virtualbox.org/virtualbox/debian xenial InRelease [7,882 B]
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:4 http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial InRelease     
Hit:5 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:6 http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial InRelease          
Ign:2 http://download.virtualbox.org/virtualbox/debian xenial InRelease        
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:9 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:10 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Fetched 7,882 B in 0s (9,195 B/s)

```
And it just stuck at this point......

---

### Post by Bashing-om on 2016-05-19
Nahua_Kang; Huh ...

No fault with connectivity .

Back to square one.

Show the command and the complete output of:
```

sudo apt update

```
see if the package manger gives any hints on what the problem is .

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Nahua_Kang on 2016-05-19
Hey thanks for the quick reply!
```

 sudo apt update
Get:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease [7,882 B]
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial InRelease     
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Err:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease        
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
Hit:5 http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial InRelease          
Hit:7 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial InRelease               
Hit:9 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:10 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Reading package lists... Done 
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: GPG error: http://download.virtualbox.org/virtualbox/debian xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
E: The repository 'http://download.virtualbox.org/virtualbox/debian xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1

```

---

### Post by Bashing-om on 2016-05-19
Nahua_Kang; Uh Huh ...

Now we are getting somewhere.

The package manager's advise is correct:
> 
configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/virtualbox.list:1

the proper place for the 3rd party sources is in the /etc/apt/sources.list.d/ directory, so;
backup the present /etc/apt/sources.list file prior to making the edit.
In your favorite text editor remove line 54 and save the file.


Next is virtualbox;
As it is 'trusted' obtain the signing key:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2F683C52980AECF

```

Next, Google has re-configured their server, but their security is not up to what xenial requires . It is just an advisory however that the security is weak and in this instance can be ignored. We await Google to upgrade their security.


Once these are done .... 
What now
```

sudo apt update
sudo apt full-upgrade

```


[INDENT][INDENT][INDENT]I see said the blind man
[/INDENT][/INDENT][/INDENT]

---

### Post by The Cog on 2016-05-19
Hmm. I just started this thread: [http://ubuntuforums.org/showthread.php?t=2325168](http://ubuntuforums.org/showthread.php?t=2325168)
I wonder if they're related. If so, mods please feel free to merge.

---

### Post by Nahua_Kang on 2016-05-19
Thanks for the advice!
Removed sources.list line 54 from gedit and obtained the key with:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2F683C52980AECF
Executing: /tmp/tmp.wdPwZy35y8/gpg.1.sh --keyserver
keyserver.ubuntu.com
--recv-keys
A2F683C52980AECF
gpg: requesting key 2980AECF from hkp server keyserver.ubuntu.com
gpg: key 2980AECF: public key "Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```
Now, as I try to do:
```

sudo apt update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://download.virtualbox.org/virtualbox/debian xenial InRelease [7,882 B]
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                     
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:5 http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial InRelease     
Hit:6 http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial InRelease          
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [94.5 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [92.2 kB]
Fetched 289 kB in 1s (169 kB/s)  

```
It is again stuck at this stage...

With advice from The Cog, in another Terminal I did: 
```

**sudo pkill appstreamcli**

```
Then the original terminal with update shows: Terminated
```

 sudo apt update
Hit:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial InRelease     
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:5 http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial InRelease          
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [94.5 kB]   
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [92.2 kB]
Fetched 281 kB in 2s (136 kB/s)      
Terminated
Reading package lists... Done
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code

```

---

### Post by Brandon_MacEachern on 2016-05-19
On a fresh install I am also running into this issue, it's haulted production here as we can't do anything with new computers now, no updates will run on an entire rack, let along .deb that require dependencies.

---

### Post by Nahua_Kang on 2016-05-19
Hi The Cog, thanks for your advice. In your thread, do you mean that the server is down for all of us and we can't update or install at the moment? Cheers!

---

### Post by Nahua_Kang on 2016-05-19
Brandon, so like The Cog, you think this is probably not my own issue but a universal issue for users who try to update and install at the moment? :) That sounds better for me but quite a bad news for all of us.

---

### Post by Brandon_MacEachern on 2016-05-19
I think there's something wrong on the server.  It seems to be something wrong with the metadata, because as The Cog found, appstreamcli maxes out.  And that is indeed happening as soon as apt-get update is run.  From what I see appstreamcli deals with metadata.

When I switch servers, it locks up at: Get:75 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [201 B]  

So I really think it's a corrupt metadata on the server.

Too bad we will have to likely wait now.  I've been cursing out this entire rack of machines, thinking we had defective computers, but it's really the server.

---

### Post by Nahua_Kang on 2016-05-19
Thanks for the input! So I have been agonizing and wasting time the whole evening...... 

But luckily I still learned something from Bashing-om on how to get a signing key.

---

### Post by Brandon_MacEachern on 2016-05-19
Oh, I'm there with you.  I have already started drinking on the job because of this.  I have a quota, now have to explain to the boss that because of a Ubuntu issue, we are stuck.

Oh, and explain the Scotch.  lol

---

### Post by sgage on 2016-05-19
Yes, something is wrong with backports, and if you disable it, all is well.

---

### Post by Bashing-om on 2016-05-19
et al ; Yuk

Be aware, bug report:
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845)
one work-a-round :
 optional appstreamcli gives issues, removal works for now

[INDENT][INDENT]great minds at work
[/INDENT][/INDENT]

---

### Post by Nahua_Kang on 2016-05-20
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712/comments/24](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712/comments/24)   This solves the issue for me. Thank all of you very much!

---

