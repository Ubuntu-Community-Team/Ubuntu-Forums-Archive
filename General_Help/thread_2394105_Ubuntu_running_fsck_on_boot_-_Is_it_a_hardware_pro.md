---
title: "Ubuntu running fsck on boot - Is it a hardware problem?"
date: 2018-06-12
forum: General Help
---

### Post by fredwagner on 2018-06-12
Hi! I have a notebook running Ubuntu 16.04 and it started running fsck on almost every boot, saying it needs to fix some errors.

It fails to fix the errors, then I run fsck manually from an Ubuntu Live USB stick with the following command:

$ sudo fsck -y /dev/sda5

This trick worked a few times and I was able to boot normally.

But on the last time I tried it it booted, but when I tried to open Google Chrome and Firefox they don't open, giving a segmentation fault error at the terminal.

I'm afraid it can be a bad sector problem in the HD. I don't know.

How can I fix this? Is this a software problem in Ubuntu or a hardware problem with the HD. Should I replace the HD?

Any help is welcome. I need to fix this ASAP. Thanks!

---

### Post by Autodave on 2018-06-12
Hopefully someone else will be able to help you, but it sure sounds like a bad HD to me. Before I would trash it though, I would copy everything off of it and try re-installing to see what happens.

---

### Post by ajgreeny on 2018-06-12
Use the Disks utility to see if any hardware problems are reported with the HDD.
With the HDD highlighted go to the hamburger menu icon and choose **Smart Data & Self Tests**.
All lines shown should end with **"OK"**; if any show problems you need to look for solutions to the problem shown.

---

### Post by fredwagner on 2018-06-12
> **ajgreeny said:**
> Use the Disks utility to see if any hardware problems are reported with the HDD.
With the HDD highlighted go to the hamburger menu icon and choose **Smart Data & Self Tests**.
All lines shown should end with **"OK"**; if any show problems you need to look for solutions to the problem shown.

I'll try this when I arrive home.

If everything is listed as OK does that mean it's not a hardware problem?

---

### Post by rsteinmetz70112 on 2018-06-12
> **fredwagner said:**
> I'll try this when I arrive home.

If everything is listed as OK does that mean it's not a hardware problem?

Not necessarily. ;) It means the hard drive doesn't recognize a problem. You still could have other hardware problems including bad memory, or something on the mother board.
Good Luck

---

### Post by sudodus on 2018-06-12
Probably *yes*. But ...

It might also be an error in the file system, that cannot be corrected by the automatic (and rather safe) method that is used at boot. You could boot from another drive (for example a live USB/DVD drive with Ubuntu), check that the system partition(s) of the installed system (root, maybe some other partiiton too) is *not* mounted, and run the following command line,

```
sudo e2fsck -f /dev/sdxn
```

where x is the drive letter and n is the partition number.

There are more details at this link, [FSCK reports that filesystem still has errors - what should I do now?](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors-what-should-i-do-now/972983?s=1|14.4118#972983)

---

### Post by fredwagner on 2018-06-13
> **ajgreeny said:**
> Use the Disks utility to see if any hardware problems are reported with the HDD.
With the HDD highlighted go to the hamburger menu icon and choose **Smart Data & Self Tests**.
All lines shown should end with **"OK"**; if any show problems you need to look for solutions to the problem shown.

This tools shows the HDD failed the test and has 1300 bad sectors.

Looks like physical problem. I'm getting this HDD replaced this weekend. :(

---

