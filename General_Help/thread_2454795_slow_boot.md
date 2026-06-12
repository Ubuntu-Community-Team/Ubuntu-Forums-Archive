---
title: "slow boot"
date: 2020-12-06
forum: General Help
---

### Post by akash-pandey on 2020-12-06
hello guys,
i have hp 14q laptop with i3 seventh generation HDD 5400 RPM
and recently installed ubuntu 20.04, it working very fine but during boot it takes around 1 to 1.5 mins to start which pretty irritating...

please suggest me something which i can do.

Also i love how people solved my previous problem.
such a nice community.

---

### Post by CelticWarrior on 2020-12-06
You can replace the very slow HDD with a SSD.

---

### Post by Impavidus on 2020-12-06
You could try and remove some services that you don't need (do you need bluetooth?) or remove some snaps, as they seem to cause slow booting too. However, I don't think you'll be able to make it much faster than one minute on a 5400 RPM hard drive. Maybe you can make it 50 seconds or so.

---

### Post by Autodave on 2020-12-06
Keep in mind that Windows does not shut down.....it merely hibernates.  That is why you might think that Win10 is so much faster than Linux.  My machine here which is *quite* fast, takes 33 seconds to boot to Linux and almost 2 full minutes to boot to Win10.  (Both OS are on their own SSDs.)  As already said, an SSD would be your best bet for a faster boot.

---

### Post by oldfred on 2020-12-06
Some things to review. Not all may apply. 

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)


A new NVMe SSD makes all the difference in the world. This is a Skylake desktop system, I put together in 2016, but recently added new NVMe drive.
I went thru the threads above & applied as much as I could.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  systemd-analyze [/COLOR]
Startup finished in 3.492s (kernel) + 5.211s (userspace) = 8.704s  
graphical.target reached after 5.201s in userspace


[/FONT]
```

---

