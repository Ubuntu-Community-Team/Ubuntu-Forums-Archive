---
title: "Package operation failed; No space left on device."
date: 2015-07-04
forum: General Help
---

### Post by bookherd on 2015-07-04
I'm using Ubuntu 12.04. When I use my Software Center's "Update Manager" function, it gives me an error message:

> Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?

Of course I do! But when I click "Repair" and enter the password, it eventually says: 

> Package operation failed: The installation or removal of a software package failed.

According to some details that it initially gave me and then stopped offering, the issue appears to be one of space in /lib/modules.  I have tons of free hard drive space, but when I consult my Disk Usage Analyzer, it shows /lib/modules as being in the 90% range (maybe this folder has its own built-in size limit?).  How do I clean this up?  For bonus points, how do I prevent it from happening in the future?

---

### Post by cariboo on 2015-07-04
Do you have /lib/modules on a separate partition? Could you paste the output of the following command:

```
df -h
```

into your next post.

---

### Post by bookherd on 2015-07-04
Yes, I do:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        14G   11G  2.4G  82% /
udev            994M  4.0K  994M   1% /dev
tmpfs           201M  848K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1003M   80K 1003M   1% /run/shm
/dev/sda3       128G   71G   51G  58% /home
```

---

### Post by cariboo on 2015-07-04
That's really weird, you have plenty of space on / so the system shouldn't say that you are running out of room. I suggest running:

```
sudo apt-get autoremove
```

and

```
sudo apt-get autoclean
```

to see if you can free up more space.

---

### Post by v3.xx on 2015-07-04
I wonder if /boot is full of old kernels.
```
ls /boot
```

---

### Post by bookherd on 2015-07-05
Cariboo, I tried both of those, but the problem still exists. Thank you though!

v3.xx, /boot contains over 100 files.  How can I clean these up?

---

### Post by v3.xx on 2015-07-05
To remove old kernels
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

It may not work because you have so many, but give it a try.

If this does not work, you will need to remove a few old kernels manually  and then run the command again.  The removal command also needs some room to work.

---

### Post by bookherd on 2015-07-05
Thanks, v3.xx.  The single command indeed does not work.  I followed the link you provided and found a link in comments on [how to remove kernels manually]("http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/"), but I'm not sure this is working either.  Here's the response I'm getting to the recommended commands:

```
~$ sudo apt-get remove linux-headers-3.8.0-35-generic linux-image-3.8.0-35-generic linux-headers-3.8.0-35
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-lts-trusty : Depends: linux-headers-3.13.0-53-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

After this, /boot appears to still have the same number of kernels, and when I grep to see which files are in the one I tried to remove, it looks like they're all still there.  

When I run 'apt-get -f install' as suggested, I get 

```
After this operation, 76.5 MB of additional disk space will be used.
```

...which is of course followed by a "No space on device" error.

---

### Post by bapoumba on 2015-07-05
Please check if you are running out of inodes :
```
df -i
```

---

### Post by v3.xx on 2015-07-05
I think you will be right; inodes will be full.

When apt-get will not work; other ways to remove kernels.
[http://ubuntuforums.org/showthread.php?t=2221389&p=13011506#post13011506](http://ubuntuforums.org/showthread.php?t=2221389&p=13011506#post13011506)

[http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full](http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full)

[http://ubuntuhandbook.org/index.php/2013/08/remove-old-kernels-from-ubuntu-13-04-13-10/](http://ubuntuhandbook.org/index.php/2013/08/remove-old-kernels-from-ubuntu-13-04-13-10/)

[http://ubuntuforums.org/showthread.php?t=2177170&p=12800804#post12800804](http://ubuntuforums.org/showthread.php?t=2177170&p=12800804#post12800804)

---

### Post by bookherd on 2015-07-06
You are both correct about inodes:

```
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       883008 882659     349  100% /
udev            214904    478  214426    1% /dev
tmpfs           219655    405  219250    1% /run
none            219655      3  219652    1% /run/lock
none            219655      5  219650    1% /run/shm
/dev/sda3      8511488 106190 8405298    2% /home
```

Thank you for the links, v3.xx.  I am unable to follow up on them right now, but will do so and report back as soon as possible.

---

