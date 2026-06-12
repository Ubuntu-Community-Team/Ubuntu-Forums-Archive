---
title: "I can't run sudo apt-get update!"
date: 2017-02-10
forum: General Help
---

### Post by jsc12345 on 2017-02-10
A week or two ago, I tried installing Webby, which is like Fogger. For this, I had to add a ppa. This went well. Great! I thought, now I just have to update the package lists! So I ran sudo apt-get update, and after a bit I got "W: Can't locate certain files. They have been ignored, or old ones have been used instead." Of course, that's not a proper update." I have already taken two different steps to fix this, namely switching the DNS servver to Google's, and changing the update server from the South African one to the Main one. So what can I do to fix this?

---

### Post by howefield on 2017-02-10
What version  of Ubuntu are you using ?

Can you post the output of..

```
sudo apt-get update
```
and
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by &amp;KyT$0P# on 2017-02-10
Also how did you add the PPA?

---

### Post by jsc12345 on 2017-02-10
In answer to the first reply, the code is:

```
Hit:1 [http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu](http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu) yakkety InRelease
Ign:2 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety InRelease            
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) yakkety InRelease         
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates InRelease [102 kB]      
Hit:7 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) yakkety InRelease        
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Ign:10 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety InRelease       
Ign:11 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety InRelease
Hit:12 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) yakkety InRelease
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports InRelease [102 kB]
Ign:14 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety Release
Ign:15 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety Release
Ign:16 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety Release
Ign:17 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main i386 Packages
Ign:18 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all Packages
Ign:19 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 Packages
Ign:20 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security InRelease [102 kB]
Ign:22 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en_ZA
Ign:23 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:24 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all DEP-11 Metadata
Ign:25 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:26 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main i386 Packages
Ign:27 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all Packages
Ign:28 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 Packages
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main amd64 Packages [182 kB]
Ign:30 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en
Ign:31 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:32 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Err:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main amd64 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Checksum-FileSize:181668 [weak]
   - SHA256:1e05717b4e1a2824c1d0715662f652d0cb4dc084e8f23c4f5c2a1a0cad89be7e
   - SHA1:2c1b7be6ec22e21bf14ea6971734a742036e932f [weak]
   - MD5Sum:756da8ae5e162646995bb90adfe5f407 [weak]
  Hashes of received file:
   - SHA256:ac80c22f4cf78ad176eacb5f7b2d8baa1daac25310049b79635930cfbd4d9c90
   - SHA1:75571e7145e119faa67ff1986063ffa0db1a46a7 [weak]
   - MD5Sum:df6d22c07a398f98fab4ab7fb6410a2b [weak]
   - Checksum-FileSize:181668 [weak]
  Last modification reported: Fri, 10 Feb 2017 13:26:02 +0000
  Release file created at: Fri, 10 Feb 2017 17:41:25 +0000
Ign:33 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Get:34 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main i386 Packages [179 kB]
Ign:35 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:36 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main i386 Packages
Ign:37 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 Packages
Ign:38 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all Packages
Ign:39 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en
Ign:40 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en_ZA
Get:41 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main amd64 DEP-11 Metadata [114 kB]
Ign:42 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:43 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:44 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:17 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main i386 Packages
Ign:18 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all Packages
Ign:19 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 Packages
Ign:20 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en
Ign:22 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en_ZA
Ign:23 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:24 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all DEP-11 Metadata
Ign:25 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main DEP-11 64x64 Icons
Get:45 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main DEP-11 64x64 Icons [54.6 kB]
Ign:26 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main i386 Packages
Ign:27 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all Packages
Ign:28 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en
Get:46 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe i386 Packages [99.8 kB]
Ign:31 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:32 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:33 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:35 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Get:47 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe amd64 Packages [102 kB]
Ign:36 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main i386 Packages
Ign:37 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 Packages
Ign:38 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all Packages 
Get:48 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe amd64 DEP-11 Metadata [95.6 kB]
Ign:39 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en
Ign:40 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en_ZA
Get:49 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe DEP-11 64x64 Icons [118 kB]
Ign:42 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:43 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:44 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Get:50 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports/main amd64 DEP-11 Metadata [3,324 B]
Ign:17 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main i386 Packages
Get:51 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security/main amd64 DEP-11 Metadata [8,268 B]
Ign:18 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all Packages
Get:52 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security/main DEP-11 64x64 Icons [9,965 B]
Ign:19 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 Packages
Get:53 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security/universe i386 Packages [35.1 kB]
Ign:20 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en
Get:54 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security/universe amd64 Packages [37.4 kB]
Ign:22 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en_ZA
Get:55 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security/universe Translation-en [24.0 kB]
Ign:23 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 DEP-11 Metadata
Get:56 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security/universe amd64 DEP-11 Metadata [9,736 B]
Ign:24 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all DEP-11 Metadata
Get:57 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security/universe DEP-11 64x64 Icons [6,224 B]
Ign:25 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:26 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main i386 Packages
Ign:27 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all Packages
Ign:28 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en
Ign:31 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:32 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:33 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:35 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:36 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main i386 Packages
Ign:37 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 Packages
Ign:38 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all Packages 
Ign:39 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en
Ign:40 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:42 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:43 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:44 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:17 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main i386 Packages
Ign:18 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all Packages
Ign:19 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 Packages
Ign:20 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en
Ign:22 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en_ZA
Ign:23 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:24 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all DEP-11 Metadata
Ign:25 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:26 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main i386 Packages
Ign:27 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all Packages
Ign:28 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en
Ign:31 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:32 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:33 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:35 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:36 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main i386 Packages
Ign:37 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 Packages
Ign:38 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all Packages 
Ign:39 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en
Ign:40 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:42 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:43 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:44 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:17 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main i386 Packages
Ign:18 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all Packages
Ign:19 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 Packages
Ign:20 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en
Ign:22 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en_ZA
Ign:23 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:24 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all DEP-11 Metadata
Ign:25 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:26 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main i386 Packages
Ign:27 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all Packages
Ign:28 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en
Ign:31 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:32 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:33 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:35 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Ign:36 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main i386 Packages
Ign:37 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 Packages
Ign:38 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all Packages
Ign:39 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en
Ign:40 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:42 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:43 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:44 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Err:17 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main i386 Packages
  404  Not Found
Ign:18 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all Packages
Ign:19 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 Packages
Ign:20 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en
Ign:22 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main Translation-en_ZA
Ign:23 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:24 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main all DEP-11 Metadata
Ign:25 [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety/main DEP-11 64x64 Icons
Err:26 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main i386 Packages
  404  Not Found
Ign:27 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all Packages
Ign:28 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 Packages
Ign:30 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en
Ign:31 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:32 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:33 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:35 [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Err:36 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main i386 Packages
  404  Not Found
Ign:37 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 Packages
Ign:38 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all Packages
Ign:39 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en
Ign:40 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main Translation-en_ZA
Ign:42 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main all DEP-11 Metadata
Ign:43 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main amd64 DEP-11 Metadata
Ign:44 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety/main DEP-11 64x64 Icons
Fetched 1,385 kB in 34s (40.3 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/tombeckmann/ppa/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/main/binary-amd64/by-hash/SHA256/1e05717b4e1a2824c1d0715662f652d0cb4dc084e8f23c4f5c2a1a0cad89be7e](http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/main/binary-amd64/by-hash/SHA256/1e05717b4e1a2824c1d0715662f652d0cb4dc084e8f23c4f5c2a1a0cad89be7e)  Hash Sum mismatch
   Hashes of expected file:
    - Checksum-FileSize:181668 [weak]
    - SHA256:1e05717b4e1a2824c1d0715662f652d0cb4dc084e8f23c4f5c2a1a0cad89be7e
    - SHA1:2c1b7be6ec22e21bf14ea6971734a742036e932f [weak]
    - MD5Sum:756da8ae5e162646995bb90adfe5f407 [weak]
   Hashes of received file:
    - SHA256:ac80c22f4cf78ad176eacb5f7b2d8baa1daac25310049b79635930cfbd4d9c90
    - SHA1:75571e7145e119faa67ff1986063ffa0db1a46a7 [weak]
    - MD5Sum:df6d22c07a398f98fab4ab7fb6410a2b [weak]
    - Checksum-FileSize:181668 [weak]
   Last modification reported: Fri, 10 Feb 2017 13:26:02 +0000
   Release file created at: Fri, 10 Feb 2017 17:41:25 +0000
E: Failed to fetch [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu/dists/yakkety/main/binary-i386/Packages](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu/dists/yakkety/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```
The second piece is:
```
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security multiverse
/etc/apt/sources.list.d/dawidd0811-ubuntu-neofetch-yakkety.list:deb [http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu](http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu) yakkety main
/etc/apt/sources.list.d/dawidd0811-ubuntu-neofetch-yakkety.list.save:deb [http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu](http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu) yakkety main
/etc/apt/sources.list.d/erasmo-marin-ubuntu-webby-browser-yakkety.list:deb [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety main
/etc/apt/sources.list.d/erasmo-marin-ubuntu-webby-browser-yakkety.list.save:deb [http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu](http://ppa.launchpad.net/erasmo-marin/webby-browser/ubuntu) yakkety main
/etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-yakkety.list:deb [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-yakkety.list.save:deb [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-yakkety.list:deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-yakkety.list.save:deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/tombeckmann-ubuntu-ppa-yakkety.list:deb [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/tombeckmann-ubuntu-ppa-yakkety.list.save:deb [http://ppa.launchpad.net/tombeckmann/ppa/ubuntu](http://ppa.launchpad.net/tombeckmann/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/tualatrix-ubuntu-ppa-yakkety.list:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/tualatrix-ubuntu-ppa-yakkety.list.save:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-yakkety.list:deb [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) yakkety main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-yakkety.list.save:deb [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) yakkety main
```

I run Yakkety.
In answer to halogen2, I did it with an add-apt repository command.

---

### Post by QIII on 2017-02-10
Hello!

The first thing I would do is disable all those PPAs and try to update.

Then, I would take a very hard look at the PPAs and decide which ones I absolutely had to use.  I use only one, personally, and that is from webupd8.  PPAs are problematic.  They are not official and you cannot assume that they have been tested to avoid conflicts.  A PPA maintainer can put anything they want in their PPA, some of which may even be dangerous or malicious.

---

### Post by Perfect Storm on 2017-02-10
> **QIII said:**
> Hello!

The first thing I would do is disable all those PPAs and try to update.

Then, I would take a very hard look at the PPAs and decide which ones I absolutely had to use.  I use only one, personally, and that is from webupd8.  PPAs are problematic.  They are not official and you cannot assume that they have been tested to avoid conflicts.  A PPA maintainer can put anything they want in their PPA, some of which may even be dangerous or malicious.

I second that. It looks like one big mess.

---

### Post by howefield on 2017-02-10
There is no yakkety repository for Webby, likewise a couple of your other ppas so you are basically querying non existent repositories.  I'd suggest removing them and then trying a  sudo apt update again, if no errors fine, if there are post back here with the output of the update command. 

```
sudo rm /etc/apt/sources.list.d/erasmo-marin-ubuntu-webby-browser-yakkety.list*
```
```
sudo rm /etc/apt/sources.list.d/tombeckmann-ubuntu-ppa-yakkety.list*
```
```
sudo rm /etc/apt/sources.list.d/tualatrix-ubuntu-ppa-yakkety.list*
```

---

### Post by jsc12345 on 2017-02-11
I removed those three ppas, and a still got an "E: Some index files failed to download" error. This time, the output was:
Code:
```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu](http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu) yakkety InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety InRelease
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:6 [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) yakkety InRelease         
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports InRelease       
Hit:9 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) yakkety InRelease 
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security InRelease [102 kB]
Hit:11 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) yakkety InRelease      
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates InRelease [102 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main amd64 Packages [182 kB]
Err:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main amd64 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Checksum-FileSize:181668 [weak]
   - SHA256:55c0847a8c7168addbd6441090b437f6009a946f0ff99946a77b02dede099c17
   - SHA1:47b77a3d97cb9c90d97e26c636d0598e8d1eef47 [weak]
   - MD5Sum:f4e0ab51459ab5d6db12aae1d6f0005b [weak]
  Hashes of received file:
   - SHA256:ac80c22f4cf78ad176eacb5f7b2d8baa1daac25310049b79635930cfbd4d9c90
   - SHA1:75571e7145e119faa67ff1986063ffa0db1a46a7 [weak]
   - MD5Sum:df6d22c07a398f98fab4ab7fb6410a2b [weak]
   - Checksum-FileSize:181668 [weak]
  Last modification reported: Sat, 11 Feb 2017 00:59:33 +0000
  Release file created at: Sat, 11 Feb 2017 03:25:42 +0000
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main i386 Packages [179 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main amd64 DEP-11 Metadata [114 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/main DEP-11 64x64 Icons [64.7 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe i386 Packages [101 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe amd64 Packages [103 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe Translation-en [55.8 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe amd64 DEP-11 Metadata [95.7 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates/universe DEP-11 64x64 Icons [118 kB]
Fetched 386 kB in 3s (102 kB/s)
Reading package lists... Done
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/main/binary-amd64/by-hash/SHA256/55c0847a8c7168addbd6441090b437f6009a946f0ff99946a77b02dede099c17](http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/main/binary-amd64/by-hash/SHA256/55c0847a8c7168addbd6441090b437f6009a946f0ff99946a77b02dede099c17)  Hash Sum mismatch
   Hashes of expected file:
    - Checksum-FileSize:181668 [weak]
    - SHA256:55c0847a8c7168addbd6441090b437f6009a946f0ff99946a77b02dede099c17
    - SHA1:47b77a3d97cb9c90d97e26c636d0598e8d1eef47 [weak]
    - MD5Sum:f4e0ab51459ab5d6db12aae1d6f0005b [weak]
   Hashes of received file:
    - SHA256:ac80c22f4cf78ad176eacb5f7b2d8baa1daac25310049b79635930cfbd4d9c90
    - SHA1:75571e7145e119faa67ff1986063ffa0db1a46a7 [weak]
    - MD5Sum:df6d22c07a398f98fab4ab7fb6410a2b [weak]
    - Checksum-FileSize:181668 [weak]
   Last modification reported: Sat, 11 Feb 2017 00:59:33 +0000
   Release file created at: Sat, 11 Feb 2017 03:25:42 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.
```
The output of the second command is:
Code
```
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security multiverse
/etc/apt/sources.list.d/dawidd0811-ubuntu-neofetch-yakkety.list:deb [http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu](http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu) yakkety main
/etc/apt/sources.list.d/dawidd0811-ubuntu-neofetch-yakkety.list.save:deb [http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu](http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu) yakkety main
/etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-yakkety.list:deb [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-yakkety.list.save:deb [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-yakkety.list:deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-yakkety.list.save:deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) yakkety main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-yakkety.list:deb [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) yakkety main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-yakkety.list.save:deb [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) yakkety main
```
So any ideas?

---

### Post by wildmanne39 on 2017-02-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jsc12345 on 2017-02-11
In reply to QIII, can you suggest a way to do that without removing the Google Chrome PPA?

---

### Post by Perfect Storm on 2017-02-11
Yes.

aso try:
```
sudo apt-get clean
sudo rm -r /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by jsc12345 on 2017-02-11
Didn't work. It now outputs: 
```
 Get:1 http://archive.ubuntu.com/ubuntu yakkety InRelease [247 kB]              Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:3 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]          
Get:4 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu yakkety InRelease [18.1 kB]
Get:5 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]         
Get:6 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu yakkety InRelease [18.1 kB]
Get:7 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,434 B]
Get:8 http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety InRelease [23.8 kB]
Get:9 http://archive.ubuntu.com/ubuntu yakkety-updates InRelease [102 kB]      
Get:10 http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety InRelease [18.1 kB]
Get:11 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu yakkety/main i386 Packages [532 B]
Get:12 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu yakkety/main amd64 Packages [532 B]
Get:13 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu yakkety/main Translation-en [360 B]
Get:14 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu yakkety/main amd64 Packages [520 B]
Get:15 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu yakkety/main i386 Packages [520 B]
Get:16 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu yakkety/main Translation-en [188 B]
Get:17 http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety/main amd64 Packages [29.7 kB]
Get:18 http://archive.ubuntu.com/ubuntu yakkety-backports InRelease [102 kB]
Get:19 http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety/main i386 Packages [29.7 kB]
Get:20 http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety/main Translation-en [11.7 kB]
Get:21 http://archive.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]    
Get:22 http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety/main amd64 Packages [2,440 B]
Get:23 http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety/main i386 Packages [2,392 B]
Get:24 http://archive.ubuntu.com/ubuntu yakkety/main amd64 Packages [1,222 kB] 
Get:25 http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety/main Translation-en [980 B]
Get:26 http://archive.ubuntu.com/ubuntu yakkety/main i386 Packages [1,218 kB]  
Get:27 http://archive.ubuntu.com/ubuntu yakkety/main Translation-en [582 kB]   
Get:28 http://archive.ubuntu.com/ubuntu yakkety/main amd64 DEP-11 Metadata [654 kB]
Get:29 http://archive.ubuntu.com/ubuntu yakkety/main DEP-11 64x64 Icons [368 kB]
Get:30 http://archive.ubuntu.com/ubuntu yakkety/restricted i386 Packages [8,724 B]
Get:31 http://archive.ubuntu.com/ubuntu yakkety/restricted amd64 Packages [8,416 B]
Get:32 http://archive.ubuntu.com/ubuntu yakkety/restricted Translation-en [2,996 B]
Get:33 http://archive.ubuntu.com/ubuntu yakkety/restricted amd64 DEP-11 Metadata [187 B]
Get:34 http://archive.ubuntu.com/ubuntu yakkety/universe i386 Packages [7,712 kB]
Get:35 http://archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages [7,729 kB]
Get:36 http://archive.ubuntu.com/ubuntu yakkety/universe Translation-en [4,484 kB]
Get:37 http://archive.ubuntu.com/ubuntu yakkety/universe amd64 DEP-11 Metadata [2,669 kB]
Get:38 http://archive.ubuntu.com/ubuntu yakkety/universe DEP-11 64x64 Icons [7,194 kB]
Get:39 http://archive.ubuntu.com/ubuntu yakkety/multiverse i386 Packages [141 kB]
Get:40 http://archive.ubuntu.com/ubuntu yakkety/multiverse amd64 Packages [146 kB]
Get:41 http://archive.ubuntu.com/ubuntu yakkety/multiverse Translation-en [108 kB]
Get:42 http://archive.ubuntu.com/ubuntu yakkety/multiverse amd64 DEP-11 Metadata [47.6 kB]
Get:43 http://archive.ubuntu.com/ubuntu yakkety/multiverse DEP-11 64x64 Icons [246 kB]
Get:44 http://archive.ubuntu.com/ubuntu yakkety-updates/main amd64 Packages [182 kB]
Err:44 http://archive.ubuntu.com/ubuntu yakkety-updates/main amd64 Packages    
  Hash Sum mismatch
  Hashes of expected file:
   - Checksum-FileSize:181668 [weak]
   - SHA256:111a40d1d8f0a91b222eaa0f56e09975bef6959acc7ad1b4405a3e1e95ed356b
   - SHA1:d6f3bb8f7b2f3d8f38e36fcbb23b38099306ccaf [weak]
   - MD5Sum:cdf76ea88e73e32ba6b352ace8ec536c [weak]
  Hashes of received file:
   - SHA256:ac80c22f4cf78ad176eacb5f7b2d8baa1daac25310049b79635930cfbd4d9c90
   - SHA1:75571e7145e119faa67ff1986063ffa0db1a46a7 [weak]
   - MD5Sum:df6d22c07a398f98fab4ab7fb6410a2b [weak]
   - Checksum-FileSize:181668 [weak]
  Last modification reported: Sat, 11 Feb 2017 07:57:17 +0000
  Release file created at: Sat, 11 Feb 2017 07:57:11 +0000
Get:45 http://archive.ubuntu.com/ubuntu yakkety-updates/main i386 Packages [179 kB]
Err:45 http://archive.ubuntu.com/ubuntu yakkety-updates/main i386 Packages     
  
Get:46 http://archive.ubuntu.com/ubuntu yakkety-updates/main Translation-en [80.4 kB]
Get:47 http://archive.ubuntu.com/ubuntu yakkety-updates/main amd64 DEP-11 Metadata [114 kB]
Get:48 http://archive.ubuntu.com/ubuntu yakkety-updates/main DEP-11 64x64 Icons [63.1 kB]
Get:49 http://archive.ubuntu.com/ubuntu yakkety-updates/restricted i386 Packages [5,196 B]
Get:50 http://archive.ubuntu.com/ubuntu yakkety-updates/restricted amd64 Packages [5,180 B]
Get:51 http://archive.ubuntu.com/ubuntu yakkety-updates/restricted Translation-en [1,880 B]
Get:52 http://archive.ubuntu.com/ubuntu yakkety-updates/restricted amd64 DEP-11 Metadata [185 B]
Get:53 http://archive.ubuntu.com/ubuntu yakkety-updates/universe i386 Packages [101 kB]
Get:54 http://archive.ubuntu.com/ubuntu yakkety-updates/universe amd64 Packages [103 kB]
Get:55 http://archive.ubuntu.com/ubuntu yakkety-backports/main i386 Packages [2,484 B]
Get:56 http://archive.ubuntu.com/ubuntu yakkety-backports/main amd64 Packages [2,484 B]
Get:57 http://archive.ubuntu.com/ubuntu yakkety-backports/main Translation-en [1,608 B]
Get:58 http://archive.ubuntu.com/ubuntu yakkety-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:59 http://archive.ubuntu.com/ubuntu yakkety-backports/main DEP-11 64x64 Icons [29 B]
Get:60 http://archive.ubuntu.com/ubuntu yakkety-backports/restricted amd64 DEP-11 Metadata [187 B]
Get:61 http://archive.ubuntu.com/ubuntu yakkety-backports/universe i386 Packages [1,564 B]
Get:62 http://archive.ubuntu.com/ubuntu yakkety-backports/universe amd64 Packages [1,560 B]
Get:63 http://archive.ubuntu.com/ubuntu yakkety-backports/universe Translation-en [632 B]
Get:64 http://archive.ubuntu.com/ubuntu yakkety-backports/universe amd64 DEP-11 Metadata [216 B]
Get:65 http://archive.ubuntu.com/ubuntu yakkety-backports/universe DEP-11 64x64 Icons [29 B]
Get:66 http://archive.ubuntu.com/ubuntu yakkety-backports/multiverse amd64 DEP-11 Metadata [216 B]
Get:67 http://archive.ubuntu.com/ubuntu yakkety-backports/multiverse DEP-11 64x64 Icons [29 B]
Get:68 http://archive.ubuntu.com/ubuntu yakkety-security/main i386 Packages [89.1 kB]
Get:69 http://archive.ubuntu.com/ubuntu yakkety-security/main amd64 Packages [91.0 kB]
Get:70 http://archive.ubuntu.com/ubuntu yakkety-security/main Translation-en [40.8 kB]
Get:71 http://archive.ubuntu.com/ubuntu yakkety-security/main amd64 DEP-11 Metadata [8,264 B]
Get:72 http://archive.ubuntu.com/ubuntu yakkety-security/main DEP-11 64x64 Icons [10.1 kB]
Get:73 http://archive.ubuntu.com/ubuntu yakkety-security/restricted amd64 Packages [5,180 B]
Get:74 http://archive.ubuntu.com/ubuntu yakkety-security/restricted i386 Packages [5,196 B]
Get:75 http://archive.ubuntu.com/ubuntu yakkety-security/restricted Translation-en [1,880 B]
Get:76 http://archive.ubuntu.com/ubuntu yakkety-security/restricted amd64 DEP-11 Metadata [186 B]
Get:77 http://archive.ubuntu.com/ubuntu yakkety-security/universe amd64 Packages [37.4 kB]
Get:78 http://archive.ubuntu.com/ubuntu yakkety-security/universe i386 Packages [35.1 kB]
Get:79 http://archive.ubuntu.com/ubuntu yakkety-security/universe Translation-en [24.0 kB]
Get:80 http://archive.ubuntu.com/ubuntu yakkety-security/universe amd64 DEP-11 Metadata [9,736 B]
Get:81 http://archive.ubuntu.com/ubuntu yakkety-security/universe DEP-11 64x64 Icons [6,224 B]
Get:82 http://archive.ubuntu.com/ubuntu yakkety-security/multiverse amd64 Packages [2,840 B]
Get:83 http://archive.ubuntu.com/ubuntu yakkety-security/multiverse i386 Packages [3,004 B]
Get:84 http://archive.ubuntu.com/ubuntu yakkety-security/multiverse Translation-en [1,268 B]
Get:85 http://archive.ubuntu.com/ubuntu yakkety-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:86 http://archive.ubuntu.com/ubuntu yakkety-security/multiverse DEP-11 64x64 Icons [29 B]
Fetched 36.5 MB in 1min 45s (345 kB/s)                                         
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/main/binary-amd64/by-hash/SHA256/111a40d1d8f0a91b222eaa0f56e09975bef6959acc7ad1b4405a3e1e95ed356b  Hash Sum mismatch
   Hashes of expected file:
    - Checksum-FileSize:181668 [weak]
    - SHA256:111a40d1d8f0a91b222eaa0f56e09975bef6959acc7ad1b4405a3e1e95ed356b
    - SHA1:d6f3bb8f7b2f3d8f38e36fcbb23b38099306ccaf [weak]
    - MD5Sum:cdf76ea88e73e32ba6b352ace8ec536c [weak]
   Hashes of received file:
    - SHA256:ac80c22f4cf78ad176eacb5f7b2d8baa1daac25310049b79635930cfbd4d9c90
    - SHA1:75571e7145e119faa67ff1986063ffa0db1a46a7 [weak]
    - MD5Sum:df6d22c07a398f98fab4ab7fb6410a2b [weak]
    - Checksum-FileSize:181668 [weak]
   Last modification reported: Sat, 11 Feb 2017 07:57:17 +0000
   Release file created at: Sat, 11 Feb 2017 07:57:11 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/main/binary-i386/by-hash/SHA256/dac4f1c1a25048c0efb3d30021a48905e819956c1b52989696ca384c451a4dc2  
E: Some index files failed to download. They have been ignored, or old ones used instead. 
```

---

### Post by Perfect Storm on 2017-02-11
Maybe try switch sourcelist server:
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

Just don't pick 3rd Parties Repos

---

### Post by jsc12345 on 2017-02-11
What am I supposed to do with this?

---

### Post by howefield on 2017-02-11
> **jsc12345 said:**
> Didn't work. It now outputs:

Au contraire, it did work in as much as removing the non existent repositories stopped the not found errors.

The remaining hash mismatch errors would usually be cleared with Artificial Intelligences advice, can you confirm whether or not you have run his suggested commands before suggesting anything else ?

PS. The repogen website suggested by A.I. creates fresh sources.lists which you can use to replace your current list.

Here is a copy of my sources.list (default yakkety with Partners repo enabled and for the gb servers)

```
# deb cdrom:[Ubuntu 16.10 _Yakkety Yak_ - Release amd64 (20161012.2)]/ yakkety main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ yakkety main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ yakkety main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ yakkety universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ yakkety universe
deb http://gb.archive.ubuntu.com/ubuntu/ yakkety-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ yakkety-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ yakkety multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ yakkety multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu yakkety partner
# deb-src http://archive.canonical.com/ubuntu yakkety partner

deb http://security.ubuntu.com/ubuntu yakkety-security main restricted
# deb-src http://security.ubuntu.com/ubuntu yakkety-security main restricted
deb http://security.ubuntu.com/ubuntu yakkety-security universe
# deb-src http://security.ubuntu.com/ubuntu yakkety-security universe
deb http://security.ubuntu.com/ubuntu yakkety-security multiverse
# deb-src http://security.ubuntu.com/ubuntu yakkety-security multiverse
```

---

### Post by jsc12345 on 2017-02-11
Okay, I'm pretty sure that worked. Just to make sure, the output is: ```

Hit:1 http://za.archive.ubuntu.com/ubuntu yakkety InRelease
Hit:2 http://za.archive.ubuntu.com/ubuntu yakkety-security InRelease           
Hit:3 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu yakkety InRelease    
Hit:4 http://za.archive.ubuntu.com/ubuntu yakkety-updates InRelease            
Get:5 http://za.archive.ubuntu.com/ubuntu yakkety-proposed InRelease [102 kB]  
Hit:6 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu yakkety InRelease         
Ign:7 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:8 http://archive.canonical.com/ubuntu yakkety InRelease [11.5 kB]          
Hit:9 http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety InRelease        
Hit:10 http://dl.google.com/linux/chrome/deb stable Release                    
Hit:11 http://za.archive.ubuntu.com/ubuntu yakkety-backports InRelease   
Hit:12 http://ppa.launchpad.net/wine/wine-builds/ubuntu yakkety InRelease      
Get:13 http://za.archive.ubuntu.com/ubuntu yakkety/restricted Sources [5,376 B]
Get:14 http://za.archive.ubuntu.com/ubuntu yakkety/multiverse Sources [181 kB] 
Get:15 http://archive.canonical.com/ubuntu yakkety/partner Sources [2,252 B]   
Get:17 http://archive.canonical.com/ubuntu yakkety/partner amd64 Packages [2,468 B]
Get:18 http://archive.canonical.com/ubuntu yakkety/partner i386 Packages [2,760 B]
Get:19 http://archive.canonical.com/ubuntu yakkety/partner Translation-en [1,352 B]
Get:20 http://za.archive.ubuntu.com/ubuntu yakkety/main Sources [903 kB]       
Get:21 http://za.archive.ubuntu.com/ubuntu yakkety/universe Sources [8,044 kB]
Get:22 http://za.archive.ubuntu.com/ubuntu yakkety-security/universe Sources [11.8 kB]
Get:23 http://za.archive.ubuntu.com/ubuntu yakkety-security/multiverse Sources [1,144 B]
Get:24 http://za.archive.ubuntu.com/ubuntu yakkety-security/restricted Sources [1,924 B]
Get:25 http://za.archive.ubuntu.com/ubuntu yakkety-security/main Sources [29.2 kB]
Get:26 http://za.archive.ubuntu.com/ubuntu yakkety-updates/main Sources [71.7 kB]
Get:27 http://za.archive.ubuntu.com/ubuntu yakkety-updates/universe Sources [36.5 kB]
Get:28 http://za.archive.ubuntu.com/ubuntu yakkety-updates/restricted Sources [1,924 B]
Get:29 http://za.archive.ubuntu.com/ubuntu yakkety-updates/multiverse Sources [2,476 B]
Get:30 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/main Sources [20.1 kB]
Get:31 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/universe Sources [8,948 B]
Get:32 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/restricted Sources [780 B]
Get:33 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/main amd64 Packages [40.7 kB]
Get:34 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/main i386 Packages [39.5 kB]
Get:35 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/main Translation-en [20.6 kB]
Get:36 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/main amd64 DEP-11 Metadata [13.5 kB]
Get:37 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/main DEP-11 64x64 Icons [17.2 kB]
Get:38 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/restricted i386 Packages [760 B]
Get:39 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/restricted amd64 Packages [760 B]
Get:40 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/restricted Translation-en [304 B]
Get:41 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/restricted amd64 DEP-11 Metadata [201 B]
Get:42 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/universe i386 Packages [22.1 kB]
Get:43 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/universe amd64 Packages [20.9 kB]
Get:44 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/universe Translation-en [11.8 kB]
Get:45 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/universe amd64 DEP-11 Metadata [11.1 kB]
Get:46 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/universe DEP-11 64x64 Icons [15.7 kB]
Get:47 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/multiverse amd64 DEP-11 Metadata [212 B]
Get:48 http://za.archive.ubuntu.com/ubuntu yakkety-proposed/multiverse DEP-11 64x64 Icons [29 B]
Get:49 http://za.archive.ubuntu.com/ubuntu yakkety-backports/universe Sources [1,012 B]
Get:50 http://za.archive.ubuntu.com/ubuntu yakkety-backports/main Sources [1,908 B]
Fetched 9,661 kB in 27s (356 kB/s)                                             
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_ZA) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_ZA) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:33 and /etc/apt/sources.list.d/google-chrome.list:3

```. 
I added the Google Chrome repo because I use it as my primary browser. If that output was good, I think my problem is solved! Thanks all!

---

### Post by howefield on 2017-02-11
> **jsc12345 said:**
> I added the Google Chrome repo because I use it as my primary browser. If that output was good, I think my problem is solved! Thanks all!

Cool, that looks good except for the fact that you shouldn't have the "*is configured multiple times in*" errors, although they may not be fatal.

If you load up the Software & Updates application, do you see multiple entries for the Chrome repository in the "*Other Software*" tab ?

---

