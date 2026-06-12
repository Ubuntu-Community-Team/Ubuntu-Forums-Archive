---
title: "cant get k7-smp to show up in grub menu"
date: 2006-08-06
forum: General Help
---

### Post by djsamsel on 2006-08-06
i've downloaded the k7-smp core using apt-get, but it does not show up as an option in grub. any help will be greatly appreciated. doug

---

### Post by Sutekh on 2006-08-06
In the Dapper Drake release, the K7 kernel has the SMP config option enabled, so when you install the K7-SMP kernel from apt-get it actually fetches and installs the ordinary K7 kernel. Check it out from the Ubuntu Packages site. The [linux-k7-smp]("http://%5BURL=%22http://packages.ubuntu.com/dapper/base/linux-k7-smp%22") package installs the [linux-k7-image]("http://packages.ubuntu.com/dapper/base/linux-image-k7") package, which installs the ordinary [k7 kernel]("http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-26-k7")


SMP will be enabled in this kernel. You can check this by entering in this command, which lists the CPU information, from a Terminal window (Applications -> Accessories menu)
```
cat /proc/cpuinfo
``` You should see two separate listings, one for each core; CPU 0 and CPU 1.

---

