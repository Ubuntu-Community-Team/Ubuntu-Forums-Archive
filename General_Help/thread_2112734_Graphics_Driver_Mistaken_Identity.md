---
title: "Graphics Driver Mistaken Identity"
date: 2013-02-05
forum: General Help
---

### Post by tubular on 2013-02-05
I have xubuntu on 2 diferrent computers. Just installed the catalyst package on the wrong system where I have a radeon card  ](*,)
Now Xubuntu hangs and does not boot completely. 

Need Help ! #-o

---

### Post by omeomi on 2013-02-05
Can you boot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode")? That will allow you to fix your drivers.

---

### Post by tubular on 2013-02-05
i can get to the 'root shell prompt' thru recovery mode - but don't know how to remove catalyst and recover the original driver which was auto-installed with Xubuntu a while back.

My Options in recovery mode:
Clean - clean up space
dpkg - repair broken packages
fsck - check file system
grub - ...
network - ...
Root - root shell prompt
System Summary - ...

---

### Post by omeomi on 2013-02-05
If you go into the root shell prompt you can use the steps described in [this post]("http://ubuntuforums.org/showpost.php?p=12008178&postcount=3") to remove the catalyst driver and reinstall the default

---

### Post by tubular on 2013-02-05
Thanks for the link omeomi...
but after first line entry (sudo sh /usr/share/ati/fglrx-uninstall.sh) tells me "cannot get" :(

---

### Post by Thee on 2013-02-05
Continue with rest of the commands, it should still work.

---

### Post by tubular on 2013-02-06
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
```


Lines 2 and 3 entries give me this:
W: Not using locking forread only lock file /var/dpkg/lock
E: Unable to writr to /var/cache/apt
E: The package list or status file could not be parsed or opened

and...
```
sudo apt-get install --reinstall libgl1 -mesa-glx libgl1 -mesa-dri xserver-xorg-core
```

cannot identify '-mesa-glx'

---

