---
title: "Unable to do upgrade"
date: 2014-08-06
forum: General Help
---

### Post by ishottya on 2014-08-06
Boot is full and I can not do upgrade

sudo apt-get update

...

sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-44-generic but it is not installed
E: Unmet dependencies. Try using -f.



uname -r


3.8.0-42-generic


sudo dpkg --list 'linux-image*'

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-3. <none>         (no description available)
ii  linux-image-3. 3.8.0-29.42~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-34.49~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-35.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-36.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-37.53~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-38.56~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-39.58~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-41.60~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-42.62~pr Linux kernel image for version 3.8.0 on 32 b
in  linux-image-3. <none>         (no description available)
iU  linux-image-ge 3.8.0.44.44    Generic Linux kernel image

sudo apt-get remove linux-image-3.8.0-29-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-44-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by whitesmith on 2014-08-06
Please run```
df -hT | egrep -i "file|^/"
```and post the result.

---

### Post by ishottya on 2014-08-06
Filesystem                  Type      Size  Used Avail Use% Mounted on
/dev/mapper/beguhl--vg-root ext4      456G  6.5G  426G   2% /
/dev/sda1                   ext2      228M  225M     0 100% /boot
/dev/sr0                    udf       7.3G  7.3G     0 100% /media/THE_DAY_AFTER_TOMORROW

---

### Post by whitesmith on 2014-08-06
Looks like /media is also filled. Run this incantation```
du -ah ~ | sort -nr | head -n 25
``` to get a list of the 25 largest files on your system. Move them elsewhere and you should be fine. Linux requires at least 5% free space in order to work.

---

### Post by Impavidus on 2014-08-06
> **ishottya said:**
> (...)
sudo apt-get remove linux-image-3.8.0-29-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-44-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Try```
sudo dpkg --purge linux-image-3.8.0-29-generic
```instead of that. The same for the other old kernels. Then try again```
sudo apt-get -f install
```

@whitesmith: the thing in /media is a dvd, so, always full.

---

### Post by ajgreeny on 2014-08-06
I'm afraid your problem is because you are trying to update either a raring installation, or a raring hardware stack, both of which are no longer supported or available in the repositories.  This is why you are getting the 
 ```
linux-image-generic-lts-raring : Depends: linux-image-3.8.0-44-generic but it is not going to be installed
```
line in your output.

What version of Ubuntu are you running?  If you are not certain please show the output of the command ```
lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -mrn
``` which will tell us a lot more about your version of Ubuntu and the current DE and kernel in use.

It will also be of use to know what partition arrangement you are using and whether you have a separate /boot partition.

Please show the output of ```
sudo fdisk -l
```which will show us the details.

---

### Post by whitesmith on 2014-08-07
> **Impavidus said:**
> @whitesmith: the thing in /media is a dvd, so, always full.
My eyes sink and my brain shrinks when my boss has me pull an all-nighter.

---

