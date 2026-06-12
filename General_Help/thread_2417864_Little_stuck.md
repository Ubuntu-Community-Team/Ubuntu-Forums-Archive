---
title: "Little stuck"
date: 2019-04-28
forum: General Help
---

### Post by jmh474 on 2019-04-28
So I quite new to the Ubuntu seen and hoping for a little help. 

I'm triple booting windows 10, Ubuntu and android, each os has its own hard drive, using grub2

Android = sdb1
Windows = sdb2
Ubuntu = sdb3

Iv got Ubuntu and windows but I'm struggling with adding android to the boot list. 

Iv installed the latest version of android.

System is 64bit, 4 GB ram and old optiplex 390  hard drive 1TB windows / 500GB android / 250GB Ubuntu, standard cpu but I'm hunting for an i5 2400 and possibly increase ram to 8GB

thanks for any advice

---

### Post by jmh474 on 2019-04-29
Any help anyone please

---

### Post by Rubi1200 on 2019-04-29
Please boot into the system from a liveCD/USB and run the summary report for the boot info (link in my signature). Do not repair anything, just generate the report and paste here so we can advise better on your options.

Thanks.

---

### Post by jmh474 on 2019-04-30
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the &#8216;exec tail&#8217; line above.
menuentry 'Android' {
set root= 'hd1,1'
linux /android-8.1-r1/kernel quiet root=/dev/ram0 androidboot.hardware=android_x86_64 SRC=/android-8.1-r1
initrd /android-8.1-r1/initrd.img }

this is the the custom_40 file i created whats wrong

---

