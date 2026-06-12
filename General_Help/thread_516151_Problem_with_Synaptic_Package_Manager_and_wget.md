---
title: "Problem with Synaptic Package Manager and wget"
date: 2007-08-02
forum: General Help
---

### Post by bars123 on 2007-08-02
Hi,

  I am running Feisty Fawn and everything worked perfectly till now (Synaptic and wget). However, I am facing problems now with both of these applications.

**Problem with synaptic:**

This is my sourcelist:

```
deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://packages.medibuntu.org/ feisty free non-free
deb http://archive.canonical.com/ubuntu feisty-commercial main

# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```

Now, I am unable to install packages using either Synaptic or the terminal. I am behind a proxy and I am able to access the internet and everything(using the same proxy settings in Synaptic and Network proxy in system-->Preferences)

I am able to download the package via the browser but not through synaptic or terminal :confused: i tried using different servers (main servers) for the packages.

Using Synaptic i am getting this error:
> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


**The problem with wget:**

I am getting this error if i am using the wget command for ex:

if i use this in the terminal:  wget [http://easylinux.info/uploads/scanModem.gz](http://easylinux.info/uploads/scanModem.gz)
i am getting this error: **Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.**

Please help me.

---

### Post by bars123 on 2007-08-02
No one :(

---

### Post by bars123 on 2007-08-03
can someone help me :( this problem is making me mad.. i am able to do everything except downloading packages:confused:

Even this message i am posting using ubuntu..don't know what the problem..i need to install quite a few packages 

Thank you

---

### Post by kn0x_d3m3ntor on 2007-08-09
add the following to the end of your /etc/bash.bashrc

[HTML]export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/[/HTML]

that should do the trick
good luck

kn0x

---

