---
title: "there's gotta be an easy way.. (complex partitioning)"
date: 2007-11-20
forum: General Help
---

### Post by Kymus on 2007-11-20
Alright, I've got 4 HD: two with Ubuntu, and two with Windoze. Each drive is not just partitioned with that file system, but actually has that OS on it.

HD1 is my main drive with Ubuntu on it
HD2 is a secondary Ubuntu drive but has some interesting issues ([see here]("http://ubuntuforums.org/showthread.php?t=586878"))
HD3 is my over-sized Windoze partition (Windoze doesn't need 250GB all to itself when I really only use it as a last resort if I can't run something with wine or in a virtual machine)
HD4 is my friends drive with Windoze (it won't boot, so I gotta grab the files and then format and reinstall Windoze)

Because of the issue I mentioned with HD2, as well as the fact that HD4 likes to supercede all other boot processes (thanks windows; nice to know you're good at something), right now my boot options are just HD1 and HD3.

What I need to do, is connect all 4, get all 4 to pop up in grub, copy the contents of HD4 to another HD and then remove it and bring everything back to my everyday usage of HD 1, 2, & 3. I'd also like to take about 200GB out of HD3 and turn that into another ext3 file system (I assume that can be done effortlessly through a partition manager?).

so uh.... how would this happen?

---

### Post by JohnLM_the_Ghost on 2007-12-01
As for Partitioning the best bet would be to get some Windows NTFS (i presume) filesystem compatible Partition Editor within Windows. Try googling 'Partition Magic' cause that one would be a good start, but i'm not really sure it can Resize NTFS.
Within Ubuntu GParted (Gnome Partition Editor) is probably the best and what you should have already.

Alternative is to backup needed files from HD3 and then make two fresh new partitions with gparted and reinstall Windows on HD3 but installation might interfere with GRUB :(

As for GRUB... I'm no Pro myself, but I know for sure you have to edit /boot/grub/menu.lst on the your main HDD (the one containing Boot info - GRUB)

You have to edit it as root of course.
to add HD2 it would be a good idea to try adding another option at the end of menu.lst

similiar to Ubuntu's one but with different HDD (and Kernel probably)

should look similiar like my menu entry
```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot
```

just dont copy this one. (Replace root, kernel and initrd with yours.)
and MAYBE HDD for GRUB are defined in 'device.map', at least i got two entries there

If HD2 had a GRUB which is now inactive, check for its entry in menu.lst on HD2

Just before you do anything try searching for GRUB configuration topics.
Sorry I couldn't be of any more help.

---

