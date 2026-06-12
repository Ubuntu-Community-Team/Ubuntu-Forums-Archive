---
title: "Where did my software go?"
date: 2017-11-23
forum: General Help
---

### Post by Lloydb39 on 2017-11-23
Problems multiplying. Now when I click on software, it comes up and says "no application data found." Shows no software, and none installed. Under updates it says "OS software" but clicking on it does nothing. It shows it is installing (whatever it is) but nothing ever happens. Can anyone give me a clue?

---

### Post by Autodave on 2017-11-23
Let's try this: in a terminal type:

sudo apt-get update

It will then ask for your password: enter it. Note: you will NOT see your password being entered: the line will remain blank: this is normal.

After that is done updating, run:

sudo apt-get upgrade

Let that run. You may be asked to reboot after done: reboot.  If you have not updated the system for quite awhile, I would repeat the sequence in the terminal again to make sure that there are no more updates available.  Now try your software center.

---

### Post by Lloydb39 on 2017-11-23
I don't know how to put copied material in one of those little boxes but this is what update returned:
```
lloyd@linux:~$ sudo apt-get update
[sudo] password for lloyd: 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Ign:5 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                    
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:7 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial InRelease           
Hit:8 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Ign:9 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease               
Hit:10 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                    
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]   
Hit:12 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                     
Hit:13 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release                
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Sources       
Err:15 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg
  The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Sources   
Err:17 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release.gpg                 
  The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
Ign:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages 
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en
Ign:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main DEP-11 64x64 Icons [29 B]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata [194 B]
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages
Ign:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Sources    
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,588 B]
Ign:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources      
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons
Ign:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Sources
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Sources
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Sources
Ign:36 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
Ign:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages
Ign:37 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en
Ign:38 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages
Get:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [60.2 kB]
Get:40 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [67.1 kB]
Ign:41 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons [2,717 B]
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:42 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Sources [3,506 B]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Sources [5,196 B]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages [5,174 B]
Ign:43 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages [5,166 B]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en [3,234 B]
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages [7,135 B]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages [7,127 B]
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en
Err:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages
  Hash Sum mismatch
Ign:44 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 DEP-11 Metadata
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:45 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons
Ign:46 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages
Ign:47 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en
Get:48 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51.3 kB]
Get:49 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Ign:50 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 Packages
Ign:51 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages
Ign:52 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Translation-en
Ign:53 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata
Get:54 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse DEP-11 64x64 Icons [29 B]
Ign:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources
Ign:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Sources    
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources
Ign:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Sources
Ign:36 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
Ign:37 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages
Ign:38 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en
Ign:41 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages
Ign:42 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages
Ign:43 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en
Ign:44 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 DEP-11 Metadata
Ign:45 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
Ign:46 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages
Ign:47 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en
Ign:50 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 Packages
Ign:51 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages
Ign:52 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Translation-en
Ign:53 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [124 kB] 
Get:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Sources [2,770 B]
Get:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources [53.1 kB]
Get:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Sources [1,076 B]
Get:36 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [504 kB]
Get:37 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [463 kB]
Get:38 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [245 kB]
Get:41 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages [12.9 kB]
Get:42 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages [13.0 kB]
Ign:43 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en
Err:44 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 DEP-11 Metadata
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 91.189.91.26 80]
Get:45 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [229 kB]
Get:46 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [196 kB]
Get:47 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [124 kB]
Get:50 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 Packages [3,479 B]
Get:51 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages [3,675 B]
Get:52 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Translation-en [1,279 B]
Hit:53 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata
Ign:43 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en
Fetched 2,193 kB in 10s (202 kB/s)                                             
Segmentation fault (core dumped)
Reading package lists... Done
N: Ignoring file 'google-' in directory '/etc/apt/sources.list.d/' as it has no filename extension
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release: The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg](http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg)  The following signatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
E: Failed to fetch store:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-amd64_Packages.gz  Hash Sum mismatch
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/dep11/Components-amd64.yml](http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/dep11/Components-amd64.yml)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 91.189.91.26 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code
lloyd@linux:~$
```

---

### Post by Lloydb39 on 2017-11-23
Ran upgrade anyway. Been running for 15 mins., executing hundreds of lines of code. Fingers crossed....

---

### Post by Lloydb39 on 2017-11-23
Upgraded, I guess, but apt-get update still funky. Software Center still not working but "Ubuntu Software Center" works, sort of.  Software Updater tried to install about 15 items but failed with "This requires installing packages from unauthenticated sources."

---

### Post by Bashing-om on 2017-11-23
Lloydb39; Hello -

Working from the old data I see 2 problems ... likely corrupted package manager control files - and bad singing key for google.
let's address the corrupted file 1st.
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update

```
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt-get update.

Post back the output of 'update' and we see what now there is to do - ( is the badsig resolved ?) .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Lloydb39 on 2017-11-23
OK.

```
lloyd@linux:~$ sudo rm -fr /var/lib/apt/lists
[sudo] password for lloyd: 
lloyd@linux:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory '/var/lib/apt/lists'
mkdir: created directory '/var/lib/apt/lists/partial'
lloyd@linux:~$ sudo apt update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]            
Ign:4 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease               
Get:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11.5 kB]           
Get:6 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial InRelease [17.5 kB] 
Get:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]           
Get:8 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease [4,487 B]                    
Get:9 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release [2,141 B]       
Get:10 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]        
Get:11 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release.gpg [916 B]    
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB] 
Get:13 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable/main amd64 Packages [1,930 B]         
Get:14 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner amd64 Packages [3,128 B]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [102 kB] 
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]   
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Sources [2,600 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources [46.0 kB]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Sources [1,140 B]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [396 kB]
Get:21 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main amd64 Packages [20.0 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main Sources [868 kB]        
Get:23 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,407 B]
Get:24 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner i386 Packages [3,120 B]
Get:25 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner Translation-en [1,616 B]
Get:26 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable/main amd64 Packages [778 B]
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [364 kB]
Get:28 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable/main i386 Packages [784 B]
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [174 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [60.2 kB]
Get:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [62.6 kB]
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages [7,472 B]
Get:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages [7,472 B]
Get:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en [2,412 B]
Get:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 DEP-11 Metadata [200 B]
Get:36 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main i386 Packages [20.0 kB]
Get:37 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [183 kB]
Get:38 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [157 kB]
Get:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [96.5 kB]
Get:40 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:41 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Get:42 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 Packages [3,212 B]
Get:43 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages [3,384 B]
Get:44 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Translation-en [1,336 B]
Get:45 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:46 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse DEP-11 64x64 Icons [29 B]
Get:47 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main Translation-en [5,796 B]
Get:48 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted Sources [4,808 B] 
Get:49 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe Sources [7,728 kB]
Get:50 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse Sources [179 kB]  
Get:51 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages [1,201 kB]
Get:52 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 Packages [1,196 kB]
Get:53 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main Translation-en [568 kB] 
Get:54 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 DEP-11 Metadata [733 kB]
Get:55 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons [409 kB]
Get:56 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages [8,344 B]
Get:57 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted i386 Packages [8,684 B]
Get:58 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en [2,908 B]
Get:59 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted amd64 DEP-11 Metadata [186 B]
Get:60 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages [7,532 kB]
Get:61 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages [7,512 kB]
Get:62 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe Translation-en [4,354 kB]                                                                                    
Get:63 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 DEP-11 Metadata [3,410 kB]                                                                             
Get:64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe DEP-11 64x64 Icons [7,448 kB]                                                                                
Get:65 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages [144 kB]                                                                                    
Get:66 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse i386 Packages [140 kB]                                                                                     
Get:67 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en [106 kB]                                                                                    
Get:68 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]                                                                            
Get:69 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                                                
Get:70 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Sources [3,428 B]                                                                                      
Get:71 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Sources [4,940 B]                                                                                  
Get:72 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages [4,860 B]                                                                               
Get:73 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages [4,856 B]                                                                                
Get:74 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en [3,220 B]                                                                               
Get:75 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]                                                                        
Get:76 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main DEP-11 64x64 Icons [29 B]                                                                              
Get:77 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata [194 B]                                                                    
Get:78 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages [6,600 B]                                                                           
Get:79 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages [6,584 B]                                                                            
Get:80 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en [3,760 B]                                                                           
Get:81 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,584 B]                                                                    
Get:82 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons [2,717 B]                                                                       
Get:83 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata [216 B]                                                                    
Get:84 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons [29 B]                                                                        
Get:85 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 Packages [16.2 kB]                                                                           
Get:86 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [15.3 kB]                                                                            
Get:87 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Translation-en [7,996 B]                                                                           
Get:88 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]                                                                    
Get:89 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]                                                                       
Get:90 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [668 kB]                                                                                  
Get:91 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [630 kB]                                                                                   
Get:92 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [279 kB]                                                                                  
Get:93 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [307 kB]                                                                           
Get:94 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [211 kB]                                                                              
Get:95 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 Packages [8,072 B]                                                                           
Get:96 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages [8,100 B]                                                                            
Get:97 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en [2,672 B]                                                                           
Get:98 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 DEP-11 Metadata [157 B]                                                                      
Get:99 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [554 kB]                                                                              
Get:100 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [527 kB]                                                                              
Get:101 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [226 kB]                                                                             
Get:102 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [185 kB]                                                                      
Get:103 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [252 kB]                                                                         
Fetched 50.3 MB in 17s (2,902 kB/s)                                                                                                                                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
15 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Ignoring file 'google-' in directory '/etc/apt/sources.list.d/' as it has no filename extension
lloyd@linux:~$ 

```
Also, it seemed like appstreamcli was a problem. When I started to remove it, it told me it would also have to remove "gnome-software" too, which didn't look like a good idea...

---

### Post by Lloydb39 on 2017-11-23
What is the difference between apt-get update and "apt update"?

---

### Post by Bashing-om on 2017-11-23
Lloydb39; Hey hey ...

So far so good :)

Now let's see:
```

sudo apt full-upgrade
sudo apt -f install

```

[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT]

---

### Post by wildmanne39 on 2017-11-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Lloydb39 on 2017-11-23
```
lloyd@linux:~$ sudo apt full-upgrade
[sudo] password for lloyd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  account-plugin-identica account-plugin-twitter fonts-roboto gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gstreamer1.0-plugins-base:i386 guile-2.0-libs
  libcdaudio1 libcdparanoia0:i386 libcec-platform1v5 libcec3 libcec4
  libcrossguid1 libfaac0 libfstrcmp0 libgc1c2 libgles1-mesa libglu1-mesa:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libhdhomerun2
  libjs-iscroll libllvm3.8 libllvm3.8:i386 libmicrohttpd10 libmircommon5
  libnfs8 libopus0:i386 liborc-0.4-0:i386 libp8-platform2 libpcrecpp0v5
  libplatform2 libqqwing2v5 libqt4-opengl:i386 libqtwebkit4:i386 libsdl2-2.0-0
  libshairplay0 libslv2-9 libsndio6.1 libsqlite3-0:i386 libssl1.0.0:i386
  libtheora0:i386 libtinyxml2.6.2v5 libvisual-0.4-0:i386
  libvisual-0.4-plugins:i386 libxml2:i386 libxslt1.1:i386 libxss1:i386
  libxv1:i386 linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic
  linux-headers-4.4.0-42 linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-headers-4.4.0-45
  linux-headers-4.4.0-45-generic linux-headers-4.4.0-47
  linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-65
  linux-headers-4.4.0-65-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-67
  linux-headers-4.4.0-67-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-42-generic linux-image-4.4.0-43-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-47-generic
  linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic
  linux-image-4.4.0-64-generic linux-image-4.4.0-65-generic
  linux-image-4.4.0-66-generic linux-image-4.4.0-67-generic
  linux-image-4.4.0-70-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-43-generic
  linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-47-generic
  linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-53-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-65-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-67-generic
  linux-image-extra-4.4.0-70-generic python-bluez snap-confine sni-qt:i386
  ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'google-' in directory '/etc/apt/sources.list.d/' as it has no filename extension
lloyd@linux:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-identica account-plugin-twitter fonts-roboto gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gstreamer1.0-plugins-base:i386 guile-2.0-libs
  libcdaudio1 libcdparanoia0:i386 libcec-platform1v5 libcec3 libcec4
  libcrossguid1 libfaac0 libfstrcmp0 libgc1c2 libgles1-mesa libglu1-mesa:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libhdhomerun2
  libjs-iscroll libllvm3.8 libllvm3.8:i386 libmicrohttpd10 libmircommon5
  libnfs8 libopus0:i386 liborc-0.4-0:i386 libp8-platform2 libpcrecpp0v5
  libplatform2 libqqwing2v5 libqt4-opengl:i386 libqtwebkit4:i386 libsdl2-2.0-0
  libshairplay0 libslv2-9 libsndio6.1 libsqlite3-0:i386 libssl1.0.0:i386
  libtheora0:i386 libtinyxml2.6.2v5 libvisual-0.4-0:i386
  libvisual-0.4-plugins:i386 libxml2:i386 libxslt1.1:i386 libxss1:i386
  libxv1:i386 linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic
  linux-headers-4.4.0-42 linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-headers-4.4.0-45
  linux-headers-4.4.0-45-generic linux-headers-4.4.0-47
  linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-65
  linux-headers-4.4.0-65-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-67
  linux-headers-4.4.0-67-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-42-generic linux-image-4.4.0-43-generic
  linux-image-4.4.0-45-generic linux-image-4.4.0-47-generic
  linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic
  linux-image-4.4.0-64-generic linux-image-4.4.0-65-generic
  linux-image-4.4.0-66-generic linux-image-4.4.0-67-generic
  linux-image-4.4.0-70-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-43-generic
  linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-47-generic
  linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-53-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-65-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-67-generic
  linux-image-extra-4.4.0-70-generic python-bluez snap-confine sni-qt:i386
  ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'google-' in directory '/etc/apt/sources.list.d/' as it has no filename extension
lloyd@linux:~$ 



```

That's what I got but I don't know what I have...

---

### Post by Lloydb39 on 2017-11-23
Oh, I also ran Software Updater, and it did something....

---

### Post by Bashing-om on 2017-11-23
Lloydb39' Look'n good :)

OK, next now is to get rid of all that crud:
```

sudo apt autoremove
dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

then we deal with google.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2017-11-23
Lesson #1: Read the summary at the bottom first:

```
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'google-' in directory '/etc/apt/sources.list.d/' as it has no filename extension
```

Line #1 is a suggestion. It's a good one. Do it: (sudo apt autoremove)
Line #2 is good news. Nothing is waiting for upgrade. Nothing is stuck. Apt is working.
Line #3 is a (N)otification (not a Warning or Error): You have a messed up source for Google (Chrome or Chromium?). You must still fix that.

---

### Post by Lloydb39 on 2017-11-23
Ian: I'm using Chrome. I tried to remove that bad file but it wouldn't let me. I think it was for Google Earth, which I have removed.

---

### Post by Lloydb39 on 2017-11-23
Done. I must have had a lot of crud. LOL. Now what?

---

### Post by ian-weisser on 2017-11-23
Now you tell us.
Is your system working better? Do the applications work? What is still a problem?

---

### Post by Lloydb39 on 2017-11-23
Everything seems to be working, better than ever. Bashing-om said something about dealing with google. Not sure what he meant. Anyway, thanks to you both. Awesome stuff.

---

### Post by Bashing-om on 2017-11-23
Lloydb39; Uh Huh -

Just nit-pick'n
> 
N: Ignoring file 'google-' in directory '/etc/apt/sources.list.d/' as it has no filename extension


If there is no need of the google app .. remove the source fetch .

-we can do that too-
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

---

### Post by Lloydb39 on 2017-11-24
OK. Ran that and got this and the file is still there....?

```
lloyd@linux:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google- <==
deb http://dl.google.com/linux/earth/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-earth.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/earth/deb/ stable main


==> /etc/apt/sources.list.d/google-earth.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/earth/deb/ stable main


==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main


==> /etc/apt/sources.list.d/google-talkplugin.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main


==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main


==> /etc/apt/sources.list.d/medibuntu.list <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/


==> /etc/apt/sources.list.d/medibuntu.list.distUpgrade <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/


==> /etc/apt/sources.list.d/medibuntu.list.save <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/


==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.distUpgrade <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main # disabled on upgrade to trusty
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/skype-stable.list <==
deb [arch=amd64] https://repo.skype.com/deb stable main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list.save <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
lloyd@linux:~
```$

---

### Post by ian-weisser on 2017-11-24
That command was not intended to remove anything.
Quick Learning Point: NEVER run a random command from some internet forum --including this one-- unless you know what it will do. 
An unwise magic incantation can cause you a whole lot more grief than one little busted source warning.

Rad the output again carefully. You will see that you still have a Google Earth source (source, not software) among your sources. Delete that source.

---

### Post by Lloydb39 on 2017-11-24
Would I use rm -f [COLOR=#000000][FONT=&quot]/etc/apt/sources.list.d/google- to do that?[/FONT][/COLOR]

---

### Post by ian-weisser on 2017-11-24
I gently suggest against reaching for '-f' as a first choice. On that path lies danger.

The files, full path and name, are listed clearly on your output.
You know they are in /etc, so you must use sudo to rm them.

```
sudo rm /etc/apt/sources.list.d/google-earth.list.distUpgrade
sudo rm /etc/apt/sources.list.d/google-earth.list.save
```

Wasn't that easy?

---

### Post by Lloydb39 on 2017-11-24
Very easy. Thanks for the help in cleaning up. I think I'm good to go.

---

