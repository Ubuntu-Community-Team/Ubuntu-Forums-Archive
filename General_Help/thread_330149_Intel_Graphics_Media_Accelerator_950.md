---
title: "Intel Graphics Media Accelerator 950"
date: 2007-01-02
forum: General Help
---

### Post by Quillz on 2007-01-02
Does there exist an automated script that can configure the GMA 950 so that its native widescreen resolution, 1400x900 is available for my laptop? I don't want to manually edit the X11.conf file if I don't have to.

---

### Post by evilghost on 2007-01-02
915resolution

---

### Post by Quillz on 2007-01-02
I'll try that out. Thank you.

---

### Post by evilghost on 2007-01-02
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29) may be even more useful...

---

### Post by Quillz on 2007-01-02
The GMA 950 doesn't seem to be listed in chipset_info.txt. Is it similar to the 945G?

---

### Post by Quillz on 2007-01-02
> **evilghost said:**
> [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29) may be even more useful...
It installed and said something about 1440x900 being available, but it's not... Did I do something wrong?

---

### Post by Quillz on 2007-01-03
> **Quillz said:**
> It installed and said something about 1440x900 being available, but it's not... Did I do something wrong?
Unfortunately, I'm still having trouble. I tried re-installing 915resolution, but it's already installed. How do I uninstall it so I can start over?

---

### Post by vvlist on 2007-01-04
> **Quillz said:**
> Unfortunately, I'm still having trouble. I tried re-installing 915resolution, but it's already installed. How do I uninstall it so I can start over?

To reinstall Ubuntu with a clean slate, you can (1) Delete every file that begins with a period (.), then boot up with the install disk, and select the correct partitions in the advanced gparted editor, and install. Or (2) you can just boot up with the install disk, and choose to erase everything and proceed with the install. Hope that helps...

---

### Post by Quillz on 2007-01-04
I finally got it to work. I'm now using Ubuntu in 1440x900 resolution, which looks far better!

---

