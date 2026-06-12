---
title: "Is possible an kernel update in Ubuntu 18.04.5 i386 ?"
date: 2022-07-31
forum: General Help
---

### Post by aug7744 on 2022-07-31
Thanks for read my topic.
Last Ubuntu 32 bits was 18.04.5.
Have kernel updates for 18.04.5 32 bits ?
I only wait update because module btrfs updates.

If have what simple and easy way to update ? Have PPA available ?

Thanks for your reply.

---

### Post by Bashing-om on 2022-07-31
aug7744 - Hello

What results with terminal commands:
```

sudo apt update
sudo apt upgrade

```

-see where we go from here-

---

### Post by aug7744 on 2022-07-31
All right with you ?
In moment I not has any 18.04.5 installed.
I remember using in an installed 18.04.5 32 bits
sudo apt update
sudo apt upgrade

begin 200 MB download only of libraries updates. Not any kernel update.

---

### Post by guiverc on 2022-07-31
> **aug7744 said:**
> All right with you ?
In moment I not has any 18.04.5 installed.
I remember using in an installed 18.04.5 32 bits
sudo apt update
sudo apt upgrade

begin 200 MB download only of libraries updates. Not any kernel update.

A quick look on my primary box and what I'd expect to see are (using `rmadison linux-image-generic`)
```

 linux-image-generic | 4.15.0.189.174         | bionic-updates   | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-image-generic | 4.15.0.190.175         | bionic-proposed  | amd64, arm64, armhf, i386, ppc64el, s390x
```

and if using the HWE kernel Id expect

```
 linux-image-generic-hwe-18.04 | 5.4.0.122.138~18.04.102 | bionic-security | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-image-generic-hwe-18.04 | 5.4.0.122.138~18.04.102 | bionic-updates  | amd64, arm64, armhf, i386, ppc64el, s390x
```

You can see the ***i386*** in those lines for packages that are 32-bit *i386* involved, note if you want 32-bit for ARM processors it'll be ***armhf  ****(there is no 32-bit for ppc or other architectures*).

Alas my network connection between this (*my primary Lubuntu kinetic box*) and my ibm thinkpad t43 (*i386*) running *bionic* is currently *flaky* so I can't copy/paste what that box sees currently, but I'd expect those to be available (*even if not installed given it's currently ~offline anyway*).

FYI:   A fully upgraded *bionic* system reports itself as 18.04.6 and not 18.04.5, and can tell you my system does!.  You can refer to [here]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") which shows the ISO release date for 18.04.5 was 17-Sept-2021, but the upgrade to installed systems occurred before that date (*I even ran a few QA-tests of that release if I recall correctly; though Lubuntu and other flavors were not involved given it was after the three years of support for flavors*).

---

### Post by ActionParsnip on 2022-07-31
What is the full output of
```

sudo apt update
sudo apt -y full-upgrade
dpkg - l | grep linux-image

```
Thanks

---

