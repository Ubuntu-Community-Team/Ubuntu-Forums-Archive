---
title: "CANT INSTALL SKYPE using gdebi status: wrong architecture i386"
date: 2016-05-03
forum: General Help
---

### Post by jameswdenyer on 2016-05-03
ive tried all the different downloads from the skype website what do i do.
this is for ubuntu 16
my cpu is AMD A6-3420M APU with Radeon(tm) HD Graphics × 4 
im running at 64 bit

---

### Post by Coffed on 2016-05-03
i386 is a 32-Bit Architecture of Intel CPUs. Since you are running ubuntu on an AMD, the architecture of the skype package does not match with the one of your CPU.

Either download the 64-Bit Version of Skype for AMD CPUs or try this guide found after a quick google search: [http://ubuntuhandbook.org/index.php/2016/04/install-skype-4-3-in-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/04/install-skype-4-3-in-ubuntu-16-04/)

---

### Post by howefield on 2016-05-03
> **jameswdenyer said:**
> ive tried all the different downloads from the skype website what do i do.
this is for ubuntu 16
my cpu is AMD A6-3420M APU with Radeon(tm) HD Graphics × 4 
im running at 64 bit

Have you tried installing Skype from the Ubuntu repositories ?

You would need to enable the Partners repository first.

---

### Post by jameswdenyer on 2016-05-03
I have just looked at the how to guide and I can't seem to enable it there is no option to do so in the others categories

---

### Post by $yl9pAR%t on 2016-05-03
> [COLOR=#000000]ive tried all the different downloads from the skype website[/COLOR]

From Skype website you should download version for Ubuntu 12.04 (multiarch), do not tinker with others. This is 32-bit version but it works both with 32-bit and 64-bit OS's.

To install from repo, you can run this command in terminal:

```
sudo apt install skype
```

If installing via terminal will not succeed, paste here the output from terminal you will get.

EDIT: About enabling partners repo:

[https://help.ubuntu.com/16.04/ubuntu-help/addremove-sources.html](https://help.ubuntu.com/16.04/ubuntu-help/addremove-sources.html)

---

