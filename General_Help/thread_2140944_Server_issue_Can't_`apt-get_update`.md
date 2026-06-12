---
title: "Server issue: Can't `apt-get update`"
date: 2013-05-01
forum: General Help
---

### Post by ak5 on 2013-05-01
I have the same issue as the person here: [http://askubuntu.com/questions/259114/reading-package-lists-in-update-apt-get-ubuntu-12-04-vps](http://askubuntu.com/questions/259114/reading-package-lists-in-update-apt-get-ubuntu-12-04-vps)

In a nutshell,

```
$ sudo apt-get update
```

produces this output:

```
$ sudo apt-get update
Get:1 http://us-east-1.ec2.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://us-east-1.ec2.archive.ubuntu.com precise-updates Release.gpg [198 B]  
Get:3 http://us-east-1.ec2.archive.ubuntu.com precise Release [49.6 kB]             
Get:4 http://us-east-1.ec2.archive.ubuntu.com precise-updates Release [49.6 kB]                        
Get:5 http://us-east-1.ec2.archive.ubuntu.com precise/main Sources [934 kB]                                    
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:7 http://us-east-1.ec2.archive.ubuntu.com precise/universe Sources [5,019 kB]
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:9 http://us-east-1.ec2.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]    
Get:10 http://security.ubuntu.com precise-security/main Sources [69.9 kB]
Get:11 http://us-east-1.ec2.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]  
Get:12 http://security.ubuntu.com precise-security/universe Sources [24.0 kB]    
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [248 kB]  
Get:14 http://us-east-1.ec2.archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:15 http://security.ubuntu.com precise-security/universe amd64 Packages [71.4 kB]
Get:16 http://us-east-1.ec2.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [259 kB]   
Get:18 http://security.ubuntu.com precise-security/universe i386 Packages [73.4 kB]        
Get:19 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]               
Get:20 http://us-east-1.ec2.archive.ubuntu.com precise/main TranslationIndex [3,706 B]
Get:21 http://us-east-1.ec2.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:22 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]       
Get:23 http://us-east-1.ec2.archive.ubuntu.com precise-updates/main Sources [379 kB]
Get:24 http://security.ubuntu.com precise-security/main Translation-en [120 kB]
Get:25 http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe Sources [85.8 kB]     
Get:26 http://us-east-1.ec2.archive.ubuntu.com precise-updates/main amd64 Packages [601 kB]
Get:27 http://security.ubuntu.com precise-security/universe Translation-en [45.0 kB]
Get:28 http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe amd64 Packages [196 kB]   
Get:29 http://us-east-1.ec2.archive.ubuntu.com precise-updates/main i386 Packages [613 kB]
Get:30 http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe i386 Packages [199 kB]
Get:31 http://us-east-1.ec2.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:32 http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:33 http://us-east-1.ec2.archive.ubuntu.com precise/main Translation-en [726 kB]
Get:34 http://us-east-1.ec2.archive.ubuntu.com precise/universe Translation-en [3,341 kB]
Get:35 http://us-east-1.ec2.archive.ubuntu.com precise-updates/main Translation-en [269 kB]
Get:36 http://us-east-1.ec2.archive.ubuntu.com precise-updates/universe Translation-en [116 kB]
Fetched 25.7 MB in 1min 41s (254 kB/s)                                                                                                                                   
Reading package lists... Error!
```

I have tried:

```
$ sudo rm -rf /var/lib/apt/lists/*
```

EDIT:

```
$ sudo apt-get install -f && sudo rm -rf /var/lib/apt/lists/* && sudo apt-get update
```

but that does not help (same error).

Any insights would be appreciated, the IRC channels were stumped, too.

---

### Post by plucky on 2013-05-01
What do you get if you ```
sudo apt-get update
ls -l /var/lib/apt/lists/
```?

Are there any files?

What are the permissions on the files?

Can you open one file using "cat" command?

What are the permissions on the "lists" directory?

```
cd /var/lib/apt/
ls -l
```

---

### Post by ak5 on 2013-05-01
Thank you for making me look into this folder again!

I seem to have fixed it.

First, here is the information you asked for:

```
$ ls -l /var/lib/apt/lists/
total 129744
-rw-r----- 1 root root        0 May  1 10:03 lock
drwxr-xr-x 2 root root     4096 May  1 10:25 partial
-rw-r--r-- 1 root root  1656937 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages
-rw-r--r-- 1 root root  1750577 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
-rw-r--r-- 1 root root       74 Apr 29 21:08 security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index
-rw-r--r-- 1 root root  1067978 Apr 26 13:37 security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en
-rw-r--r-- 1 root root   340042 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources
-rw-r--r-- 1 root root    49575 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_Release
-rw-r--r-- 1 root root      198 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg
-rw-r--r-- 1 root root   392735 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages
-rw-r--r-- 1 root root   409301 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root       73 Apr 29 21:08 security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index
-rw-r--r-- 1 root root   232109 Apr  8 21:52 security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en
-rw-r--r-- 1 root root    93766 May  1 10:10 security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources
-rw-r--r-- 1 root root  7818931 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
-rw-r--r-- 1 root root  7816415 May  1 05:15 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
-rw-r--r-- 1 root root     3706 May  1 05:15 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index
-rw-r--r-- 1 root root  3861559 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
-rw-r--r-- 1 root root  4356187 May  1 05:15 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources
-rw-r--r-- 1 root root    49563 May 21  2012 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root      198 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg
-rw-r--r-- 1 root root 25546870 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
-rw-r--r-- 1 root root 25568759 May  1 05:15 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
-rw-r--r-- 1 root root     2922 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index
-rw-r--r-- 1 root root 15034875 May  1 04:52 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
-rw-r--r-- 1 root root 21256524 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources
-rw-r--r-- 1 root root  4090573 May  1 05:14 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages
-rw-r--r-- 1 root root  4186947 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
-rw-r--r-- 1 root root     3564 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index
-rw-r--r-- 1 root root  2084926 May  1 05:14 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en
-rw-r--r-- 1 root root  1967690 May  1 05:14 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources
-rw-r--r-- 1 root root    49573 Apr 30 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_Release
-rw-r--r-- 1 root root      198 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg
-rw-r--r-- 1 root root  1059778 May  1 04:52 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages
-rw-r--r-- 1 root root  1075497 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages
-rw-r--r-- 1 root root     2850 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index
-rw-r--r-- 1 root root   583349 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en
-rw-r--r-- 1 root root   356987 May  1 08:56 us-east-1.ec2.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources
```

The important part here is: 

```
-rw-r----- 1 root root        0 May  1 10:03 lock
```

I just removed this file, ran ```
$ sudo apt-get install -f
``` and it works again!

---

