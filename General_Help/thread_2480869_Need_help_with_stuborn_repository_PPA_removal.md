---
title: "Need help with stuborn repository PPA removal"
date: 2022-11-12
forum: General Help
---

### Post by DVD-R on 2022-11-12
Hello,
I'm running ubuntu 16.04 - (linux lite version 3.4)

I need to clean out a repository PPA that I added by mistake

The URL is: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease
The error for this is:  "The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F"


I've gone into the etc/apt/sources.list and deleted it - and then performed "sudo apt update"
But it is still appearing as an error during every "sudo apt update"

Apparently deleting it from the sources.list file is not sufficient to remove it
I then tried to remove it using synaptic - but synaptic does not show it.
That probably means that Synaptic is reading the sources.list file

I then tried the command:
sudo add-apt-repository --remove ppa: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease

And this returns an error - need a single repository as argument

I'm stumpted!
Can anyone help!
Sincere thanks

---

### Post by mIk3_08 on 2022-11-12
> **DVD-R said:**
> Hello,
I'm running ubuntu 16.04 - (linux lite version 3.4)

I need to clean out a repository PPA that I added by mistake

The URL is: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease
The error for this is:  "The following signatures couldn't be verified  because the public key is not available: NO_PUBKEY 76F1A20FF987672F"


I've gone into the etc/apt/sources.list and deleted it - and then performed "sudo apt update"
But it is still appearing as an error during every "sudo apt update"

Apparently deleting it from the sources.list file is not sufficient to remove it
I then tried to remove it using synaptic - but synaptic does not show it.
That probably means that Synaptic is reading the sources.list file

I then tried the command:
sudo add-apt-repository --remove ppa: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease

And this returns an error - need a single repository as argument

I'm stumpted!
Can anyone help!
Sincere thanks
Just run the following command below to add the following key for the repo. 
if  you want to remove the link repo just find it in the source list the  just add "#" to the following link. sample: Regards and cheers
```
#[https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu)
```
Just add the following key, 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <PUBKEY>
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 76F1A20FF987672F
```

---

### Post by Bashing-om on 2022-11-12
DVD-R; Ouch !

The repository as you once knew it no longer exists. 
> 
Ubuntu 16.04 LTS (Xenial Xerus) was the 24th release of Ubuntu. !End-of-life was April 30th, 2021. Paid support 
               (ESM) is available.


May I suggest that you do a clean fresh install - the latest LTS release is 22.04; as will be much faster and the more reliable than a release-upgrade.

[INDENT][INDENT]all good things must end
[/INDENT][/INDENT]

---

### Post by mIk3_08 on 2022-11-12
> **DVD-R said:**
> Hello,
I'm running ubuntu 16.04 - (linux lite version 3.4)

Yeah. Bashing-om is right. 16.04 is now out of support.  Ended support just last year. Regards and cheers.

---

### Post by DVD-R on 2022-11-12
I figured it out
The offending files were located in a different folder within /etc/apt/sourses.list.d
deleting the offending files fixed the problem

---

### Post by mIk3_08 on 2022-11-12
> **DVD-R said:**
> I figured it out
The offending files were located in a different folder within /etc/apt/sourses.list.d
deleting the offending files fixed the problem

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

