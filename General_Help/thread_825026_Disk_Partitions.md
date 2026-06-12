---
title: "Disk Partitions"
date: 2008-06-10
forum: General Help
---

### Post by hippiedream on 2008-06-10
Does anyone how to partition a hard drive in Ubuntu? I am looking to keep a a minimal version of Vista on my system and be able to use that for dual booting purposes. First of all I want to know how to partition the drive then how I go about installing Vista on that particular drive. Thanks!

---

### Post by sexcopter on 2008-06-10
A good starting point would be to use gparted. (If my memory serves, it appears as "Gnome Partition Editor" in the menu, but I'm at work now so can't check) Either install in Synaptic, or run

```
sudo apt-get install gparted
```

gparted is a simple and powerful partitioning tool. I'm sure there are plenty of others, but this one does the trick nicely. If you haven't partitioned before, tread with **extreme caution**, and **back-up** anything that you can't afford to lose.

Cheers,
James

---

### Post by dudude on 2008-06-10
For dual-booting follow this guide [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

and use gparted for any further modifications.

---

### Post by forestpixie on 2008-06-10
This might help you to do that. I assume that you have buntu installed already, not sure if vista is different but it might want to be at the beginning of the hard drive

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by forestpixie on 2008-06-10
> **sexcopter said:**
> A good starting point would be to use gparted. (If my memory serves, it appears as "Gnome Partition Editor" in the menu, but I'm at work now so can't check) Either install in Synaptic, or run

```
sudo apt-get install gparted
```

gparted is a simple and powerful partitioning tool. I'm sure there are plenty of others, but this one does the trick nicely. If you haven't partitioned before, tread with **extreme caution**, and **back-up** anything that you can't afford to lose.

Cheers,
James

If the op has to resize the /, it's not possible on a running system afaik, hence the livecd.

Of course I prefer to use a bootable partition editor like gparted or partedmagic anyway.

---

### Post by sexcopter on 2008-06-10
> **forestpixie said:**
> If the op has to resize the /, it's not possible on a running system afaik, hence the livecd.

Of course I prefer to use a bootable partition editor like gparted or partedmagic anyway.

Fair point. It would be handy to know more about his set-up and exactly what he intends to do.

---

### Post by forestpixie on 2008-06-11
Another one of those how do I do this - but no information to help threads :)

---

### Post by hippiedream on 2008-06-22
Shoot sorry people. Initially, it was recommended that I keep Vista installed on my computer but through subsequent use of Ubuntu I came to realize that it simply wasn't necessary and forgot about this thread. Bad manner. Sorry!

---

