---
title: "how to install balena etcher to burn iso files"
date: 2018-12-25
forum: General Help
---

### Post by geovino on 2018-12-25
I tried installing etcher burning software but it would not open. Ubuntu does not have a iso burner software that works. Tried Make Start up disk but it does not show the iso I want to burn.

---

### Post by ajgreeny on 2018-12-25
I do not know etcher at all so can not help specifically with that but try [unetbootin]("https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa") or even better in my opinion, [mkusb]("https://help.ubuntu.com/community/mkusb"), both of which need a ppa enabled.  

They are both for USB creation but if you want to burn a DVD try xfburn, the burner from Xubuntu.

The startup-disk-creator has not been trustworthy for a while now according to many and was always for Ubuntu or Ubuntu derived .iso archives only, though I've not used it for several years and now always go straight to mkusb.

---

### Post by oldos2er on 2018-12-25
xfburn, mkusb, and k3b all work well for me.

---

### Post by CatKiller on 2018-12-25
> **geovino said:**
> I tried installing etcher burning software but it would not open. Ubuntu does not have a iso burner software that works. Tried Make Start up disk but it does not show the iso I want to burn.

Install gdebi if you haven't already.

Get the appropriate .deb file from [here](https://github.com/balena-io/etcher/releases/tag/v1.4.4).

Install the file with gdebi.

---

### Post by scottbomb on 2018-12-25
I use dd to make iso files of DVDs/CDs for storage and to write them to disk, thumbdrive, etc. 

To make iso from DVD or CD. The sr0 is my DVD device. To get yours, look it up with df -H. Do not use spaces around the "=".

```
dd bs=4M if=/dev/sr0 of=your_iso__file_name.iso
```

To burn iso to DVD/CD, we do the above in reverse.

```
dd bs=4M if=your_iso__file_name.iso of=/dev/sr0
```

To make audio CDs from mp3, wav, etc, I use xfburn. Brasero and k3b work well too.

---

### Post by gsahli on 2018-12-25
I found Brasero (installed in MATE) to work well. There are many working choices.

---

### Post by Topsiho on 2018-12-27
I always use brasero, successfully.
You need to burn the .iso file as **an image**, not just copy it to the DVD.
There are many programs available in Ubuntu for burning .iso files.

Topsiho

---

