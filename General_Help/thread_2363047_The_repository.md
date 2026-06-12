---
title: "The repository"
date: 2017-06-05
forum: General Help
---

### Post by george110 on 2017-06-05
While regularly downloading updates I've receive a message saying that a failure in downloading repository information has occurred. The suggestion being that I ought check my internet connection which was functioning well.
Then when i click on " okay " the normal Ubuntu downloads proceed.
Could someone advise what I can do to solve this problem.
This situation occurs everytime I check for updates.

---

### Post by QIII on 2017-06-05
Hello!

Would you please attempt to update via the terminal and post back the entirety of the results?

Please place the results inside code tags to make your post easier to read.

The easiest way to do that would be to click the # sign above the text entry box, place your cursor between the code tags that appear and then paste the text.

---

### Post by george110 on 2017-06-06
Thank you for responding QIII. 

Just a little more help if you think it's worth pursuing this cause.

When you say update from inside the terminal what are the instructions that I ought follow.

For instance when I open the terminal & type " update " I get a " command not found " ressponse.

Asumming you may have an answer for that I may still find it difficult to understand let alone apply your instructions about the issue of the code requirement for posting.

Please don't worry if nothing comes of your effort to liason on this problem. The requirements for progress to a solution may be beyond my scope.

---

### Post by QIII on 2017-06-06
Hello!

If you are using a release from 16.04 or later, please issue

```
sudo apt update && sudo apt upgrade
```

For releases prior to 16.04, issue
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by george110 on 2017-06-07
QIII, here's the print out

```
Get:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]            
Get:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [252 kB] 
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [76.2 kB] 
Get:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [157 kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [552 kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [536 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources [30.9 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [284 kB]
Get:12 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [224 kB]
Get:13 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [298 kB]
Get:14 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [200 kB]
Get:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [477 kB]
Get:16 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [461 kB]
Get:17 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [188 kB]
Get:18 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [162 kB]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [270 kB]
Get:20 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [203 kB]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [121 kB]
Get:22 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:23 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:24 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [3,976 B]
Ign:25 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main Sources                 
Get:26 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [54.6 kB]
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [45.7 kB]
Get:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [131 kB]
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [117 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [67.5 kB]
Get:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [35.2 kB]
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [46.7 kB]
Hit:34 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Sources             
Ign:34 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Sources             
Hit:36 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages          
Ign:36 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages          
Ign:40 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 DEP-11 Metadata   
Ign:41 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons      
Hit:44 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en_AU 
Hit:45 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en    
Ign:46 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted amd64 DEP-11 Metadata
Ign:44 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en_AU 
Ign:45 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en    
Hit:47 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages      
Ign:47 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages      
Hit:48 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages       
Ign:48 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages       
Ign:51 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:52 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe DEP-11 64x64 Icons  
Ign:57 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 DEP-11 Metadata
Ign:58 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse DEP-11 64x64 Icons
Hit:33 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Sources           
Ign:33 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Sources           
Hit:35 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse Sources           
Ign:35 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse Sources           
Hit:37 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main i386 Packages           
Hit:38 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main Translation-en_AU       
Hit:39 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main Translation-en          
Ign:40 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 DEP-11 Metadata   
Ign:37 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main i386 Packages           
Ign:38 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main Translation-en_AU       
Ign:39 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main Translation-en          
Ign:41 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons      
Hit:42 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages    
Ign:42 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages    
Hit:43 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted i386 Packages     
Ign:43 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted i386 Packages     
Ign:46 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted amd64 DEP-11 Metadata
Hit:49 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Translation-en_AU   
Hit:50 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Translation-en      
Ign:49 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Translation-en_AU   
Ign:50 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Translation-en      
Ign:51 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe amd64 DEP-11 Metadata
Ign:52 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe DEP-11 64x64 Icons  
Hit:53 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages    
Ign:53 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages    
Hit:54 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse i386 Packages     
Ign:54 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse i386 Packages     
Hit:55 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en_AU 
Hit:56 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en    
Ign:55 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en_AU 
Ign:56 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en    
Ign:57 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 DEP-11 Metadata
Ign:58 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/multiverse DEP-11 64x64 Icons
Hit:25 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main Sources                 
Ign:25 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main Sources                 
Hit:34 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Sources             
Ign:34 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe Sources             
Hit:36 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages          
Ign:36 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages          
Err:40 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 DEP-11 Metadata   
  Could not open file /var/lib/apt/lists/partial/au.archive.ubuntu.com_ubuntu_dists_xenial_main_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 202.158.214.106 80]
Ign:41 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons      
Ign:46 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted amd64 DEP-11 Metadata
Hit:44 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en_AU 
Hit:45 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en    
Hit:47 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages      
Fetched 5,552 kB in 28s (196 kB/s)                                             
Reading package lists... Done
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages.xz](http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages.xz)  lzma_read: Read error (7)
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Translation-en_AU.xz](http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Translation-en_AU.xz)  lzma_read: Read error (7)
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Translation-en.xz](http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/i18n/Translation-en.xz)  lzma_read: Read error (7)
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/dep11/Components-amd64.yml](http://au.archive.ubuntu.com/ubuntu/dists/xenial/main/dep11/Components-amd64.yml)  Could not open file /var/lib/apt/lists/partial/au.archive.ubuntu.com_ubuntu_dists_xenial_main_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 202.158.214.106 80]
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-amd64/Packages.xz](http://au.archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-amd64/Packages.xz)  lzma_read: Read error (7)
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-i386/Packages.xz](http://au.archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-i386/Packages.xz)  lzma_read: Read error (7)
E: Some index files failed to download. They have been ignored, or old ones used instead.
george@george-pc:~$
```

---

### Post by LastDino on 2017-06-07
Have you tried running clean command? 

```
sudo apt clean
```

Then again run the update command as suggested before by Qlll

---

### Post by vasa1 on 2017-06-07
Also please post the output of ```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl
```

---

### Post by george110 on 2017-06-07
Here you are vasa 1. I hope it's helpful.

george@george-pc:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl
grep: /etc/apt/sources.list.d/*: No such file or directory
     1    /etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial main restricted
     2    /etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
     3    /etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial universe
     4    /etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial-updates universe
     5    /etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial multiverse
     6    /etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
     7    /etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
     8    /etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
     9    /etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    10    /etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
george@george-pc:~$

---

