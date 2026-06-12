---
title: "Rufus for linux"
date: 2015-12-05
forum: General Help
---

### Post by Evil Wayz on 2015-12-05
I have never once gotten unetbootin to work in Ubunut or Mint.  I have always used a windows computer and used Rufus.  Well my windows comp is dead, and I need a live disk, I noticed rfus has a linx version but it's unsupported and I'm not very good at compiling.  Anyone know where I might find a Debian/Ubuntu deb file?  THanks

---

### Post by cariboo on 2015-12-05
You can use Gnome Disks to create a bootable usb device. Select Restore Disk Image... and follow the prompts

---

### Post by tgalati4 on 2015-12-05
*unetbootin* has always work for me.  I like the fact that you can choose several distros, directly from the net to download-and-burn in one step.  What version did you use and what problems did you have?

I don't know what version is in 14.04, but the documentation is dated Nov 2008.

> tgalati4@Mint17 ~ $ apt-cache policy unetbootin
unetbootin:
  Installed: 585-2ubuntu1
  Candidate: 585-2ubuntu1
  Version table:
 *** 585-2ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
        100 /var/lib/dpkg/status


Perhaps run it in debug mode:

```
unetbootin --debug
```

---

### Post by sammiev on 2015-12-05
I really like mkusb.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

