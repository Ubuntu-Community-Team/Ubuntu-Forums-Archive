---
title: "is encryption of the home directory is something that the team is working on?"
date: 2019-12-16
forum: General Help
---

### Post by ronjjjg8885 on 2019-12-16
at the moment it is complicated to encrypt the home directory.

thank you very much!

---

### Post by TheFu on 2019-12-17
They removed it because of security issues with the 2 most popular implementations. Those both leaked metadata about the file sizes.
The approved solution is it perform whole disk encryption for the partition with LUKS.  That is an install option, last time I checked. My 16.04 laptop uses it.

Regardless of which encryption method is used, excellent backups are mandatory.  When an encrypted partition/file gets corrupted for any reason, the only solution is to restore from a backup.

---

### Post by ronjjjg8885 on 2019-12-20
hi thank you!
do you say that in the ubuntu installation of 16.04 there is an option for whole disk encryption?
at what stage of the installation

---

### Post by TheFu on 2019-12-20
> **ronjjjg8885 said:**
> hi thank you!
do you say that in the ubuntu installation of 16.04 there is an option for whole disk encryption?
at what stage of the installation

Yes, it is definitely an option.  I've been running multiple 16.04 installs with whole disk encryption. I've never installed the default Ubuntu Gnome3 ISO.  I typically use either Ubuntu Server or Ubuntu-Mate.  The selection happens when you pick how to setup the storage. I don't remember all the options, but there are 2 with LVM.
a) LVM
b) Whole drive encryption with LVM

something like that.  There are a few other choices on the page.  It will not be offered in a dual boot situation.  The installer needs to wipe the entire disk.

---

### Post by ronjjjg8885 on 2019-12-25
thank you very much!!!

---

### Post by sudodus on 2019-12-25
Maybe the following link will help you recognize **how to select LVM with LUKS encryption**. It describes how to do it with Ubuntu 19.10, and it is very similar in all current versions of Ubuntu and Ubuntu family flavours (Kubuntu, Lubuntu ... Xubuntu).

[Install Ubuntu 19.10 with encrypted swap/home partitions, specifying manually the swap partition](https://askubuntu.com/questions/1195949/install-ubuntu-19-10-with-encrypted-swap-home-partitions-specifying-manually-th/1196568#1196568)

Probably *you need not add extra swap* to what is configured automatically (but the original poster at AskUbuntu asked for it).

---

### Post by CelticWarrior on 2019-12-25
> **TheFu said:**
> (...) When an encrypted partition/file gets corrupted for any reason, the only solution is to restore from a backup.

Many thanks!!! I suspect that for a long time but the online information and discussions about it are scarce and typically dead-ends. Having at last an expert confirming it makes all the difference.

---

### Post by ronjjjg8885 on 2020-06-20
hi
thank you
what about version 20.04? 
is it the same?

i don't have much important data on my computer and i also like it be eencrypted still.

---

### Post by HermanAB on 2020-06-20
It is best to always encrypt the 'whole disk'.  It isn't really the whole disk, since /boot is in plain text, but it makes it very difficult/impossible to subvert if there is almost no plain text space on the disk.  However, you must have good backups, since data that is not backed up, is ephemeral and doesn't really exist.

I had a laptop stolen a couple decades ago, and learned the value of encryption the hard way...

---

### Post by ronjjjg8885 on 2020-06-20
i see
thanks
one of my computers is dual boot with windows 10
does that means tthat in this particular computer i need another aproach than the whole disk encryption?

is there a video tutoriall that you reccomned that explain the whole disk encryption proccess?

---

