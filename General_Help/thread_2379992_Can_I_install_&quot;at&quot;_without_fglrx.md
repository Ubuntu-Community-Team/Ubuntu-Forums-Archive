---
title: "Can I install &quot;at&quot; without fglrx?"
date: 2017-12-12
forum: General Help
---

### Post by tonightilive on 2017-12-12
When trying to install "at" 
```
sudo apt-get install at
```
 I get : 
```
The following packages have unmet dependencies: fglrx : Depends: fglrx-core but it is not installable
         Recommends: fglrx-amdcccle but it is not installable



```

Is there a way around this? I'd really love this command.

---

### Post by vasa1 on 2017-12-12
Please first post the output of```
sudo apt-get update
```and```
sudo apt-get dist-upgrade
```

You can abort the second command if you aren't comfortable with what you see.

---

### Post by QIII on 2017-12-12
Hello!

Which release of Ubuntu are you running?

---

### Post by tonightilive on 2017-12-12
```
sudo apt-get update[sudo] password for seth: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                                                          
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                                                                                          
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                   
Hit:5 http://ppa.launchpad.net/firmware-testing-team/ppa-fwts-stable/ubuntu xenial InRelease            
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                              
Hit:7 http://ppa.launchpad.net/rebuntu16/other-stuff/ubuntu xenial InRelease                                                                   
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                                       
Hit:10 http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial InRelease                                                                       
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [678 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [637 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]               
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [213 kB]                      
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [564 kB]                 
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [529 kB]               
Get:17 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62.5 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [185 kB]    
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [269 kB]           
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [16.2 kB]       
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [15.3 kB]      
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]          
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,676 B]      
Get:25 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [57.6 kB]                
Get:26 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:27 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Fetched 3,991 kB in 3s (1,291 kB/s)                                  
Reading package lists... Done

```

```
sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not installable
         Recommends: fglrx-amdcccle but it is not installable
E: Unmet dependencies. Try using -f.

```

```
lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

---

### Post by deadflowr on 2017-12-12
You need to purge all things fglrx.
As it will not run or work on 16.04.
Was this an upgrade from 14.04?

---

### Post by tonightilive on 2017-12-12
No, it was a clean minimal install.

---

### Post by QIII on 2017-12-12
Hello!

Do you know if development of that package is on-going?

If fglrx is required, that package will not be supported from 16.04 forward because AMD has ceased development of fglrx and it does not support any supported version of Ubuntu beyond 14.04.

---

### Post by tonightilive on 2017-12-12
Hi everyone,

thanks for the help. I checked my install history and it looks like I installed fglrx the other night trying to get xbacklight to work. Uninstalled fglrx and I can now install "at".

---

