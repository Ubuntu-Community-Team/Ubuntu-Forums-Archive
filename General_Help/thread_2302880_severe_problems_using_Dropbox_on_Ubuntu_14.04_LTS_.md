---
title: "severe problems using Dropbox on Ubuntu 14.04 LTS on a brand-new computer"
date: 2015-11-14
forum: General Help
---

### Post by schabert on 2015-11-14
I've been using Ubuntu LTS 14.04 for some time now and I had a very pleasant user experience up until this point in time. However, it seems that the version of Dropbox one gets through the Ubuntu software center simply doesn't work in a reasonable way on my brand-new Dell Precision M6800 and I can't sync important files that I need for work in a reasonable way at all. Maybe I am expecting too much and should just make an image of my Dropbox on an external hard drive and transfer my data over that way. But I can't shake the feeling that something is seriously off with my Dropbox and I would like some feedback from the community.

I just did a speed test pinging an East Coast server as recommended and found that my download speed is about 65 MB/s and my upload speed about 20 MB/s. I therefore set up my Dropbox by limiting download speed to 30 MB/s and upload speed to 10 MB/s. I also disabled LAN sync and set "no proxy" if that matters. At the moment, dropbox status says:

Syncing (2,058,544 files remaining, 1 min left)                                                                                                                  
Downloading 2,058,544 files (15.0 KB/sec, 1 min left)

This is quite strange for a couple reasons. I have been trying to sync my ~150 GB of data for more than a week now (I pay for 1 TB of data storage but, predictably, Dropbox customer service just ignored my complaint message) and some of my lighter-weight files have successfully downloaded so the program is doing something. However, it is completely absurd to say that I only have 1 minute of download time left. Since I have been downloading for so long, 15 KB/s might be accurate but it is quite ridiculous since I should be perfectly capable of download speeds literally orders of magnitude faster than what I'm getting right now.

Has anyone else experienced behavior like this or have any idea how to make things better?

---

### Post by raketax on 2015-11-16
I suggest removing the Software Center version of Dropbox, and downloading the .deb file directly from the Dropbox website. Unfortunately the Dropbox version found in the repositories is not always the best choice to use, the website one however should be the most up to date, hopefully solving your problem.

---

### Post by schabert on 2015-11-18
Thank you very much for your response. I'll try this out first chance I get.

---

### Post by Bucky Ball on 2015-11-19
> **raketax said:**
> Unfortunately the Dropbox version found in the repositories is not always the best choice to use, the website one however should be the most up to date, hopefully solving your problem.

If you don't mind me asking, what are you basing this on?

---

### Post by vasa1 on 2015-11-19
> **Bucky Ball said:**
> If you don't mind me asking, what are you basing this on?
I have dropbox direct from the site. It's version 3.10.11 and is autoupdated (not via apt-get).

IIRC, the software center offers nautilus-dropbox:```
Description-en: Dropbox integration for Nautilus
 Nautilus Dropbox is an extension that integrates the Dropbox web service with
 your GNOME Desktop.
 .
 Installing this package will download the proprietary dropbox binary
 from dropbox.com.
```
I don't have nautilus or a GNOME desktop but I'd be interested to know which version people have, if they've gone the nautilus-dropbox route.

---

### Post by raketax on 2015-11-19
> **Bucky Ball said:**
> If you don't mind me asking, what are you basing this on?

Mostly past experience. I had a lot of trouble with this topic back in the days after the Ubuntu 14.04 release. Honestly I am not sure if at the moment there is an actual version number difference, but while not for me personally, this advice did help people around me in the recent past. I do realise it is not a proper root cause description, but I do believe the solution itself can help.

---

### Post by schabert on 2016-01-20
Thank you all for your responses. It took me quite some time to get to a good stopping point with my work so that I could afford to tinker a bit but now I'm ready to try once more to get Dropbox working. I downloaded the source of the installer on Dropbox's website, built it, and then did a fresh install of the program. Unfortunately, the problem didn't go away. Also, in the mean time, I heard back from Dropbox support. They suggested removing all sim-linked folders and downloading only small chunks at a time using selective sync. I tried these steps and found no difference at all. I've attached a screen shot to give you some idea what I'm currently looking at. Any other ideas? I'm at my wit's end and am considering ditching Dropbox altogether.

---

### Post by Vladlenin5000 on 2016-01-20
I would remove the download/upload limits altogether. It's the most likely culprit.
And why disable LAN sync? It's quite useful if you have another Dropbox instance in your home network and if you don't it does absolutely nothing... So, why disable it?

---

### Post by schabert on 2016-01-23
> **Vladlenin5000 said:**
> 
And why disable LAN sync? It's quite useful if you have another Dropbox instance in your home network and if you don't it does absolutely nothing... So, why disable it?

Well, this was advice I got by randomly googling and, until you just explained it, I didn't know what LAN sync was supposed to do. The good news is, LAN sync actually worked wonders for me and now my problem seems to be effectively solved. Thanks for suggesting that!

---

### Post by schabert on 2016-01-23
By the way, Dropbox support basically says that they can't guarantee acceptable performance if I have more than 300,000 files. I have way more than that and am only at ~15% of my total storage capacity. How they expect me to use a whole terabyte of storage and not have more than 300,000 files is beyond me.

---

