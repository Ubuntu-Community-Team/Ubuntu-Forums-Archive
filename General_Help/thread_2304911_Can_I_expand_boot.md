---
title: "Can I expand /boot?"
date: 2015-12-01
forum: General Help
---

### Post by Ifaistos on 2015-12-01
Hello everyone :-)

When Ubuntu created my partitions it created an /boot/efi partition and a seperate /boot partition which was extra small.
I didn't make notice of this at the time, but I just got this error from Update manager.

So is there a way to expand my /boot partition, or any other way to overcome this problem?

I have already sudo apt-get cleared and emptied the trash.

Thanks!

---

### Post by slickymaster on 2015-12-01
Have you tried to see if running the autoremove command from the terminal will help clean it```
sudo apt-get autoremove
```If not, check your kernel version, so you won't delete the in-use kernel image```
uname -r
```Then get a list of installed kernels```
sudo dpkg --list 'linux-image*'
```and delete the kernels you don't want/need anymore by running```
sudo apt-get purge linux-image-VERSION
```Replace VERSION with the version of the kernel you want to remove. Finally update grub2```
sudo update-grub2 
```

---

