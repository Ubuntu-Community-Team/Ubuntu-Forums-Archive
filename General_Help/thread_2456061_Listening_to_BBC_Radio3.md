---
title: "Listening to BBC Radio3"
date: 2021-01-03
forum: General Help
---

### Post by grey1beard on 2021-01-03
For several years I've been listening to BBC R3 on my 32bit laptop running 14.04, then 16.04, then 18.04.
Now I am setting up a clean install of 18.04LTS on a 64bit hp 15 notebook, and while the BBC news site works fine, and Radio3 loads all the schedules, etc., and seems OK, it wont play the programmes, popping up a window (see attached).
My firefox browser is up to date, as is the 'device', and just in case it was the current problem with Adobe flash, I ran the programme on my old laptop with no problems.
Any thoughts or advice welcome.

John

---

### Post by GhX6GZMB on 2021-01-03
I'd look in the browser settings. New install = new browser.

---

### Post by #&amp;thj^% on 2021-01-03
Works Here:
```
pacman -Qi pepper-flash
Name            : pepper-flash
Version         : 32.0.0.465-1
Description     : Adobe Flash Player PPAPI
Architecture    : x86_64
URL             : https://get.adobe.com/flashplayer/
Licenses        : custom  LGPL
Groups          : None
Provides        : None
Depends On      : gcc-libs
Optional Deps   : flashplugin: settings utility [installed]
Required By     : freshplayerplugin
Optional For    : chromium
Conflicts With  : None
Replaces        : None
Installed Size  : 21.27 MiB
Packager        : Evangelos Foutras <foutrelis@archlinux.org>
Build Date      : Tue 08 Dec 2020 12:14:14 MST
Install Date    : Wed 09 Dec 2020 10:04:45 MST
Install Reason  : Explicitly installed
Install Script  : Yes
Validated By    : Signature

```

---

### Post by The Cog on 2021-01-03
No such problem on Xubuntu 20.04. Firefox is version 84.0. I wonder if some fairly new feature is missing from 18.04.

---

### Post by #&amp;thj^% on 2021-01-03
> **The Cog said:**
> No such problem on Xubuntu 20.04. Firefox is version 84.0. I wonder if some fairly new feature is missing from 18.04.

That's a great suggestion, and answered here: [https://www.bbc.co.uk/iplayer/help/questions/computer-issues/flash](https://www.bbc.co.uk/iplayer/help/questions/computer-issues/flash)

---

### Post by grey1beard on 2021-01-03
I'm running the latest version - 84.0.
To other posters, I've tried 20.04, didn't like it and re-installed 18.04 as a clean install
John

---

### Post by grey1beard on 2021-01-03
Hi 1 fallen,

How do I get that Terminal code vis-a-vis my set up ?
John
EDIT Just googled pepper-flash, so I guess not what I have installed ?

---

### Post by grey1beard on 2021-01-03
I've tried using **apt list** in terminal, both laptops but don't know what the exact name should be. 
At the moment I can't get a result in either the old one, which still works, nor the new one.
Tried **apt list flash**, **apt list adobe** and **apt list adobe-flash** but nothing.

---

### Post by grey1beard on 2021-01-03
This is on the 32bit m/c - 

$ apt list flashplugin-installer -a
Listing... Done
flashplugin-installer/xenial-updates,xenial-security,now 32.0.0.465ubuntu0.16.04.1 i386 [installed]
flashplugin-installer/xenial 11.2.202.616ubuntu1 i386


and this on the 64bit m/c -

$ apt list flashplugin-installer -a
Listing... Done
flashplugin-installer/bionic-updates,bionic-security 32.0.0.465ubuntu0.18.04.1 amd64
flashplugin-installer/bionic 29.0.0.140ubuntu1 amd64

Is this any help in solving the problem?
Or do I need the BBC to issue(?) a new player for their Sounds channel ?

---

### Post by grey1beard on 2021-01-18
Reverted to 16.04, and this problem goes away !

---

