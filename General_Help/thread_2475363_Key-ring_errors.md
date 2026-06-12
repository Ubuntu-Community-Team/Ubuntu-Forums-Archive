---
title: "Key-ring errors"
date: 2022-05-24
forum: General Help
---

### Post by makem2 on 2022-05-24
```

makem@makem2204:~$ sudo apt-get update
[sudo] password for makem: 
Hit:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease [109 kB]                                             
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                              
Get:4 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]                                          
Hit:5 https://brave-browser-apt-release.s3.brave.com stable InRelease                                                  
Get:6 http://dl.google.com/linux/earth/deb stable InRelease [1,807 B]                                                  
Hit:7 https://linux.teamviewer.com/deb stable InRelease                                                       
Ign:8 http://dl.google.com/linux/earth/deb stable/main amd64 Packages
Get:8 http://dl.google.com/linux/earth/deb stable/main amd64 Packages [726 B]
Fetched 320 kB in 2s (176 kB/s)   
Reading package lists... Done
W: http://dl.google.com/linux/earth/deb/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://linux.teamviewer.com/deb/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
makem@makem2204:~$

```

Can anyone assist in fixing those errors?

---

### Post by #&amp;thj^% on 2022-05-24
Did you look at: 
[https://manpages.ubuntu.com/manpages/jammy/en/man8/apt-key.8.html#deprecation](https://manpages.ubuntu.com/manpages/jammy/en/man8/apt-key.8.html#deprecation)
Those are warnings not errors
check with:
```
sudo apt-key list
```
find those 2 entries, you'll need to convert those 2  to a .gpg file, using the last 8 numeric characters from above...
Example:
```

sudo apt-key export <Key here> | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/<repo name>.gpg
```

---

### Post by makem2 on 2022-05-24
> **1fallen said:**
> Did you look at: 
[https://manpages.ubuntu.com/manpages/jammy/en/man8/apt-key.8.html#deprecation](https://manpages.ubuntu.com/manpages/jammy/en/man8/apt-key.8.html#deprecation)
Those are warnings not errors
check with:
```
sudo apt-key list
```
find those 2 entries, you'll need to convert those 2  to a .gpg file, using the last 8 numeric characters from above...
Example:
```

sudo apt-key export <Key here> | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/<repo name>.gpg
```

Yes, I read:

update (deprecated)
           Update the local keyring with the archive keyring and remove from the local keyring
           the archive keys which are no longer valid. The archive keyring is shipped in the
           archive-keyring package of your distribution, e.g. the ubuntu-keyring package in
           Ubuntu.

           Note that a distribution does not need to and in fact should not use this command any
           longer and instead ship keyring files in the [/etc/apt/trusted.gpg.d/]("file:///etc/apt/trusted.gpg.d/") directory
           directly as this avoids a dependency on gnupg and it is easier to manage keys by
           simply adding and removing files for maintainers and users alike

But, I could not follow it.I also don't understand your suggestion.** "**[COLOR=#000000]using the last 8 numeric characters from above..." and "[/COLOR]<Key here>" where do I get the key?

Do you mean take the last characters ie. 7FAC 5991?  But there are 2 entries for each, google and teamviewer

---

### Post by #&amp;thj^% on 2022-05-24
Your not following me either. ;)
check the key-list find those two that generate the warnings, first

---

### Post by makem2 on 2022-05-24
> **1fallen said:**
> Your not following me either. ;)
check the key-list find those two that generate the warnings, first

I have, is it ok to post them here?

There are two entries for each in /etc/apt/trusted.gpg

---

### Post by #&amp;thj^% on 2022-05-24
Sure I'll post mine first:
```
sudo apt-key list
[sudo] password for me: 
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
/etc/apt/trusted.gpg.d/microsoft.gpg
------------------------------------
pub   rsa2048 2015-10-28 [SC]
      BC52 8686 B50D 79E3 39D3  721C EB3E 94AD BE12 29CF
uid           [ unknown] Microsoft (Release signing) <gpgsecurity@microsoft.com>

/etc/apt/trusted.gpg.d/mozillateam-ubuntu-ppa.gpg
-------------------------------------------------
pub   rsa1024 2009-01-18 [SC]
      0AB2 1567 9C57 1D1C 8325  275B 9BDB 3D89 CE49 EC21
uid           [ unknown] Launchpad PPA for Mozilla Team

/etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg
------------------------------------------------------
pub   rsa4096 2012-05-11 [SC]
      8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid           [ unknown] Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

/etc/apt/trusted.gpg.d/ubuntu-keyring-2018-archive.gpg
------------------------------------------------------
pub   rsa4096 2018-09-17 [SC]
      F6EC B376 2474 EDA9 D21B  7022 8719 20D1 991B C93C
uid           [ unknown] Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>

```

---

### Post by makem2 on 2022-05-24
```

makem@makem2204:/$ sudo apt-key list
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
/etc/apt/trusted.gpg
--------------------
pub   rsa4096 2017-03-13 [SC]
      8CAE 012E BFAC 38B1 7A93  7CD8 C5E2 2450 0C12 89C0
uid           [ unknown] TeamViewer GmbH (TeamViewer Linux 2017) <support@teamviewer.com>
sub   rsa4096 2017-03-13 [E]


pub   rsa4096 2020-01-29 [SC]
      D2A5 FEB3 4881 60F0 28CC  1791 8DA8 4BE5 DEB4 9217
uid           [ unknown] TeamViewer Germany GmbH (TeamViewer Linux 2020) <support@teamviewer.com>


pub   dsa1024 2007-03-08 [SC]
      4CCA 1EAF 950C EE4A B839  76DC A040 830F 7FAC 5991
uid           [ unknown] Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   elg2048 2007-03-08 [E]


pub   rsa4096 2016-04-12 [SC]
      EB4C 1BFD 4F04 2F6D DDCC  EC91 7721 F63B D38B 4796
uid           [ unknown] Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
sub   rsa4096 2019-07-22 [S] [expires: 2022-07-21]
sub   rsa4096 2021-10-26 [S] [expires: 2024-10-25]


/etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg
------------------------------------------------------
pub   rsa4096 2012-05-11 [SC]
      8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid           [ unknown] Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>


/etc/apt/trusted.gpg.d/ubuntu-keyring-2018-archive.gpg
------------------------------------------------------
pub   rsa4096 2018-09-17 [SC]
      F6EC B376 2474 EDA9 D21B  7022 8719 20D1 991B C93C
uid           [ unknown] Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>


makem@makem2204:/$

```

---

### Post by #&amp;thj^% on 2022-05-24
So for you on teamviewer only:
```
sudo apt-key export 0C1289C0 | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/teamviewer.gpg
```
Repeat that for any other warnings that occur as well.
EDIT: I fixed a type O in the code
for google earth use:
```
sudo apt-key export 7FAC5991 | sudo gpg --dearmour -o /usr/share/keyrings/google.gpg

```

---

### Post by makem2 on 2022-05-24
> **1fallen said:**
> So for you on teamviewer only:
```
sudo apt-key export 0C12 89C0 | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/ teamviewer.gpg
```
Repeat that for any other warnings that occur as well.

I will do so but why just the last 8 numbers?

---

### Post by makem2 on 2022-05-24
```

makem@makem2204:/$ sudo apt-key export 0C12 89C0 | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/ teamviewer.gpg
[sudo] password for makem: 
gpg: can't open 'teamviewer.gpg': No such file or directory
gpg: dearmouring failed: No such file or directory
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
gpg: WARNING: nothing exported
makem@makem2204:/$


```

I missed the extra space before the file name :(

Should read: sudo apt-key export 0C12 89C0 | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/teamviewer.gpg

Entries now made in /etc/apt/trusted.gpg.d but warning still occur in apt-key list

```

makem@makem2204:~$ sudo apt-get update
[sudo] password for makem: 
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:2 http://dl.google.com/linux/earth/deb stable InRelease                                                            
Hit:3 http://gb.archive.ubuntu.com/ubuntu jammy InRelease                                                              
Hit:4 https://linux.teamviewer.com/deb stable InRelease                                              
Hit:5 https://brave-browser-apt-release.s3.brave.com stable InRelease          
Get:6 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease [109 kB]     
Get:7 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]
Get:8 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [11.4 kB]
Get:9 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [1,744 B]
Get:10 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [768 B]
Get:11 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [93.7 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [197 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [49.0 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [57.3 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [33.2 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [90.9 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [29.4 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [87.1 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [1,196 B]
Fetched 972 kB in 1s (751 kB/s)                                        
Reading package lists... Done
W: http://dl.google.com/linux/earth/deb/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://linux.teamviewer.com/deb/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
makem@makem2204:~$

```

---

### Post by #&amp;thj^% on 2022-05-24
yep I realized that and fixed the code in my above post.

---

### Post by #&amp;thj^% on 2022-05-24
For teamviewer, this worked for me:
```
sudo apt-key export 0C1289C0 | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/teamviewer.gpg
```
Google on other hand is still a problem with my commands, so give me some time to sort that one out. :(
Ok just heard back from google, for now just ignore the warning from google. :o
That's all was said.
[s]This is what should have** but don't work:**
```
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64 signed-by=/usr/share/keyrings/google.gpg] http://dl.google.com/>

```
I added that with: 
```
sudoedit /etc/apt/sources.list.d/google-earth-pro.list
```[/s]
**EDIT: I fixed it, sometimes I'm just stupid....**](*,)
```
cd /etc/apt
```
then run:
```
sudo cp trusted.gpg trusted.gpg.d
```
Now run your update command, should be clear of those Warnings.

---

### Post by #&amp;thj^% on 2022-05-24
**EDIT: I fixed it, sometimes I'm just stupid....**](*,)
```
cd /etc/apt
```
then run:
```
sudo cp trusted.gpg trusted.gpg.d
```
Now run your update command, should be clear of those Warnings.
This is one workaround, though it's not the best nor most "apt-preferred" solution it is a solution nonetheless. :P
```
sudo apt update
[B][U]Hit:1 https://linux.teamviewer.com/deb stable InRelease
Hit:2 http://dl.google.com/linux/earth/deb stable InRelease    [/U][/B]                
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Get:6 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]  
Ign:7 https://mkvtoolnix.download/ubuntu jammy InRelease                       
Hit:8 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease  
Hit:9 https://mkvtoolnix.download/ubuntu jammy Release                         
Fetched 210 kB in 1s (185 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```

---

### Post by makem2 on 2022-05-26
> **1fallen said:**
> **EDIT: I fixed it, sometimes I'm just stupid....**](*,)
```
cd /etc/apt
```
then run:
```
sudo cp trusted.gpg trusted.gpg.d
```
Now run your update command, should be clear of those Warnings.
This is one workaround, though it's not the best nor most "apt-preferred" solution it is a solution nonetheless. :P
```
sudo apt update
[B][U]Hit:1 https://linux.teamviewer.com/deb stable InRelease
Hit:2 http://dl.google.com/linux/earth/deb stable InRelease    [/U][/B]                
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Get:6 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]  
Ign:7 https://mkvtoolnix.download/ubuntu jammy InRelease                       
Hit:8 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease  
Hit:9 https://mkvtoolnix.download/ubuntu jammy Release                         
Fetched 210 kB in 1s (185 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```

```

makem@makem2204:~$ cd /etc/apt
makem@makem2204:/etc/apt$ ls -la
total 72
drwxr-xr-x   8 root root  4096 May 24 20:31 .
drwxr-xr-x 140 root root 12288 May 24 20:33 ..
drwxr-xr-x   2 root root  4096 Apr 30 21:07 apt.conf.d
drwxr-xr-x   2 root root  4096 Apr  8 11:22 auth.conf.d
drwxr-xr-x   2 root root  4096 Apr  8 11:22 keyrings
drwxr-xr-x   2 root root  4096 Apr  8 11:22 preferences.d
-rw-r--r--   1 root root  2841 Apr 30 20:09 sources.list
drwxr-xr-x   2 root root  4096 May 24 18:51 sources.list.d
-rw-r--r--   1 root root 12608 May 24 17:41 trusted.gpg
-rw-r--r--   1 root root  9338 May 13 16:12 trusted.gpg~
drwxr-xr-x   2 root root  4096 May 24 20:31 trusted.gpg.d
makem@makem2204:/etc/apt$ sudo cp trusted.gpg trusted.gpg.d
[sudo] password for makem: 
makem@makem2204:/etc/apt$ sudo apt-get update
Hit:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease [109 kB]                                             
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                              
Hit:4 http://dl.google.com/linux/earth/deb stable InRelease                                                            
Get:5 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]                                          
Hit:6 https://brave-browser-apt-release.s3.brave.com stable InRelease                                            
Hit:7 https://linux.teamviewer.com/deb stable InRelease                                                          
Get:8 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [213 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [101 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [54.9 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [57.4 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [3,692 B]
Get:13 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [37.2 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [98.8 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [87.8 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [1,196 B]
Get:17 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages [41.8 kB]
Get:18 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [126 kB]
Get:19 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [33.0 kB]
Get:20 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [11.4 kB]
Get:21 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [1,956 B]
Fetched 1,189 kB in 1s (1,757 kB/s)                                 
Reading package lists... Done
makem@make

```

Solved thank you.

---

