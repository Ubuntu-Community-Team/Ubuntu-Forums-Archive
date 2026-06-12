---
title: "Transmission slow"
date: 2015-03-20
forum: General Help
---

### Post by pfeiffep on 2015-03-20
I'm a bit perplexed about the speed of using transmission to download. I decided to be a good little doobie and use it to download ubuntu-gnome-14.04.2-desktop-amd64.iso last night. 
Since I wasn't in any hurry I just walked away and went to bed. This morning I saw there was still ~ 2 hours remaining; downloading from 23 of 24 clients. 
I double checked the speed settings in transmission and found both upload and download set at unlimited. 
I  decided that something was wrong with this and just went to download directly while leaving the transmission download working. 
The direct download took less that 5 minutes, and the transmission was still working (~1.75 hours remaining). I killed the transmission download.

In theory bit torrent should be really fast, so I'm missing something here and I'd like to understand what to tweak!

---

### Post by sudodus on 2015-03-20
It might have been a temporary problem. For me getting iso files via torrent with Transmission is usually much faster than downloading via http. Maybe the computers, that you connected to, had low limits for uploading. Maybe they were far away. I don't think you need to tweak the settings from the standard, that comes with Transmission.

If someone has a good tweak, please chip in and tell us :-)

---

### Post by pfeiffep on 2015-03-20
Thank you for the response sudodus ... I'll attempt with maybe a more popular distribution such as Ubuntu 14.01.2 32 bit.

---

### Post by pfeiffep on 2015-03-20
OK, I really didn't like Ubuntu Gnome nearly as much as I like Gnome flashback so I tested by downloading Ubuntu 14.10

started torrent at 9:53 after it stabilized itreported 2 hours downloading from 44 of 50 peers ... at 9:58 only 63 MB had been downloaded
started direct at 9:54 stated 3 minutes to download ... at 9:58 it completed

My ISP is Verizon, I have 50 upload / 50 download FIOS.

---

### Post by sammiev on 2015-03-21
Just tried the same file and had 12 of 12 peers. It took me 22 min which matches most direct downloads for me.

This was the first time I tried and used transmission download.

---

### Post by pfeiffep on 2015-03-21
I wonder if Verizon has 'local US' caches of popular sites such as UK's Ubuntu, and transmission is using mostly individuals located in the UK. I certainly wouldn't expect transmission to equal a major ISP's caching.

---

### Post by SeijiSensei on 2015-03-21
I've found that torrenting doesn't really improve my download speeds for Ubuntu ISOs from [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/).  I don't know about other download sites, but a direct download of [http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/release/ubuntu-gnome-14.04-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/release/ubuntu-gnome-14.04-desktop-amd64.iso) on my FiOS 50/50 line is taking less than twenty minutes.

I tried using Transmission to download via torrent, but got the "torrent not authorized on this tracker" error just now.

---

