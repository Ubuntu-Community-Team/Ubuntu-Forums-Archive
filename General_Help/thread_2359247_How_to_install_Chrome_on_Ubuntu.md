---
title: "How to install Chrome on Ubuntu"
date: 2017-04-21
forum: General Help
---

### Post by bluntc0ncussi0n2 on 2017-04-21
I'm trying to install Chrome on Ubuntu that I just installed on my laptop which is a Lenovo Y50. For some reason it when I install it in the app store nothing happens. I'm running the 64-bit version of the software. Thanks!

---

### Post by wildmanne39 on 2017-04-21
*Thread moved to **General Help**.*

What version of Ubuntu are you using?

---

### Post by monkeybrain20122 on 2017-04-22
There is a bug in gnome software center. [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573408](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573408) (it says that fix has been release, but it still doesn't work on my fully up to date 17.04, others in the comments said the same)

So forget about the buggy gnome software center, Instead use gdebi for one click installation of .deb packages, which is better than the software center anyway
Install gdebi
```
sudo apt-get install gdebi
```

Now right click the .deb you downloaded, choose properties from the menu and in the "open with" tab choose GDebi Package Installer as the default. Then close the dialogue window. Now click the .deb and gdebi will install it. In the future if you try to install any third party .deb, just click it and gdebi will do the job.

---

### Post by howefield on 2017-04-22
Alternatively, without installing extra packages you could just use apt if using Ubuntu 16.04 or later.

```
sudo apt install -s ~/Downloads/Packages/google-chrome-stable_current_amd64.deb 
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'google-chrome-stable' instead of '/home/hugh/Downloads/Packages/google-chrome-stable_current_amd64.deb'
The following additional packages will be installed:
  libpango1.0-0 libpangox-1.0-0
The following NEW packages will be installed
  google-chrome-stable libpango1.0-0 libpangox-1.0-0
0 to upgrade, 3 to newly install, 0 to remove and 13 not to upgrade.
Inst libpangox-1.0-0 (0.0.2-5 Ubuntu:17.04/zesty [amd64])
Inst libpango1.0-0 (1.40.4-1 Ubuntu:17.04/zesty [amd64])
Inst google-chrome-stable (57.0.2987.133-1 local-deb [amd64])
Conf libpangox-1.0-0 (0.0.2-5 Ubuntu:17.04/zesty [amd64])
Conf libpango1.0-0 (1.40.4-1 Ubuntu:17.04/zesty [amd64])
Conf google-chrome-stable (57.0.2987.133-1 local-deb [amd64])
```

Using the -s switch just for illustration.

---

### Post by bluntc0ncussi0n2 on 2017-04-22
I'm using 17.04

---

### Post by monkeybrain20122 on 2017-04-22
> **howefield said:**
> Alternatively, without installing extra packages you could just use apt if using Ubuntu 16.04 or later.
....

Using the -s switch just for illustration.

Good to know about this. But this method won't work without saving the .deb first, or with apturl.

---

### Post by vasa1 on 2017-04-22
> **monkeybrain20122 said:**
> Good to know about this. But this method won't work without saving the .deb first, ...I think that a saved .deb is implied and that it is in the ~/Downloads folder.```
sudo apt install -s ~/Downloads/Packages/google-chrome-stable_current_amd64.deb
```from the first line in the code of post #4.

---

### Post by howefield on 2017-04-23
> **monkeybrain20122 said:**
> Good to know about this. But this method won't work without saving the .deb first, or with apturl.

Of course, you do need the deb file before you can install it whether you use gdebi or apt for the installation process. For the sake of completeness, I would use..

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -P ~/Download/Packages/
```

to get the deb file. The -P option with the path to put it straight into the folder of my choice. Of course you can simply download graphically using a browser.

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -P ~/Download/Packages/
--2017-04-23 07:34:02--  https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
Resolving dl.google.com (dl.google.com)... 2a00:1450:4009:812::200e, 216.58.206.78
Connecting to dl.google.com (dl.google.com)|2a00:1450:4009:812::200e|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 56684626 (54M) [application/x-debian-package]
Saving to: ‘/home/hugh/Download/Packages/google-chrome-stable_current_amd64.deb’

google-chrome-stable_current_amd64 100%[================================================================>]  54.06M  3.13MB/s    in 19s     

2017-04-23 07:34:21 (2.89 MB/s) - ‘/home/hugh/Download/Packages/google-chrome-stable_current_amd64.deb’ saved [56684626/56684626]
```

and 

```
sudo apt install ~/Downloads/Packages/google-chrome-stable_current_amd64.deb
``` 

to install it.

Gdebi is very good, it is the method I used before apt got the ability to install local .deb packages. I only offer it as an alternative due to it being included in the default Ubuntu install. Ye pays yer money and ....

---

### Post by bluntc0ncussi0n2 on 2017-05-15
That solution worked! Thanks!

---

