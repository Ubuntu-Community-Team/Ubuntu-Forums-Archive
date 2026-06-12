---
title: "Encrypt Swap Partition?"
date: 2014-04-18
forum: General Help
---

### Post by RookieUbuntuUser58 on 2014-04-18
I had my home folder encrypted during Ubuntu install which I assume encrypted the swap partition as well. I deleted that swap partition and created a new swap partition using Gparted. Now when I run the following: 

```
sudo swapon --all

or 

sudo swapon --all --verbose

```


It returns 

```
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory site
```


It seems swap is working correctly though. How would I go about encrypting the new swap partition to fix that issue?

---

### Post by RookieUbuntuUser58 on 2014-04-19
Anyone?

---

### Post by taytaybongsong on 2014-04-20
i'm actually having the same problem. during an install of xubuntu 14.04 ubiquity couldn't create an encrypted swap. i let the install finish, then i started from scratch with plain ubuntu 14.04. the installer said ubiquity successfully created an encrypted swap, but after it was finished ubuntu was unable to recognize it. it won't mount during boot, and attempting to mount it through swapon or cryptsetup, doesn't work either. this is ridiculous. i wouldn't mind waiting months for a new release if significant bugs like this were ironed out.

p.s. looks like someone reported the bug quite accurately in launchpad: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1303002](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1303002) it's pretty much a show stopper, because i want an encrypted home folder, but if i choose to encrypt my home folder, i have to sit on top of an installation with a broken swap, and if i want a swap file, i can't encrypt my home folder. screwed if you do, screwed if you don't.

---

### Post by HermanAB on 2014-04-20
You could try making a swap file instead of a swap partition.  The details are in the swapon man page.  If the swap file is on your encrypted home partition, then it will also be encrypted when the system is at rest, same as the other files.

---

### Post by taytaybongsong on 2014-04-20
thanks herman, but it's still a serious bug in the installer that leaves  us with an unusable swap partition. what would be more useful is if  someone could chime in with instructions on how to get the encrypted  swap partition working, or maybe how to remove the faulty partition  altogether, and create a new one that actually functions. in 13.10 i  encrypted my swap partition manually after an install and it worked  perfectly, so even having an option to simply have an encrypted home  folder created with an unencrypted swap partition would be great.

---

### Post by taytaybongsong on 2014-04-20
unfortunately, i just found out that even a fresh install of ubuntu  14.04 without encrypted home, will repeatedly fail to recognize and  mount an encrypted swap partition created after install with ecryptfs.  it seems the new LTS is incapable of working with encrypted swap  partitions in any way.

the only temporary solutions i can see are as follows;
1.  choose to encrypt your home folder during an install, then 'convert'  your encrypted swap partition to a normal swap partition, using the  instructions here:  [http://codenachos.com/view/ubuntu-enable-and-disable-swap-encryption](http://codenachos.com/view/ubuntu-enable-and-disable-swap-encryption)
2. don't encrypt your home folder during the install.
3. use HermanAB's suggestion.

---

### Post by Alley_Oop on 2014-05-18
Try reading this. [http://ubuntuforums.org/showthread.php?t=2224129&p=13023818#post13023818](http://ubuntuforums.org/showthread.php?t=2224129&p=13023818#post13023818)

---

