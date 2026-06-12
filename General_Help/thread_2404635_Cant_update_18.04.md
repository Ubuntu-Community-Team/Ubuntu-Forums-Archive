---
title: "Cant update 18.04"
date: 2018-10-26
forum: General Help
---

### Post by linuxyogi on 2018-10-26
I am geting this 

```
$ sudo apt update 
[sudo] password for lubuntu: 
Sorry, try again.
[sudo] password for lubuntu: 
Hit:1 http://es-mirrors.evowise.com/ubuntu bionic InRelease
Get:2 http://es-mirrors.evowise.com/ubuntu bionic-updates InRelease [88.7 kB]
Hit:3 http://es-mirrors.evowise.com/ubuntu bionic-backports InRelease
Hit:4 http://es-mirrors.evowise.com/ubuntu bionic-security InRelease
Get:5 http://es-mirrors.evowise.com/ubuntu bionic-updates/main amd64 Packages [413 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Get:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages [369 kB]
Err:6 http://es-mirrors.evowise.com/ubuntu bionic-updates/main i386 Packages   
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:369476 [weak]
   - SHA256:29df98463d2edcc618c90fded0a45e75db0b32af21baed0434aa400bbb0313d1
   - SHA1:70115a593576aff4c4e9ed706a345d24e95b0171 [weak]
   - MD5Sum:7608c44be487846a98485fd4aa446cac [weak]
  Hashes of received file:
   - SHA256:47f24555b56865ef336f154352148600193223e06ed566e60dee83f0d9915f1a
   - SHA1:a523a8ea5414019cdee2b64cf73425e502233c4d [weak]
   - MD5Sum:a8fdce5fc53ebef81fae0f7482716ee2 [weak]
   - Filesize:369476 [weak]
  Last modification reported: Thu, 25 Oct 2018 06:55:05 +0000
  Release file created at: Thu, 25 Oct 2018 06:54:52 +0000
Get:16 http://es-mirrors.evowise.com/ubuntu bionic-updates/universe amd64 Packages [567 kB]
Err:16 http://es-mirrors.evowise.com/ubuntu bionic-updates/universe amd64 Packages
  
Get:17 http://es-mirrors.evowise.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [191 kB]
Get:18 http://es-mirrors.evowise.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [185 kB]
Get:19 http://es-mirrors.evowise.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [307 kB]
Get:20 http://es-mirrors.evowise.com/ubuntu bionic-updates/multiverse amd64 Packages [5,708 B]
Get:21 http://es-mirrors.evowise.com/ubuntu bionic-updates/multiverse i386 Packages [5,864 B]
Get:22 http://es-mirrors.evowise.com/ubuntu bionic-updates/multiverse Translation-en [3,176 B]
Get:23 http://es-mirrors.evowise.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:24 http://es-mirrors.evowise.com/ubuntu bionic-updates/multiverse DEP-11 48x48 Icons [29 B]
Get:25 http://es-mirrors.evowise.com/ubuntu bionic-updates/multiverse DEP-11 64x64 Icons [2,638 B]
Fetched 1,728 kB in 5s (355 kB/s)       
Reading package lists... Done
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/bionic-updates/main/binary-i386/by-hash/SHA256/29df98463d2edcc618c90fded0a45e75db0b32af21baed0434aa400bbb0313d1  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:369476 [weak]
    - SHA256:29df98463d2edcc618c90fded0a45e75db0b32af21baed0434aa400bbb0313d1
    - SHA1:70115a593576aff4c4e9ed706a345d24e95b0171 [weak]
    - MD5Sum:7608c44be487846a98485fd4aa446cac [weak]
   Hashes of received file:
    - SHA256:47f24555b56865ef336f154352148600193223e06ed566e60dee83f0d9915f1a
    - SHA1:a523a8ea5414019cdee2b64cf73425e502233c4d [weak]
    - MD5Sum:a8fdce5fc53ebef81fae0f7482716ee2 [weak]
    - Filesize:369476 [weak]
   Last modification reported: Thu, 25 Oct 2018 06:55:05 +0000
   Release file created at: Thu, 25 Oct 2018 06:54:52 +0000
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/bionic-updates/universe/binary-amd64/by-hash/SHA256/02f175a9a5f9f6ba132891cfa0d917e4da71b14709f35684c376263bf713952d  
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

How to solve the issue ?

---

### Post by oldrocker99 on 2018-10-26
You are running a 64-bit installation, right? Try using a different repository. The "Software and Updates" first tab, Ubuntu software, has a "select best server" option.

---

### Post by linuxyogi on 2018-10-26
> **oldrocker99 said:**
> You are running a 64-bit installation, right? Try using a different repository. The "Software and Updates" first tab, Ubuntu software, has a "select best server" option.

Actually I did "select best server" and that's how I configured the above mirror.

---

### Post by linuxyogi on 2018-10-26
Changed the repo back in India and somehow the issue is solved.

---

### Post by oldrocker99 on 2018-10-26
Yes, I have had problems with servers, but there are a whole lot of them. Glad you solved it. It's a good idea, as the OP of this thread, to add [SOLVED] at the beginning of the title.

---

### Post by linuxyogi on 2018-10-27
```
$ sudo apt update 
[sudo] password for lubuntu: 
Sorry, try again.
[sudo] password for lubuntu: 
Hit:1 http://archive.ubuntu.com/ubuntu bionic InRelease
Hit:3 http://archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu bionic-security InRelease
Get:2 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:5 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [414 kB]
Err:5 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:414024 [weak]
   - SHA256:8ab5c85de242a15825d31c549191f45c69ab85eb967566e525c50844fda76054
   - SHA1:2b93529a6abb36fdfd481213400359e9960881e4 [weak]
   - MD5Sum:1f1f82ad60f242e4837029e6eb5b9e4a [weak]
  Hashes of received file:
   - SHA256:59d2516974f27da755716bcde4b4665865179296bd669ff436bea820348da9f2
   - SHA1:239a0e88603f9fd4146a204320a674aa11185e34 [weak]
   - MD5Sum:8a31d5011dd0cbd68f5ab99cf5073ad4 [weak]
   - Filesize:414024 [weak]
  Last modification reported: Sat, 27 Oct 2018 12:54:36 +0000
  Release file created at: Sat, 27 Oct 2018 12:54:23 +0000
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Err:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
  
Fetched 874 kB in 4s (230 kB/s)   
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-amd64/by-hash/SHA256/8ab5c85de242a15825d31c549191f45c69ab85eb967566e525c50844fda76054  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:414024 [weak]
    - SHA256:8ab5c85de242a15825d31c549191f45c69ab85eb967566e525c50844fda76054
    - SHA1:2b93529a6abb36fdfd481213400359e9960881e4 [weak]
    - MD5Sum:1f1f82ad60f242e4837029e6eb5b9e4a [weak]
   Hashes of received file:
    - SHA256:59d2516974f27da755716bcde4b4665865179296bd669ff436bea820348da9f2
    - SHA1:239a0e88603f9fd4146a204320a674aa11185e34 [weak]
    - MD5Sum:8a31d5011dd0cbd68f5ab99cf5073ad4 [weak]
    - Filesize:414024 [weak]
   Last modification reported: Sat, 27 Oct 2018 12:54:36 +0000
   Release file created at: Sat, 27 Oct 2018 12:54:23 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-i386/by-hash/SHA256/2b1a29c345b3a762f1b1a1c25baf693ecd732d809ac05fa5b5e721dcab53c5e2  
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Same problem again. So I have temporarily switched to the main server but the problem remains.

---

### Post by linuxyogi on 2018-10-27
Same with Hong Kong mirror.

```
$ sudo apt update 
[sudo] password for lubuntu: 
Get:1 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic InRelease [242 kB]
Get:2 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates InRelease [88.7 kB]
Get:3 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports InRelease [74.6 kB]
Get:4 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security InRelease [83.2 kB]
Get:5 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main i386 Packages [1,007 kB]
Get:6 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main amd64 Packages [1,019 kB]
Get:7 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main Translation-en [516 kB]
Get:8 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]
Get:9 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main DEP-11 48x48 Icons [118 kB]
Get:10 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main DEP-11 64x64 Icons [245 kB]
Get:11 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/restricted i386 Packages [9,156 B]
Get:12 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/restricted amd64 Packages [9,184 B]
Get:13 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/restricted Translation-en [3,584 B]
Get:14 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe amd64 Packages [8,570 kB]
Get:15 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe i386 Packages [8,531 kB]
Get:16 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe Translation-en [4,941 kB]
Get:17 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe amd64 DEP-11 Metadata [3,287 kB]
Get:18 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe DEP-11 48x48 Icons [2,151 kB]
Get:19 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe DEP-11 64x64 Icons [8,420 kB]
Get:20 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse amd64 Packages [151 kB]
Get:21 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse i386 Packages [144 kB]
Get:22 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse Translation-en [108 kB]
Get:23 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse amd64 DEP-11 Metadata [49.7 kB]
Get:24 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse DEP-11 48x48 Icons [8,931 B]
Get:25 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse DEP-11 64x64 Icons [225 kB]
Get:26 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main amd64 Packages [414 kB]
Err:26 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main amd64 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:414036 [weak]
   - SHA256:bddd09e41e7b9afa0ba2b73d41a796b46534f3446935777218ac582dde695409
   - SHA1:3bda240af896a4a536a09869455e1811b5daf6c1 [weak]
   - MD5Sum:8bc3859efa9038baddddcbe2224ff6ef [weak]
  Hashes of received file:
   - SHA256:a29a4dfd1467ff44a6dfaf0ef58eccd1ddaf651b6c0b88b4919ad40042855635
   - SHA1:ff9bbc122ebf6540d17ba988ed1f3e4a808cf518 [weak]
   - MD5Sum:2a39bbb1d4bf78ceb19b72d1f5fe35fe [weak]
   - Filesize:414036 [weak]
  Last modification reported: Fri, 26 Oct 2018 07:00:46 +0000
  Release file created at: Fri, 26 Oct 2018 07:00:33 +0000
Get:27 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main i386 Packages [371 kB]
Err:27 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main i386 Packages
  
Get:28 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main Translation-en [154 kB]
Get:29 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main amd64 DEP-11 Metadata [185 kB]
Get:30 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main DEP-11 48x48 Icons [44.5 kB]
Get:31 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main DEP-11 64x64 Icons [86.2 kB]
Get:32 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/restricted amd64 Packages [7,028 B]
Get:33 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/restricted i386 Packages [6,976 B]
Get:34 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/restricted Translation-en [3,076 B]
Get:35 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:36 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/universe i386 Packages [565 kB]
Get:37 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe i386 Packages [2,848 B]
Get:38 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe amd64 Packages [2,852 B]
Get:39 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe Translation-en [1,200 B]
Get:40 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,104 B]
Get:41 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe DEP-11 48x48 Icons [29 B]
Get:42 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe DEP-11 64x64 Icons [1,789 B]
Get:43 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main i386 Packages [147 kB]
Get:44 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main amd64 Packages [186 kB]
Get:45 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main Translation-en [72.1 kB]
Get:46 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:47 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main DEP-11 48x48 Icons [29 B]
Get:48 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main DEP-11 64x64 Icons [29 B]
Get:49 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe i386 Packages [90.0 kB]
Get:50 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe amd64 Packages [90.1 kB]
Get:51 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe Translation-en [48.9 kB]
Get:52 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe amd64 DEP-11 Metadata [9,404 B]
Get:53 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,088 B]
Get:54 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe DEP-11 64x64 Icons [16.3 kB]
Get:55 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/multiverse i386 Packages [1,608 B]
Get:56 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/multiverse amd64 Packages [1,440 B]
Get:57 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/multiverse Translation-en [996 B]
Fetched 43.6 MB in 1min 36s (456 kB/s)                                         
Reading package lists... Done
E: Failed to fetch http://ftp.cuhk.edu.hk/pub/Linux/ubuntu/dists/bionic-updates/main/binary-amd64/by-hash/SHA256/bddd09e41e7b9afa0ba2b73d41a796b46534f3446935777218ac582dde695409  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:414036 [weak]
    - SHA256:bddd09e41e7b9afa0ba2b73d41a796b46534f3446935777218ac582dde695409
    - SHA1:3bda240af896a4a536a09869455e1811b5daf6c1 [weak]
    - MD5Sum:8bc3859efa9038baddddcbe2224ff6ef [weak]
   Hashes of received file:
    - SHA256:a29a4dfd1467ff44a6dfaf0ef58eccd1ddaf651b6c0b88b4919ad40042855635
    - SHA1:ff9bbc122ebf6540d17ba988ed1f3e4a808cf518 [weak]
    - MD5Sum:2a39bbb1d4bf78ceb19b72d1f5fe35fe [weak]
    - Filesize:414036 [weak]
   Last modification reported: Fri, 26 Oct 2018 07:00:46 +0000
   Release file created at: Fri, 26 Oct 2018 07:00:33 +0000
E: Failed to fetch http://ftp.cuhk.edu.hk/pub/Linux/ubuntu/dists/bionic-updates/main/binary-i386/by-hash/SHA256/c2dbcc468892d6f8f6652eb250e968369a33ed4be5ae9499e3376f59ce73fca7  
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by deadflowr on 2018-10-27
Try clearing the lists files
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt clean
sudo apt update
```

---

### Post by linuxyogi on 2018-10-27
> **deadflowr said:**
> Try clearing the lists files
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt clean
sudo apt update
```

```
$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for lubuntu: 
lubuntu@lubuntu:~$ sudo apt clean
lubuntu@lubuntu:~$ sudo apt update
Get:1 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic InRelease [242 kB]
Get:2 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates InRelease [88.7 kB]
Get:3 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports InRelease [74.6 kB]
Get:4 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security InRelease [83.2 kB]
Get:5 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main amd64 Packages [1,019 kB]
Get:6 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main i386 Packages [1,007 kB]
Get:7 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main Translation-en [516 kB]
Get:8 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]
Get:9 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main DEP-11 48x48 Icons [118 kB]
Get:10 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/main DEP-11 64x64 Icons [245 kB]
Get:11 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/restricted i386 Packages [9,156 B]
Get:12 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/restricted amd64 Packages [9,184 B]
Get:13 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/restricted Translation-en [3,584 B]
Get:14 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe amd64 Packages [8,570 kB]
Get:15 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe i386 Packages [8,531 kB]                                                                                                                                                      
Get:16 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe Translation-en [4,941 kB]                                                                                                                                                     
Get:17 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe amd64 DEP-11 Metadata [3,287 kB]                                                                                                                                              
Get:18 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe DEP-11 48x48 Icons [2,151 kB]                                                                                                                                                 
Get:19 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/universe DEP-11 64x64 Icons [8,420 kB]                                                                                                                                                 
Get:20 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse amd64 Packages [151 kB]                                                                                                                                                     
Get:21 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse i386 Packages [144 kB]                                                                                                                                                      
Get:22 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse Translation-en [108 kB]                                                                                                                                                     
Get:23 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse amd64 DEP-11 Metadata [49.7 kB]                                                                                                                                             
Get:24 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse DEP-11 48x48 Icons [8,931 B]                                                                                                                                                
Get:25 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic/multiverse DEP-11 64x64 Icons [225 kB]                                                                                                                                                 
Get:26 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main amd64 Packages [414 kB]                                                                                                                                                   
Err:26 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main amd64 Packages                                                                                                                                                            
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:414036 [weak]
   - SHA256:bddd09e41e7b9afa0ba2b73d41a796b46534f3446935777218ac582dde695409
   - SHA1:3bda240af896a4a536a09869455e1811b5daf6c1 [weak]
   - MD5Sum:8bc3859efa9038baddddcbe2224ff6ef [weak]
  Hashes of received file:
   - SHA256:a29a4dfd1467ff44a6dfaf0ef58eccd1ddaf651b6c0b88b4919ad40042855635
   - SHA1:ff9bbc122ebf6540d17ba988ed1f3e4a808cf518 [weak]
   - MD5Sum:2a39bbb1d4bf78ceb19b72d1f5fe35fe [weak]
   - Filesize:414036 [weak]
  Last modification reported: Fri, 26 Oct 2018 07:00:46 +0000
  Release file created at: Fri, 26 Oct 2018 07:00:33 +0000
Get:27 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main i386 Packages [371 kB]                                                                                                                                                    
Err:27 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main i386 Packages                                                                                                                                                             
  
Get:28 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main Translation-en [154 kB]                                                                                                                                                   
Get:29 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main amd64 DEP-11 Metadata [185 kB]                                                                                                                                            
Get:30 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main DEP-11 48x48 Icons [44.5 kB]                                                                                                                                              
Get:31 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/main DEP-11 64x64 Icons [86.2 kB]                                                                                                                                              
Get:32 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/restricted amd64 Packages [7,028 B]                                                                                                                                            
Get:33 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/restricted i386 Packages [6,976 B]                                                                                                                                             
Get:34 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/restricted Translation-en [3,076 B]                                                                                                                                            
Get:35 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/universe i386 Packages [565 kB]                                                                                                                                                
Get:36 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-updates/universe amd64 Packages [570 kB]                                                                                                                                               
Get:37 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe i386 Packages [2,848 B]                                                                                                                                             
Get:38 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe amd64 Packages [2,852 B]                                                                                                                                            
Get:39 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe Translation-en [1,200 B]                                                                                                                                            
Get:40 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,104 B]                                                                                                                                     
Get:41 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe DEP-11 48x48 Icons [29 B]                                                                                                                                           
Get:42 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-backports/universe DEP-11 64x64 Icons [1,789 B]                                                                                                                                        
Get:43 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main i386 Packages [147 kB]                                                                                                                                                   
Get:44 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main amd64 Packages [186 kB]                                                                                                                                                  
Get:45 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main Translation-en [72.1 kB]                                                                                                                                                 
Get:46 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]                                                                                                                                            
Get:47 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main DEP-11 48x48 Icons [29 B]                                                                                                                                                
Get:48 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/main DEP-11 64x64 Icons [29 B]                                                                                                                                                
Get:49 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe i386 Packages [90.0 kB]                                                                                                                                              
Get:50 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe amd64 Packages [90.1 kB]                                                                                                                                             
Get:51 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe Translation-en [48.9 kB]                                                                                                                                             
Get:52 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe amd64 DEP-11 Metadata [9,404 B]                                                                                                                                      
Get:53 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,088 B]                                                                                                                                         
Get:54 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/universe DEP-11 64x64 Icons [16.3 kB]                                                                                                                                         
Get:55 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/multiverse amd64 Packages [1,440 B]                                                                                                                                           
Get:56 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/multiverse i386 Packages [1,608 B]                                                                                                                                            
Get:57 http://ftp.cuhk.edu.hk/pub/Linux/ubuntu bionic-security/multiverse Translation-en [996 B]                                                                                                                                             
Fetched 43.6 MB in 1min 52s (390 kB/s)                                                                                                                                                                                                       
Reading package lists... Done
E: Failed to fetch http://ftp.cuhk.edu.hk/pub/Linux/ubuntu/dists/bionic-updates/main/binary-amd64/by-hash/SHA256/bddd09e41e7b9afa0ba2b73d41a796b46534f3446935777218ac582dde695409  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:414036 [weak]
    - SHA256:bddd09e41e7b9afa0ba2b73d41a796b46534f3446935777218ac582dde695409
    - SHA1:3bda240af896a4a536a09869455e1811b5daf6c1 [weak]
    - MD5Sum:8bc3859efa9038baddddcbe2224ff6ef [weak]
   Hashes of received file:
    - SHA256:a29a4dfd1467ff44a6dfaf0ef58eccd1ddaf651b6c0b88b4919ad40042855635
    - SHA1:ff9bbc122ebf6540d17ba988ed1f3e4a808cf518 [weak]
    - MD5Sum:2a39bbb1d4bf78ceb19b72d1f5fe35fe [weak]
    - Filesize:414036 [weak]
   Last modification reported: Fri, 26 Oct 2018 07:00:46 +0000
   Release file created at: Fri, 26 Oct 2018 07:00:33 +0000
E: Failed to fetch http://ftp.cuhk.edu.hk/pub/Linux/ubuntu/dists/bionic-updates/main/binary-i386/by-hash/SHA256/c2dbcc468892d6f8f6652eb250e968369a33ed4be5ae9499e3376f59ce73fca7  
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by linuxyogi on 2018-10-27
Strange issue. If I select any other mirror and then revert back to India it works for a period of time.

```
lubuntu@lubuntu:~$ sudo apt update
Get:1 http://in.archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:3 http://in.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1,019 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu bionic/main i386 Packages [1,007 kB] 
Get:7 http://in.archive.ubuntu.com/ubuntu bionic/main Translation-en [516 kB]  
Get:8 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu bionic/main DEP-11 48x48 Icons [118 kB]
Get:10 http://in.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons [245 kB]
Get:11 http://in.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [9,184 B]
Get:12 http://in.archive.ubuntu.com/ubuntu bionic/restricted i386 Packages [9,156 B]
Get:13 http://in.archive.ubuntu.com/ubuntu bionic/restricted Translation-en [3,584 B]
Get:14 http://in.archive.ubuntu.com/ubuntu bionic/universe i386 Packages [8,531 kB]
Get:15 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8,570 kB]
Get:16 http://in.archive.ubuntu.com/ubuntu bionic/universe Translation-en [4,941 kB]
Get:17 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata [3,287 kB]
Get:18 http://in.archive.ubuntu.com/ubuntu bionic/universe DEP-11 48x48 Icons [2,151 kB]
Get:19 http://in.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons [8,420 kB]
Get:20 http://in.archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages [144 kB]
Get:21 http://in.archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [151 kB]
Get:22 http://in.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en [108 kB]
Get:23 http://in.archive.ubuntu.com/ubuntu bionic/multiverse amd64 DEP-11 Metadata [49.7 kB]
Get:24 http://in.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 48x48 Icons [8,931 B]
Get:25 http://in.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64 Icons [225 kB]
Get:26 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [414 kB]
Get:27 http://in.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [371 kB]
Get:28 http://in.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [154 kB]
Get:29 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [185 kB]
Get:30 http://in.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [44.5 kB]
Get:31 http://in.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [86.2 kB]
Get:32 http://in.archive.ubuntu.com/ubuntu bionic-updates/restricted i386 Packages [6,976 B]
Get:33 http://in.archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [7,028 B]
Get:34 http://in.archive.ubuntu.com/ubuntu bionic-updates/restricted Translation-en [3,076 B]
Get:35 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:36 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [565 kB]
Get:37 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [151 kB]
Get:38 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [191 kB]
Get:39 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [193 kB]
Get:40 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [319 kB]
Get:41 http://in.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [5,708 B]
Get:42 http://in.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 Packages [5,864 B]
Get:43 http://in.archive.ubuntu.com/ubuntu bionic-updates/multiverse Translation-en [3,176 B]
Get:44 http://in.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:45 http://in.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 48x48 Icons [29 B]
Get:46 http://in.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64 Icons [2,638 B]
Get:47 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [2,852 B]
Get:48 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe i386 Packages [2,848 B]
Get:49 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe Translation-en [1,200 B]
Get:50 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,104 B]
Get:51 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 48x48 Icons [29 B]
Get:52 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64 Icons [1,789 B]
Get:53 http://in.archive.ubuntu.com/ubuntu bionic-security/main i386 Packages [149 kB]
Get:54 http://in.archive.ubuntu.com/ubuntu bionic-security/main amd64 Packages [187 kB]
Get:55 http://in.archive.ubuntu.com/ubuntu bionic-security/main Translation-en [72.7 kB]
Get:56 http://in.archive.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:57 http://in.archive.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [29 B]
Get:58 http://in.archive.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [29 B]
Get:59 http://in.archive.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [91.3 kB]
Get:60 http://in.archive.ubuntu.com/ubuntu bionic-security/universe i386 Packages [91.2 kB]
Get:61 http://in.archive.ubuntu.com/ubuntu bionic-security/universe Translation-en [50.0 kB]
Get:62 http://in.archive.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [9,396 B]
Get:63 http://in.archive.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,090 B]
Get:64 http://in.archive.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [16.3 kB]
Get:65 http://in.archive.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [1,440 B]
Get:66 http://in.archive.ubuntu.com/ubuntu bionic-security/multiverse i386 Packages [1,608 B]
Get:67 http://in.archive.ubuntu.com/ubuntu bionic-security/multiverse Translation-en [996 B]
Fetched 44.5 MB in 1min 11s (623 kB/s)                                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

---

### Post by again? on 2018-10-27
FYI I had this sort of Hash Sum mismatch error intermittently for a month or so with my ISP's mirror.
It would work fine the next day.
Don't know why the error but I would just leave it for a day or switch to the main archives.
I contacted my ISP but the tech support didn't know what Linux was or that they were running an Ubuntu mirror server. :rolleyes:#-o

---

### Post by linuxyogi on 2018-10-27
> **guber2 said:**
> FYI I had this sort of Hash Sum mismatch error intermittently for a month or so with my ISP's mirror.
It would work fine the next day.
Don't know why the error but I would just leave it for a day or switch to the main archives.
I contacted my ISP but the tech support didn't know what Linux was or that they were running an Ubuntu mirror server. :rolleyes:#-o

How do I know for sure that my ISP is using their own mirror?

Is there a way to verify this ?

If they are using their own mirror is there a way to connect directly to the Ubuntu  repos ?

---

### Post by again? on 2018-10-27
> **linuxyogi said:**
> How do I know for sure that my ISP is using their own mirror?

Is there a way to verify this ?

If they are using their own mirror is there a way to connect directly to the Ubuntu  repos ?

I may have confused you.
I am talking about the mirror you choose in software sources.
My ISP is iinet which is included in the regional mirror list.
You choose your update mirror not your ISP.

---

### Post by linuxyogi on 2018-10-27
Okay understood. But you said that I should choose the main mirror if problem persists but I have already tried that same result.

I also tried the Hong Kong mirror same result.

I guess I will wait for some days and test again.

---

### Post by linuxyogi on 2018-10-31
Still the same thing is happening. Very irritating.

```
$ sudo apt update 
[sudo] password for lubuntu: 
Hit:1 http://in.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://in.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [416 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [372 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [155 kB]
Get:8 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [185 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [44.5 kB]
Get:10 http://in.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [86.2 kB]
Get:11 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [565 kB]
Err:11 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:565092 [weak]
   - SHA256:ac47a6d95cf30707c18cf552c33907ad328afe139986c465e1f237b4edad5129
   - SHA1:41ae8c413c477f74a663a81d34e902052565abd3 [weak]
   - MD5Sum:645646fcd695a018796a94b02bc285a0 [weak]
  Hashes of received file:
   - SHA256:67b6f90c7f8c9c4a088d6a94c9dfd227f5f58ca58e3547aae1d4948820154e36
   - SHA1:6c76c81eb5dbcc2f2abb404295f7c09f5b2a8ec9 [weak]
   - MD5Sum:23b1d0e503041dfa9cf550e82be38d8d [weak]
   - Filesize:565092 [weak]
  Last modification reported: Wed, 31 Oct 2018 00:56:12 +0000
  Release file created at: Wed, 31 Oct 2018 00:55:58 +0000
Get:12 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Err:12 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
  
Get:13 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [151 kB]
Get:14 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [191 kB]
Get:15 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [185 kB]
Get:16 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [308 kB]
Get:17 http://in.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:18 http://in.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,104 B]
Get:19 http://in.archive.ubuntu.com/ubuntu bionic-security/main amd64 Packages [187 kB]
Err:19 http://in.archive.ubuntu.com/ubuntu bionic-security/main amd64 Packages                                                                                                                                                               
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:187152 [weak]
   - SHA256:a08d830e1e00715234571cf3e64fce1fc9ac8b1932e784703b8023db12b86483
   - SHA1:d7d6111fcc95675f6f55bce365a2a90743140ddb [weak]
   - MD5Sum:553e46220c1d18a56c6f3d232f6e8f6d [weak]
  Hashes of received file:
   - SHA256:a0acbb3d7307f0d8c4df061efd504fcc99bcc08c7d9bd7fd4c902ddc46729479
   - SHA1:2363b2d9788f55d35b4fd5d13e7a44a01d6bcd25 [weak]
   - MD5Sum:55c6068df05a8b325a17178ae1b994bd [weak]
   - Filesize:187152 [weak]
  Last modification reported: Tue, 30 Oct 2018 18:46:50 +0000
  Release file created at: Tue, 30 Oct 2018 20:00:50 +0000
Get:20 http://in.archive.ubuntu.com/ubuntu bionic-security/main i386 Packages [149 kB]                                                                                                                                                       
Get:21 http://in.archive.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]                                                                                                                                                
Get:22 http://in.archive.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [91.5 kB]                                                                                                                                                 
Get:23 http://in.archive.ubuntu.com/ubuntu bionic-security/universe i386 Packages [91.4 kB]                                                                                                                                                  
Get:24 http://in.archive.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [9,420 B]                                                                                                                                          
Get:25 http://in.archive.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,084 B]                                                                                                                                             
Fetched 4,021 kB in 15s (265 kB/s)                                                                                                                                                                                                           
Reading package lists... Done
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/universe/binary-i386/by-hash/SHA256/ac47a6d95cf30707c18cf552c33907ad328afe139986c465e1f237b4edad5129  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:565092 [weak]
    - SHA256:ac47a6d95cf30707c18cf552c33907ad328afe139986c465e1f237b4edad5129
    - SHA1:41ae8c413c477f74a663a81d34e902052565abd3 [weak]
    - MD5Sum:645646fcd695a018796a94b02bc285a0 [weak]
   Hashes of received file:
    - SHA256:67b6f90c7f8c9c4a088d6a94c9dfd227f5f58ca58e3547aae1d4948820154e36
    - SHA1:6c76c81eb5dbcc2f2abb404295f7c09f5b2a8ec9 [weak]
    - MD5Sum:23b1d0e503041dfa9cf550e82be38d8d [weak]
    - Filesize:565092 [weak]
   Last modification reported: Wed, 31 Oct 2018 00:56:12 +0000
   Release file created at: Wed, 31 Oct 2018 00:55:58 +0000
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/universe/binary-amd64/by-hash/SHA256/863be2951b3fbd2365860ea2d289468bd9e22e5583341fdbfd4f22cbb8d4b390  
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/bionic-security/main/binary-amd64/by-hash/SHA256/a08d830e1e00715234571cf3e64fce1fc9ac8b1932e784703b8023db12b86483  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:187152 [weak]
    - SHA256:a08d830e1e00715234571cf3e64fce1fc9ac8b1932e784703b8023db12b86483
    - SHA1:d7d6111fcc95675f6f55bce365a2a90743140ddb [weak]
    - MD5Sum:553e46220c1d18a56c6f3d232f6e8f6d [weak]
   Hashes of received file:
    - SHA256:a0acbb3d7307f0d8c4df061efd504fcc99bcc08c7d9bd7fd4c902ddc46729479
    - SHA1:2363b2d9788f55d35b4fd5d13e7a44a01d6bcd25 [weak]
    - MD5Sum:55c6068df05a8b325a17178ae1b994bd [weak]
    - Filesize:187152 [weak]
   Last modification reported: Tue, 30 Oct 2018 18:46:50 +0000
   Release file created at: Tue, 30 Oct 2018 20:00:50 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by linuxyogi on 2018-10-31
Just reinstalled. Same result. Please help.

---

### Post by again? on 2018-10-31
Same result if you chose the main server?

---

### Post by linuxyogi on 2018-10-31
> **guber2 said:**
> Same result if you chose the main server?

Yes same result

```
$ sudo apt update 
[sudo] password for lubuntu: 
Hit:1 http://archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Get:5 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [416 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [372 kB]
Get:7 http://archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [155 kB]
Get:8 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [185 kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [44.5 kB]
Get:10 http://archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [86.2 kB]
Get:11 http://archive.ubuntu.com/ubuntu bionic-updates/restricted i386 Packages [6,976 B]
Get:12 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [7,028 B]
Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/restricted Translation-en [3,076 B]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [570 kB]
Err:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages 
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:570096 [weak]
   - SHA256:863be2951b3fbd2365860ea2d289468bd9e22e5583341fdbfd4f22cbb8d4b390
   - SHA1:e6c7a34ee166590f924bd2a36e5fae3493e836c5 [weak]
   - MD5Sum:06278163364032d603d7ee0f567260f4 [weak]
  Hashes of received file:
   - SHA256:423fcf5d1f3d7f0d59576bf85996a05890d4abb1e907ddafac993434a9bd3328
   - SHA1:3e5e6365116c992ff98c5dab28985922e4342cb0 [weak]
   - MD5Sum:2a6951d2809cf671818354616feb921f [weak]
   - Filesize:570096 [weak]
  Last modification reported: Wed, 31 Oct 2018 00:56:12 +0000
  Release file created at: Wed, 31 Oct 2018 06:48:53 +0000
Get:23 http://archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [565 kB]
Err:23 http://archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages  
  
Get:24 http://archive.ubuntu.com/ubuntu bionic-security/main amd64 Packages [187 kB]
Err:24 http://archive.ubuntu.com/ubuntu bionic-security/main amd64 Packages                                                                                                                                                                  
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:187152 [weak]
   - SHA256:a08d830e1e00715234571cf3e64fce1fc9ac8b1932e784703b8023db12b86483
   - SHA1:d7d6111fcc95675f6f55bce365a2a90743140ddb [weak]
   - MD5Sum:553e46220c1d18a56c6f3d232f6e8f6d [weak]
  Hashes of received file:
   - SHA256:a0acbb3d7307f0d8c4df061efd504fcc99bcc08c7d9bd7fd4c902ddc46729479
   - SHA1:2363b2d9788f55d35b4fd5d13e7a44a01d6bcd25 [weak]
   - MD5Sum:55c6068df05a8b325a17178ae1b994bd [weak]
   - Filesize:187152 [weak]
  Last modification reported: Tue, 30 Oct 2018 18:46:50 +0000
  Release file created at: Wed, 31 Oct 2018 06:48:43 +0000
Get:25 http://archive.ubuntu.com/ubuntu bionic-security/main i386 Packages [149 kB]                                                                                                                                                          
Get:26 http://archive.ubuntu.com/ubuntu bionic-security/main Translation-en [72.7 kB]                                                                                                                                                        
Get:27 http://archive.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]                                                                                                                                                   
Get:28 http://archive.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [29 B]                                                                                                                                                       
Get:29 http://archive.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [29 B]                                                                                                                                                       
Get:30 http://archive.ubuntu.com/ubuntu bionic-security/universe i386 Packages [91.4 kB]                                                                                                                                                     
Get:31 http://archive.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [91.5 kB]                                                                                                                                                    
Get:32 http://archive.ubuntu.com/ubuntu bionic-security/universe Translation-en [50.3 kB]                                                                                                                                                    
Get:33 http://archive.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [9,420 B]                                                                                                                                             
Get:34 http://archive.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,084 B]                                                                                                                                                
Fetched 1,569 kB in 17s (90.1 kB/s)                                                                                                                                                                                                          
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/universe/binary-amd64/by-hash/SHA256/863be2951b3fbd2365860ea2d289468bd9e22e5583341fdbfd4f22cbb8d4b390  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:570096 [weak]
    - SHA256:863be2951b3fbd2365860ea2d289468bd9e22e5583341fdbfd4f22cbb8d4b390
    - SHA1:e6c7a34ee166590f924bd2a36e5fae3493e836c5 [weak]
    - MD5Sum:06278163364032d603d7ee0f567260f4 [weak]
   Hashes of received file:
    - SHA256:423fcf5d1f3d7f0d59576bf85996a05890d4abb1e907ddafac993434a9bd3328
    - SHA1:3e5e6365116c992ff98c5dab28985922e4342cb0 [weak]
    - MD5Sum:2a6951d2809cf671818354616feb921f [weak]
    - Filesize:570096 [weak]
   Last modification reported: Wed, 31 Oct 2018 00:56:12 +0000
   Release file created at: Wed, 31 Oct 2018 06:48:53 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/universe/binary-i386/by-hash/SHA256/ac47a6d95cf30707c18cf552c33907ad328afe139986c465e1f237b4edad5129  
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-security/main/binary-amd64/by-hash/SHA256/a08d830e1e00715234571cf3e64fce1fc9ac8b1932e784703b8023db12b86483  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:187152 [weak]
    - SHA256:a08d830e1e00715234571cf3e64fce1fc9ac8b1932e784703b8023db12b86483
    - SHA1:d7d6111fcc95675f6f55bce365a2a90743140ddb [weak]
    - MD5Sum:553e46220c1d18a56c6f3d232f6e8f6d [weak]
   Hashes of received file:
    - SHA256:a0acbb3d7307f0d8c4df061efd504fcc99bcc08c7d9bd7fd4c902ddc46729479
    - SHA1:2363b2d9788f55d35b4fd5d13e7a44a01d6bcd25 [weak]
    - MD5Sum:55c6068df05a8b325a17178ae1b994bd [weak]
    - Filesize:187152 [weak]
   Last modification reported: Tue, 30 Oct 2018 18:46:50 +0000
   Release file created at: Wed, 31 Oct 2018 06:48:43 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by again? on 2018-10-31
Using main server...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt update**
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
```

Ok here.
As you reinstalled I don't really know.
Wouldn't hurt to post your computer details. Someone may know of a recent hardware/kernel bug.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] inxi -b**
System:    Host: Bionic Kernel: 4.15.0-38-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x serial: N/A BIOS: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1407/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1680x1050@59.88hz
           OpenGL: renderer: GeForce GTX 550 Ti/PCIe/SSE2 version: 4.6.0 NVIDIA 390.87
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 870.2GB (13.8% used)
Info:      Processes: 232 Uptime: 1 day Memory: 1322.3/3926.7MB Client: Shell (bash) inxi: 2.3.56
```

---

### Post by linuxyogi on 2018-10-31
> **guber2 said:**
> Using main server...
```
**[COLOR=#006400]glen@Bionic:~$[/COLOR] sudo apt update**
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
```

Ok here.
As you reinstalled I don't really know.
Wouldn't hurt to post your computer details. Someone may know of a recent hardware/kernel bug.
```
**[COLOR=#006400]glen@Bionic:~$[/COLOR] inxi -b**
System:    Host: Bionic Kernel: 4.15.0-38-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x serial: N/A BIOS: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1407/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1680x1050@59.88hz
           OpenGL: renderer: GeForce GTX 550 Ti/PCIe/SSE2 version: 4.6.0 NVIDIA 390.87
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 870.2GB (13.8% used)
Info:      Processes: 232 Uptime: 1 day Memory: 1322.3/3926.7MB Client: Shell (bash) inxi: 2.3.56
```


```
$ inxi -b
System:    Host: lubuntu Kernel: 4.15.0-29-generic x86_64 bits: 64
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: H110M-CS v: Rev X.0x serial: N/A
           UEFI: American Megatrends v: 3016 date: 12/27/2016
CPU:       Dual core Intel Core i3-6100 (-MT-MCP-) speed/max: 800/3700 MHz
Graphics:  Card: Intel HD Graphics 530
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           version: 4.5 Mesa 18.0.5
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 120.0GB (12.4% used)
Info:      Processes: 182 Uptime: 1:52 Memory: 847.7/3810.9MB
           Client: Shell (bash) inxi: 2.3.56
```

---

### Post by linuxyogi on 2018-10-31
I got fed up and installed OpenSUSE. All well now.

---

