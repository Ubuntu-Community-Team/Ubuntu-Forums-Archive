---
title: "Update NetworkManager to v1.4.6 (or higher) in Ubuntu MATE 16.04???"
date: 2017-10-08
forum: General Help
---

### Post by d0006 on 2017-10-08
VERSION="16.04.3 LTS (Xenial Xerus)"
NetworkManager v1.2.6-0 - This is the latest version available through Synaptic.

I want to update to a higher version of NetworkManager.
I tried to install NetworkManager v1.4.6, v1.6.4, and v1.8.2 from source but they all give this error:
```
libglib2.0-dev:
  Depends: libglib2.0-0 (=2.48.0-1ubuntu4) but 2.48.2-0ubuntu1 is to be installed
 Depends: libglib2.0-bin (= 2.48.0-1ubuntu4)
```
When I try to install libglib2.0-dev with Synaptic, it wants to uninstall many, many packages, including many core components.

Synaptic shows libglib2.0-0,  libglib2.0-bin, and libglib2.0-data are installed.

Is there any way to install a later version of NetworkManager?

I want to update NetworkManager because I can not get it to work with MAC Changer. I have tried several fixes but none work.
Thanks

---

### Post by mörgæs on 2017-10-08
If you want to try Networkmanager 1.4.4 then it comes as the default package in 17.04. I don't know what 17.10 brings. 

Running LTS means running packages which were in fashion one and a half year ago. If they work for you everything is good, if not then it's better to leave the LTS idea.

---

### Post by &amp;KyT$0P# on 2017-10-08
> **mörgæs said:**
> If you want to try Networkmanager 1.4.4 then ...
... [you can.]("https://ubuntuforums.org/showthread.php?t=2327441&p=13635258&viewfull=1#post13635258")

> **d0006 said:**
> ```
libglib2.0-dev:
  Depends: libglib2.0-0 (=2.48.0-1ubuntu4) but 2.48.2-0ubuntu1 is to be installed
 Depends: libglib2.0-bin (= 2.48.0-1ubuntu4)
```
You have outdated versions of libglib2.0-0 and libglib2.0-bin.  Please update your system by running this command.
```
sudo apt-get update && sudo apt-get dist-upgrade
```
If it fails, or if it does not update the libglib2.0 packages, please post its output here.

---

### Post by d0006 on 2017-10-08
Thanks very much for all replies!!!
I think I will try NetworkManager v1.4.4 first. If that does not work I will do a backup and dist-upgrade.
I consider myself moderately competent with Ubuntu but I like the idea of LTS versions.

Thanks again!

---

### Post by d0006 on 2017-10-17
Oy! 

```
foobar@foobar:~/Desktop$ gdebi ./network-manager_1.4.4-1ubuntu3_amd64.deb 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: libgnutls30 (>= 3.5.0)
```

libgnutls30 v3.4.10-4 is latest version available in Synaptic.

I will try dist-upgrade soon and post results.
Thanks

---

### Post by mörgæs on 2017-10-22
> **mörgæs said:**
> I don't know what 17.10 brings. 


Now I have tried it; the version is 1.8.2.

---

### Post by d0006 on 2018-01-23
Hello:
Well, I finally backed-up my system and tried some stuff:

I tried
```
sudo apt-get -dV --show-progress dist-upgrade
```
 and
```
sudo apt full-upgrade
```
Both commands gave the same result:
```
foo@bar:/var/cache/apt/archives$ sudo apt-get -sV --show-progress dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
   libclang-common-4.0-dev (1:4.0-1ubuntu1~16.04.2)
   libllvm4.0 (1:4.0-1ubuntu1~16.04.2)
   linux-headers-4.10.0-42 (4.10.0-42.46~16.04.1)
   linux-headers-4.10.0-42-generic (4.10.0-42.46~16.04.1)
   linux-image-4.10.0-40-generic (4.10.0-40.44~16.04.1)
   linux-image-4.10.0-42-generic (4.10.0-42.46~16.04.1)
   linux-image-extra-4.10.0-40-generic (4.10.0-40.44~16.04.1)
   linux-image-extra-4.10.0-42-generic (4.10.0-42.46~16.04.1)
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
   chromium-codecs-ffmpeg-extra (62.0.3202.94-0ubuntu0.16.04.1317 => 63.0.3239.84-0ubuntu0.16.04.1)
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst chromium-codecs-ffmpeg-extra [62.0.3202.94-0ubuntu0.16.04.1317] (63.0.3239.84-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
Conf chromium-codecs-ffmpeg-extra (63.0.3239.84-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-security, Ubuntu:16.04/xenial-updates [amd64])
```
That's it.
GDebi still says it can not install NetworkManager v1.4.4
```
Dependency is not satisfiable: libgnutls30 (>= 3.5.0)
```
Are there any other options?
Is there any way to get MACChanger to work with NetworkManager v1.2.6-0?

Thanks

---

### Post by mörgæs on 2018-01-24
Sorry, can't help you with 16.04.

---

### Post by d0006 on 2018-01-28
Thank you for your reply.  I do appreciate your efforts to help me.
I suppose the good news is that because of this bug in NetworkManager and the inability to update Ubuntu 16.04 I am learning how to write a Bash script!
Yeah, maybe kindergarten level for many users but it is new to me.

P.S. I read about the UEFI bug previously. Really kind of scary.  Install an update and brick your system!
Thanks again!

---

### Post by mörgæs on 2018-01-29
The UEFI bug is fixed. Just do a fresh install of 17.10.1 and not 17.10.0.

All other bug fixes released from october have also been incorporated into the .1 version making it a highly recommended option.

---

