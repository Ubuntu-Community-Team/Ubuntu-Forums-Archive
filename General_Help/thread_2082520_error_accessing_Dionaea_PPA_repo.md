---
title: "error accessing Dionaea PPA repo"
date: 2012-11-09
forum: General Help
---

### Post by toosweetnitemare on 2012-11-09
**background:** I am installing the honeypot application Dionaea in a ubuntu VM. I am using [this Dionaea blog]("http://andrewmichaelsmith.com/2012/02/quick-install-of-dionaea-on-ubuntu/") as a installation guide. It is very simple and straight forward. However, I think i might have something misconfigured as pulling down a package from a PPA repo should be simple but currently isnt working for me.

**error: ** the error occurs during step 2: "sudo apt-get update".
 
Step 1 works fine: 

```
USERS@ubuntu:~$ sudo apt-add-repository ppa:honeynet/unstable
You are about to add the following PPA to your system:
 
 More info: https://launchpad.net/~honeynet/+archive/unstable
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpz7x091/secring.gpg' created
gpg: keyring `/tmp/tmpz7x091/pubring.gpg' created
gpg: requesting key A6131AE4 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpz7x091/trustdb.gpg: trustdb created
gpg: key A6131AE4: public key "Launchpad Stable Packages" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```

Step 2 shows this error:

```
Fetched 256 kB in 3s (69.9 kB/s)
W: Failed to fetch http://ppa.launchpad.net/honeynet/unstable/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/honeynet/unstable/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

``` 

**what i think happened: ** I think that the repo isnt working correctly but i have no real way to verify it that i can think of. I was able to go to repo via my browser and the files are there. What am i missing? Thank you in advanced for any help you can provide.

---

### Post by Erik1984 on 2012-11-09
If I browse to this page: [http://ppa.launchpad.net/honeynet/unstable/ubuntu/dists/](http://ppa.launchpad.net/honeynet/unstable/ubuntu/dists/) it seems like this PPA didn't get updated for any version past Lucid.

---

### Post by toosweetnitemare on 2012-11-09
@Euroman I will try installing it on 12.04 and comment back when i finish. THanks for the idea.

---

### Post by Erik1984 on 2012-11-09
> **toosweetnitemare said:**
> @Euroman I will try installing it on 12.04 and comment back when i finish. THanks for the idea.

Lucid is **10**.04, I suspect installing from this PPA won't work in 12.04 either. So if you really want to run this software I would search for either a recent PPA, a .deb file or the source to compile yourself.

---

### Post by toosweetnitemare on 2012-11-09
ubuntu 12.04 works, 12.10 does not. Not sure why, most likely just not supported for various reasons. Below is the full output of the install for anyones reference. Thanks for the help!

```
dionaea@ubuntu:~$ sudo add-apt-repository ppa:honeynet/nightly
[sudo] password for dionaea: 
You are about to add the following PPA to your system:
 
 More info: https://launchpad.net/~honeynet/+archive/nightly
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp99IXkI/secring.gpg' created
gpg: keyring `/tmp/tmp99IXkI/pubring.gpg' created
gpg: requesting key A6131AE4 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp99IXkI/trustdb.gpg: trustdb created
gpg: key A6131AE4: public key "Launchpad Stable Packages" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
dionaea@ubuntu:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://us.archive.ubuntu.com precise Release                               
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:4 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Get:5 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:6 http://us.archive.ubuntu.com precise-updates/main Sources [187 kB]
Get:7 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://extras.ubuntu.com precise Release                                   
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:9 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:10 http://us.archive.ubuntu.com precise-updates/universe Sources [61.1 kB] 
Get:11 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:12 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:13 http://us.archive.ubuntu.com precise-updates/main i386 Packages [432 kB]
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:14 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:15 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [152 kB]
Get:16 http://ppa.launchpad.net precise/main Sources [2,042 B]                 
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Get:18 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:19 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:20 http://us.archive.ubuntu.com precise-backports/universe Sources [17.3 kB]
Get:21 http://us.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:22 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:23 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:24 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [15.7 kB]
Get:25 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Get:26 http://ppa.launchpad.net precise/main i386 Packages [2,753 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Get:27 http://security.ubuntu.com precise-security/main Sources [54.1 kB]      
Get:28 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:29 http://security.ubuntu.com precise-security/universe Sources [15.8 kB]
Get:30 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:31 http://security.ubuntu.com precise-security/main i386 Packages [200 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:32 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:33 http://security.ubuntu.com precise-security/universe i386 Packages [54.4 kB]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:34 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Get:35 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:36 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:37 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:38 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:39 http://security.ubuntu.com precise-security/universe Translation-en [33.0 kB]
Fetched 1,435 kB in 1s (770 kB/s)     
Reading package lists... Done
dionaea@ubuntu:~$ sudo apt-get install dionaea
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libemu libev4 libgc1c2 liblcfg libnetfilter-queue1 libpython3.2 libudns0
  python3.2 python3.2-minimal
Suggested packages:
  python3.2-doc binfmt-support
The following NEW packages will be installed:
  dionaea libemu libev4 libgc1c2 liblcfg libnetfilter-queue1 libpython3.2
  libudns0 python3.2 python3.2-minimal
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,909 kB of archives.
After this operation, 21.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgc1c2 i386 1:7.1-8ubuntu0.12.04.1 [77.5 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/universe libnetfilter-queue1 i386 0.0.17-1 [8,564 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python3.2-minimal i386 3.2.3-0ubuntu3.2 [1,733 kB]
Get:4 http://ppa.launchpad.net/honeynet/nightly/ubuntu/ precise/main libemu i386 1:0.2.0+git20120122+564-0ubuntu1~precise [625 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python3.2 i386 3.2.3-0ubuntu3.2 [2,508 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libpython3.2 i386 3.2.3-0ubuntu3.2 [1,263 kB]
Get:7 http://ppa.launchpad.net/honeynet/nightly/ubuntu/ precise/main liblcfg i386 1:0.2.1+git20120405+23-0ubuntu1~precise [22.7 kB]
Get:8 http://ppa.launchpad.net/honeynet/nightly/ubuntu/ precise/main dionaea i386 0.1.0+git20111230+884-0ubuntu4~precise [606 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/universe libudns0 i386 0.0.9-3 [34.6 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise/universe libev4 i386 1:4.11-1 [29.5 kB]
Fetched 6,909 kB in 3s (1,819 kB/s)                         
Selecting previously unselected package libgc1c2.
(Reading database ... 168158 files and directories currently installed.)
Unpacking libgc1c2 (from .../libgc1c2_1%3a7.1-8ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libnetfilter-queue1.
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.17-1_i386.deb) ...
Selecting previously unselected package python3.2-minimal.
Unpacking python3.2-minimal (from .../python3.2-minimal_3.2.3-0ubuntu3.2_i386.deb) ...
Selecting previously unselected package python3.2.
Unpacking python3.2 (from .../python3.2_3.2.3-0ubuntu3.2_i386.deb) ...
Selecting previously unselected package libpython3.2.
Unpacking libpython3.2 (from .../libpython3.2_3.2.3-0ubuntu3.2_i386.deb) ...
Selecting previously unselected package libudns0.
Unpacking libudns0 (from .../libudns0_0.0.9-3_i386.deb) ...
Selecting previously unselected package libemu.
Unpacking libemu (from .../libemu_1%3a0.2.0+git20120122+564-0ubuntu1~precise_i386.deb) ...
Selecting previously unselected package libev4.
Unpacking libev4 (from .../libev4_1%3a4.11-1_i386.deb) ...
Selecting previously unselected package liblcfg.
Unpacking liblcfg (from .../liblcfg_1%3a0.2.1+git20120405+23-0ubuntu1~precise_i386.deb) ...
Selecting previously unselected package dionaea.
Unpacking dionaea (from .../dionaea_0.1.0+git20111230+884-0ubuntu4~precise_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up libgc1c2 (1:7.1-8ubuntu0.12.04.1) ...
Setting up libnetfilter-queue1 (0.0.17-1) ...
Setting up python3.2-minimal (3.2.3-0ubuntu3.2) ...
Setting up python3.2 (3.2.3-0ubuntu3.2) ...
Setting up libpython3.2 (3.2.3-0ubuntu3.2) ...
Setting up libudns0 (0.0.9-3) ...
Setting up libemu (1:0.2.0+git20120122+564-0ubuntu1~precise) ...
Setting up libev4 (1:4.11-1) ...
Setting up liblcfg (1:0.2.1+git20120405+23-0ubuntu1~precise) ...
Setting up dionaea (0.1.0+git20111230+884-0ubuntu4~precise) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dionaea@ubuntu:~$ sudo mkdir -p /var/dionaea/wwwroot
dionaea@ubuntu:~$ sudo mkdir -p /var/dionaea/binaries
dionaea@ubuntu:~$ sudo mkdir -p /var/dionaea/log
dionaea@ubuntu:~$ sudo chown -R nobody:nogroup /var/dionaea/
dionaea@ubuntu:~$ sudo mv /etc/dionaea/dionaea.conf.dist /etc/dionaea/dionaea.conf
dionaea@ubuntu:~$ sudo sed -i 's/var\/dionaea\///g' /etc/dionaea/dionaea.conf
dionaea@ubuntu:~$ sudo sed -i 's/log\//\/var\/dionaea\/log\//g' /etc/dionaea/dionaea.conf
dionaea@ubuntu:~$ sudo dionaea -c /etc/dionaea/dionaea.conf -w /var/dionaea -u nobody -g nogroup -D

Dionaea Version 0.1.0 
Compiled on Linux/x86 at Jul 19 2012 12:06:27 with gcc 4.6.3 
Started on ubuntu running Linux/i686 release 3.2.0-32-generic-pae

[09112012 13:55:17] dionaea dionaea.c:245: User nobody has uid 65534

[09112012 13:55:17] dionaea dionaea.c:264: Group nogroup has gid 65534

dionaea@ubuntu:~$ 

```

---

### Post by Erik1984 on 2012-11-09
Glad that you have it working. I didn't see there was a Nightly 'branch'. Yes, that one has support for 12.04 (but not for 12.10 (yet)).

---

