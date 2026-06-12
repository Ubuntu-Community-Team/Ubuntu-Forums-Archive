---
title: "cannot install pamusb"
date: 2015-11-16
forum: General Help
---

### Post by farhanali on 2015-11-16
Hi all

i dont know where to ask this. i googled around and found nothing similar.

I am on Wily and the Universe repository is active.

when i try to install libpam-usb and pamusb-tools i get the following;

```
user@Desktop:~$ sudo apt-get install libpam-usb pamusb-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libpam-usb is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  pamusb-common

Package pamusb-tools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  pamusb-common

E: Package 'libpam-usb' has no installation candidate
E: Package 'pamusb-tools' has no installation candidate
```

any help will be appreciated.

---

### Post by matt_symes on 2015-11-16
Hi

The error message is telling you that you need to install pamusb-common by the looks of it.

```
sudo apt-get install pamusb-common
```

Have you tried this ?

Kind regards

---

### Post by farhanali on 2015-11-16
yes its already installed

---

### Post by matt_symes on 2015-11-16
Hi

> **farhanali said:**
> yes its already installed

...and does it supply the binaries you need ?

You really need to supply far more information, such as what you are trying to achieve as a start, to be able to get any useful help.

Kind regards

---

### Post by farhanali on 2015-11-17
OK so some details...

i am trying to authenticate my login to my desktop with a usb stick. i have already done it on my laptop using instruction from [here]("http://linuxconfig.org/linux-authentication-login-with-usb-device")

On another laptop. I have achieved the same in virtualbox running debian VM with win7 as host.

however, with this desktop i am stuck at the first step. this is an old machine (amd64 3500+, with 1MB ram) thus i was trying lubuntu on it. over all the machine runs fine with lubuntu.

When lubuntu did not find libpam-usb and pamusb-tools i searched for the related files and strangely enough the file  **/etc/pamusb.conf ** was available. i change it along with  **/etc/pam.d/common-auth** manually but it did not work.

i also tried running 

```
sudo pamusb-conf --add-device my-usb-stick
```

and it returns command not found error.

i am lost with no idea what to try next.

can you guys please advise as to what next should i try?

thanks in advance.

---

### Post by farhanali on 2015-11-18
Bump

---

### Post by matt_symes on 2015-11-18
Hi

Are you sure your desktop PC is running Wily ?

I've just installed Lubuntu Wily (15.10) on a test machine and a package search doesn't find pamusb-common package.

This page also suggests it has gone for Wily.

[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=pamusb-common](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=pamusb-common)

...along with libpam-usb and pamusb-tools.

This also a fresh install with universe enabled.

They are available for Precise, trusty and Vivid though.

I'm trying to find out what has changed.

EDIT:

Here's the ppa for libpam-usb. Nothing in there for Wily though unless you go for an unsupported PPA.

[https://launchpad.net/ubuntu/+source/libpam-usb](https://launchpad.net/ubuntu/+source/libpam-usb)

Kind regards

---

### Post by farhanali on 2015-11-18
That explains a lot...

i actually upgraded from lubuntu 14.04... and the upgrade did not go smoothly... I had to run recovery to upgrade successfully...

thanks a lot matt i will try the ppa you suggested...

---

### Post by matt_symes on 2015-11-18
Hi

> **farhanali said:**
> That explains a lot...

i actually upgraded from lubuntu 14.04... and the upgrade did not go smoothly... I had to run recovery to upgrade successfully...

thanks a lot matt i will try the ppa you suggested...

That particular PPA i linked above doesn't have any packages for Wily but if you click on the unsupported PPAs link at the bottom of that page, one of the referenced PPAs does contain packages for Wily. That PPA is unsupported and untrusted by Canonical though (but most of them are also not trusted and supported....).

Kind regards

---

### Post by farhanali on 2015-11-21
thanks a lot matt_symes. IT WORKED.

had to mess around a little but it is now up and running.

when i installed the package from the ppa link you suggested it installed but the **libpam-usb** did not install and apt-get returned an error that **udisks** is not available. when i searched for that i found that udisks was also not available for wily.

so i searched for unsupported package for udisks and found it [here]("https://launchpad.net/ubuntu/wily/i386/udisks/1.0.5-1build1")

i downloaded the .deb and installed it and VIOLA... it worked like a charm.

regards,

---

