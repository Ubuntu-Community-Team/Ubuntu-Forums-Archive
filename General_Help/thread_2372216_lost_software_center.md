---
title: "lost software center"
date: 2017-09-22
forum: General Help
---

### Post by s9032g@comcast.net on 2017-09-22
I lost my software center and perhaps my repository list as well. How do I recover?

Based on online advice I have already tried the usual terminal commands apt-get update, upgrade, install software center etc etc. All I get back os a message  that software center has no installation candidate.

Tnakns

---

### Post by oldos2er on 2017-09-22
Which version of Ubuntu? Newer versions now have gnome-software; software-center is dead.

---

### Post by vasa1 on 2017-09-22
> **s9032g@comcast.net said:**
> I lost my software center and perhaps my repository list as well. How do I recover?

Based on online advice I have already tried the usual terminal commands apt-get update, upgrade, install software center etc etc. All I get back os a message  that software center has no installation candidate.

TnaknsPost the exact commands and the exact reponses.

---

### Post by s9032g@comcast.net on 2017-09-22
My distro is listed on the thread. Xubuntu 17.04

---

### Post by ajgreeny on 2017-09-22
Please answer the questions you have been asked or we are shooting in the dark trying to answer you.
Show us the output of ```
sudo apt update
sudo apt upgrade
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by s9032g@comcast.net on 2017-09-23
steven@steven-Latitude-E7240:~$ sudo apt update
[sudo] password for steven: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty InRelease                         
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease                
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates InRelease [89.2 kB] 
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security InRelease [89.2 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports InRelease [89.2 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 Packages [218 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main i386 Packages [214 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata [53.1 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons [32.3 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata [173 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons [230 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata [5,840 B]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata [12.8 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/main DEP-11 64x64 Icons [17.6 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata [21.1 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons [42.3 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 DEP-11 Metadata [208 B]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/universe amd64 DEP-11 Metadata [4,588 B]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/universe DEP-11 64x64 Icons [2,713 B]
Fetched 1,294 kB in 1s (1,094 kB/s)                      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
steven@steven-Latitude-E7240:~$ 

steven@steven-Latitude-E7240:~$ sudo apt upgrade
[sudo] password for steven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@steven-Latitude-E7240:~$ 

Sorry I can't figure out the code-tags. The "how to" that I see does not seem to apply to what I see on my screen.

Thanks for your patience.

---

### Post by s9032g@comcast.net on 2017-09-23
I just went on Synaptic and looked at "missing package recommendations". I found what was missing, installed, and am now ok. Yesterday I had done a search for my missing items with no result. Simple solutions are often best. One just needs to find them.

Thanks, Steve (no my ID here is not my email address

---

### Post by vasa1 on 2017-09-23
> **s9032g@comcast.net said:**
> ...
Sorry I can't figure out the code-tags. The "how to" that I see does not seem to apply to what I see on my screen. ...
When you start a new thread or make a post in an existing thread using "Reply With Quote" or "Adv Reply", you'll see an icon that looks like **#** above the posting area's text box. Single-click on it. Automatically, you'll see [noparse]```

```[/noparse] appear in the text area where the insertion cursor is located. Simply paste your content from the terminal between the opening [noparse]```
[/noparse] and closing [noparse]
```[/noparse] tags.

In case you use the "Quick Reply" option, the **#** icon will not appear: these options provide a minimal set of icons. In that case you can carefully type in the tags yourself or click on "Go Advanced" below the posting area's text box to make the **#** icon (and other icons) appear.

---

