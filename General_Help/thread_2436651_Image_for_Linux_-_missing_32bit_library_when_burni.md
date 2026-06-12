---
title: "Image for Linux - missing 32bit library when burning CD"
date: 2020-02-10
forum: General Help
---

### Post by sussexlad on 2020-02-10
Hi

I'm now using Ubunto 18.04.4 LTS, having moved from Centos.

I've used  IFL 3.31 64bit for a long time now. There's a slightly later version available but to create the image to burn to CD it requites the 32bit library  libncursesw5

I can't find anything directly relating to this library.  How can I go about installing it?

TIA Andy

---

### Post by GhX6GZMB on 2020-02-10
what's IFL?

---

### Post by deadflowr on 2020-02-10
libncursesw5:i386 is the 32-bit version.
It's definitely available on 18.04.

libncursesw5, is in fact, a required package on Ubuntu.
So the 64-bit version is already installed.

---

### Post by sussexlad on 2020-02-10
> **ml9104 said:**
> what's IFL?

Image for Linux  - as per title

---

### Post by sussexlad on 2020-02-10
> **deadflowr said:**
> libncursesw5:i386 is the 32-bit version.
It's definitely available on 18.04.

libncursesw5, is in fact, a required package on Ubuntu.
So the 64-bit version is already installed.

It's the 32-bit version I need. How do you install it?

Thanks

---

### Post by deadflowr on 2020-02-10
From the command line
```
sudo apt update
sudo apt full-upgrade
sudo apt install libncursesw5:i386
```

The first two commands should always be run in order to assure the system is fully-up-to-date.
But to install the package you only need to run the last one.

If you want to install using gui, then install and use the synaptic package manager (available in the Software store program)

---

### Post by sussexlad on 2020-02-11
Many thanks for the answer and explanation.

---

### Post by sussexlad on 2020-02-11
More details to get IFL working on 64 bit machines, here.

[https://www.terabyteunlimited.com/kb/article.php?id=566](https://www.terabyteunlimited.com/kb/article.php?id=566)

---

### Post by mastablasta on 2020-02-11
if you don't need to create images from mounted drives, then you can just use clonezilla.

i would image only system backup. otherwise for data backup they should be scheduled and done regularly, so rather than to image them i would send them off to a networked drive or external drive (as i set it up at work).

currently only the so called static data (photos & videos) is important to me.

---

### Post by sussexlad on 2020-02-12
I take an image to an external HD of my one and only SSD drive, if I make a fairly significant change or about once a month.
I am so confident in IFL, even if I make a minor slip-up, I will do a full restore to get back to the beginning state.
I also copy all regularly changed files to the same HD, different partition, on a daily basis.
An image is staggeringly fast since they updated the software and I just prefer to keep everything local !

---

### Post by mastablasta on 2020-02-12
i guess it depends how many things are changed daily and how static the data is.

if you have plenty of changes done and if SSD suddenly fails or is taken over by malware, then you will loose all data since last backup ( which could be previous month). if data is quite static this is not really an issue. 

by the way since you like backing up to same disk, have a look at BRFS. that file system creates snapshots and you can easily restore from them.

if you will ever go down the automated backup i found that Areca and Duplicati work quite well. i use Areca, since it is easy to browse the individual files in a GUI. it will store backups locally, external drive or network (LAN or outside, but i suggest encryption and keys for that data). with Areca i like that the setup is run through gui but then script is ran in command line (in the background)

another good command line utility is rdiff-backup. but that one is CLI only.

in any case the idea is to have versions of files so that if maleare takes over or if disk stops working you can easily restore and continue with work. possibly where you left of that day. with HDD disk usually has signs that it will give up (noise or otherwise), but with SSD, i am not sur ehow one could see other than doing S.M.A.R.T. checks.

---

