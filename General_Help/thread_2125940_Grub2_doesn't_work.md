---
title: "Grub2 doesn't work"
date: 2013-03-15
forum: General Help
---

### Post by bdylan616 on 2013-03-15
Hey all,

I installed lubuntu on an old XP machine, but when I boot it up it doesn't give me the option to choose between the two operating systems, it just boots straight to lubuntu. I can mount the XP section of my hard drive from lubuntu and it looks like everything's there. Does anybody have any ideas? 

Thanks.

---

### Post by deadflowr on 2013-03-15
Try opening up a terminal and running
```
sudo update-grub
```

If the output doesn't generate a line or two for windows run:
```
sudo apt-get install os-prober
```

Though, os-prober should be installed.

---

### Post by bdylan616 on 2013-03-15
I've tried updating grub and installing os-prober, still no luck though. I got grub to load when I press shift now, and I used the 4th post in [http://ubuntuforums.org/showthread.php?t=2000951](http://ubuntuforums.org/showthread.php?t=2000951) to try to get windows to show up. My only problem now is I don't know what to put after "fs-uuid" in the code. XP will load when I select the custom option now, but only because of an error message.

---

### Post by deadflowr on 2013-03-15
You can find the uuid using:
```
sudo blkid
```

The windows id will have either fat32, or ntfs.

You could also post the output from /etc/default/grub , and see if os-prober has been disabled, and also see where the default timeout is set at.

If you do post, please use the code tags (# symbol in the reply box toolbar)

---

### Post by bdylan616 on 2013-03-15
There we go, now that I have the right uuid everything works. Thanks a lot, I really appreciate it!

---

