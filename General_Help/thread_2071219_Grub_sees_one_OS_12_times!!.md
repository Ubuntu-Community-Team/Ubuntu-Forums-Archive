---
title: "Grub sees one OS 12 times!?!?"
date: 2012-10-14
forum: General Help
---

### Post by Ms. Daisy on 2012-10-14
My laptop dual-boots Windows 7 & Ubuntu.  Recently I added a logical partition and installed Backtrack.  So now I'm triple-booting.  Grub was fine until I installed Backtrack, now grub seems hopelessly confused.

Here's the output of sudo update-grub from the Ubuntu 11.10 installation:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-26-generic
Found initrd image: /boot/initrd.img-3.0.0-26-generic
Found linux image: /boot/vmlinuz-3.0.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-25-generic
Found initrd image: /boot/initrd.img-3.0.0-25-generic
Found linux image: /boot/vmlinuz-3.0.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-24-generic
Found initrd image: /boot/initrd.img-3.0.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-23-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-23-generic
Found initrd image: /boot/initrd.img-3.0.0-23-generic
Found linux image: /boot/vmlinuz-3.0.0-22-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-22-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-22-generic
Found initrd image: /boot/initrd.img-3.0.0-22-generic
Found linux image: /boot/vmlinuz-3.0.0-21-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-21-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-21-generic
Found initrd image: /boot/initrd.img-3.0.0-21-generic
Found linux image: /boot/vmlinuz-3.0.0-20-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-20-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-20-generic
Found initrd image: /boot/initrd.img-3.0.0-20-generic
Found linux image: /boot/vmlinuz-3.0.0-19-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-19-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-17-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-3.0.0-16-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-16-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-15-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-15-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found linux image: /boot/vmlinuz-3.0.0-14-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-14-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
Found Ubuntu 10.04.3 LTS (10.04) on /dev/sda7
done

```But in reality what I've got installed is:

/dev/sda1 = windows boot
/dev/sda2 = windows7
/dev/sda3 = hidden windows recovery
/dev/sda4 = the extended partition
/dev/sda5 = Ubuntu 11.10
/dev/sda6 = linux swap
/dev/sda7 = Backtrack (which grub reports as "ubuntu 10.04")

Here's how gparted sees my partitions
[ATTACH]225561[/ATTACH]

Why does Grub think there are 12 partitions of Ubuntu installed?  How do I convince it there is only one Ubuntu?

---

### Post by mamamia88 on 2012-10-14
with each kernel upgrade a new entry is added and the old one remains an option in case there is something wrong with the old ome

---

### Post by Ms. Daisy on 2012-10-14
Thanks for the lightning-fast response! 

Interesting. So how do I remove the old ones? I can see keeping one previous one, but I don't want all of them.

---

### Post by lisati on 2012-10-14
Entering this from the command line should be enough to get you started:
```

sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove

```

---

### Post by papibe on 2012-10-14
Hi Ms. Daisy.

> **Ms. Daisy said:**
> how do I remove the old ones?

The easiest way is to remove the old kernel packages on synaptic. Check this [article and video]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/") (it still works OK on 10.04).

Regards.

---

### Post by Ms. Daisy on 2012-10-14
papibe's link worked like a charm. Thanks.

lisati's command didn't remove the previous kernels, although it did remove some other junk I didn't need.

---

### Post by lisati on 2012-10-14
> **Ms. Daisy said:**
> papibe's link worked like a charm. Thanks.

lisati's command didn't remove the previous kernels, although it did remove some other junk I didn't need.

Thank you for the feedback and the news that you're making progress. It looks like I might need to do a bit of reading to jog my memory a bit better..... :D

---

### Post by Ditchdoc7893 on 2012-10-14
The easiest way I have found to remedy this situation is to install Grub Customizer. It will allow you display only the things that you wish to display when the Grub menu comes up following boot. It allows you to keep the previous kernel versions on your machine (which I have found very useful in the past if something screwed up and I had a situation that I could not boot into), but you can actually place them in a submenu. I titled mine "Previous Linux Kernels." It is a GUI that has several settings that you can customize to fit your needs. I believe I got it either from Synaptic or from the Ubuntu Software Center.

---

