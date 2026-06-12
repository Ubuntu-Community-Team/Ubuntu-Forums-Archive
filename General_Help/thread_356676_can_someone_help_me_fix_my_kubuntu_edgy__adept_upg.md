---
title: "can someone help me fix my kubuntu edgy  adept upgrade problem?"
date: 2007-02-08
forum: General Help
---

### Post by maddbaron on 2007-02-08
For the past few days I have not been able to update completely when I try to use adept, I tried konsole and it said 7 programs are being left back. I ran sudo apt-get update and it went normally til the end and I got this:
> W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems


When I ran sudo apt-get upgrade I got this:
> maddbaron@baronworks:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  audacity bmp-mp4 k3b libk3b2 linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

Can someone please tell me what steps to take to fix this please.

---

### Post by barney_1 on 2007-02-08
Ok, I'll tell you how to fix it, but also how I figured out how to fix it so you'll know next time.

This error:
```
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
```

Is showing up because you don't have the authentication key to say "hey, this is a trusted repository and it's safe to install these programs".  You need to add this key.

So, I went to that web address ([http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com)) and clicked where is says "Repository How-To".  The first thing on that page tells you how to save their gpg key:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Once that is done you just need to update your sources:
```
sudo apt-get update
```

---

### Post by maddbaron on 2007-02-08
> **barney_1 said:**
> Ok, I'll tell you how to fix it, but also how I figured out how to fix it so you'll know next time.

This error:
```
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
```

Is showing up because you don't have the authentication key to say "hey, this is a trusted repository and it's safe to install these programs".  You need to add this key.

So, I went to that web address ([http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com)) and clicked where is says "Repository How-To".  The first thing on that page tells you how to save their gpg key:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Once that is done you just need to update your sources:
```
sudo apt-get update
```

Thanks, it fixed my sources but I am still getting 7 being held back
I attempted to install one by one and was told I have broken packages.
> maddbaron@baronworks:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  audacity bmp-mp4 k3b libk3b2 linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
maddbaron@baronworks:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.17-11-generic but it is not installable
E: Broken packages

Is there a way to fix that?
This is frustrating....

---

### Post by maddbaron on 2007-02-08
got pushed back, still looking for help please

---

### Post by bollix47 on 2007-02-08
[http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---

### Post by maddbaron on 2007-02-08
I had problems installing
> audacity bmp-mp4 k3b libk3b2

before the kernal image problem. Does this dependency issue mean I won't be able to update 

> audacity bmp-mp4 k3b libk3b2

until its fixed?

---

