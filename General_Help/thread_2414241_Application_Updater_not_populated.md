---
title: "Application Updater not populated"
date: 2019-03-07
forum: General Help
---

### Post by flyinghigh2 on 2019-03-07
Hi my software updater only has a few softwares available, I think they are the editors pick

there used to be several categories to chose from

any advice?

---

### Post by deadflowr on 2019-03-07
You mean Software.
software updater will only ever show software that can be updated.
That will change indefinitely depending on what needs to be updated.

Have you added any new sources lately?
Please run this in a terminal and post back the results
```
sudo apt update
```

That should be a simple starting point.

---

### Post by flyinghigh2 on 2019-03-07
hi i noticed this problem a while ago but only just have gotten around to posting about it, so no new packages installed as they havent been showing up in the software centre

here is the code you were asking


```

Get:1 http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu xenial InRelease [17.6 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]     
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]    
Hit:5 http://repo.steampowered.com/steam precise InRelease                     
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]  
Get:7 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [102 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main Sources [331 kB] 
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67.9 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [67.1 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [428 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [250 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [920 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [373 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [116 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [173 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:18 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [804 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [318 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [237 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [737 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [675 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [252 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [355 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,964 B]
Get:26 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:28 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5,104 B]
Fetched 6,580 kB in 17s (387 kB/s)  

```

---

### Post by flyinghigh2 on 2019-03-14
Oh- Well ; It seems to be working again!

thanks

---

### Post by flyinghigh2 on 2019-03-14
How do I mark this thread as solved!?

---

### Post by Impavidus on 2019-03-14
Click "Thread tools" (near top of the page) -> "Mark as solved".

---

