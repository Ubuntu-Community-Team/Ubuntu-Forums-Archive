---
title: "root partition free space"
date: 2007-05-31
forum: General Help
---

### Post by nahham on 2007-05-31
When I had Edgy the root "/" partition had 4 GB of space (I had a separate /home partition).  It filled up to around 86% making me feel that the computer isn't running that great.  When it came time to upgrade I deleted everything and increased the root partition to 8 GB for Feisty.  It still uses 86% of the space allocated :confused:

I am wondering what is happening because I did not install any more programs on Feisty (I actually installed less).


Here is what df gives:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              7779680   6280112   1104372  86% /
varrun                  517288        92    517196   1% /var/run
varlock                 517288         0    517288   0% /var/lock
udev                    517288       156    517132   1% /dev
devshm                  517288        16    517272   1% /dev/shm
lrm                     517288     33788    483500   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda5             22105760   4905288  16077532  24% /home
/dev/sda1             56563888  27801976  28761912  50% /media/sda1
/dev/sda2              4949672   4201388    748284  85% /media/sda2

```

Thanks..

---

### Post by pbw on 2007-05-31
sudo apt-get install filelight. Launch that and see where your diskspace is being used, should help.

To give you an idea my diskspace is as follows:
/ - 175mb
/boot - 24mb
/usr - 2.5gb
/var - 639mb

Adept shows # of packages installed to be - 997.

-- pbw

---

### Post by kruppe on 2007-06-07
I'm struggling with a similar/related problem

My setup is 

[html]/dev/hdb1               21G    20G   110M 100% /
varrun                 1.1G   267k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
procbususb             1.1G   132k   1.1G   1% /proc/bus/usb
udev                   1.1G   132k   1.1G   1% /dev
devshm                 1.1G      0   1.1G   0% /dev/shm
lrm                    1.1G    32M   1.1G   3% /lib/modules/2.6.20-15-generic/vo                                                                                                   latile
/dev/hdb3               92G    69G    24G  75% /home
/dev/sdc1              320G   285G    36G  89% /media/500
/dev/sdb1              500G   314G   187G  63% /media/300xfs
/dev/sda1              290G   288G   2.5G 100% /media/series
tmpfs                  1.1G    40M   1.1G   4% /lib/modules/2.6.20-16-generic/vo     [/html]My problem however is that my / (root partition) keeps running full. 

My applications tend to break as they have no more temp space to write to.



Could anyone please suggest how I 'peacefully' modify my setup so that I can migrate more space (I have an extra 150gig lying around I can possibly map to some folders)?

What folders would be best to map to the new / larger drive?

Thanks in advance for your help.

---

### Post by Mr. C. on 2007-06-07
You will have to look at your (almost) full file systems to see where the space is being used.

You can use the app recommended by pbw, or you can use du via command line:
```

du -xh --max-depth=1  /
```

and see what totals come back for the various directories.  Then, do likewise for each subdirectory reported, largest ones first.

MrC

---

### Post by pbw on 2007-06-07
For Kruppe i'd also suggest clearing his apt cache and removing old kernels he doesnt use anymore. i bet he'll clear up an easy couple gb. That'll at least allow him to run some apps properly and be able to diagnose what to partition to the new drive.

Personally I would dump /home and swap over to the new drive and then resize root (should help with a bit of speed as well). And depending how the root partition is being used, either resize it to take advantage of the space freed up from moving home and swap, or split it up a bit.

Paste back what du says and someone can advise you.

-- pbw

---

