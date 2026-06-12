---
title: "Please help me set my screen resolution"
date: 2012-11-25
forum: General Help
---

### Post by IainP on 2012-11-25
Hi,

Could someone help me set up my screen resolution on my netbook (Asus X101CH) which is running intel atom CPU

At present in the displays window I only have the option to set resolution @ 800X800, I need 1024X168.

I have tried some of the online guides

When I run xrandr in the terminal I get:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* 
  1680x1050 (0x150)  146.2MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1024x768 (0x151)  146.2MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz


I think I need to set my output to 1024X768, but I cant see what the output is called, have tried a few random combinations now but im a but stuck now  ;D


please help :D


Iain.

---

### Post by sdowney717 on 2012-11-25
1024 by 600 is all it can do

here someone says they found a solution
[http://ubuntuforums.org/showthread.php?t=1948617](http://ubuntuforums.org/showthread.php?t=1948617)

---

### Post by IainP on 2012-11-25
nice one, thanks will try now and update :D

---

### Post by sdowney717 on 2012-11-25
I am currently using 3.2 kernel
Mine is not your PC issue, just remarking that seems you need to upgrade the kernel one way or another.

> scott@scott-P5QC:~$ uname -r
3.2.0-33-generic-pae
scott@scott-P5QC:~$ 


---

### Post by sdowney717 on 2012-11-25
following their directions I get errors, so perhaps you will need to find another way to upgrade the kernel to 3.4

```
scott@scott-P5QC:~$ cd /tmp && wget http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.4.2
--2012-11-25 14:41:19--  http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.4.2
Resolving dl.dropbox.com (dl.dropbox.com)... 184.73.219.26, 23.21.81.10, 50.16.185.216, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|184.73.219.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596 (1.6K) [text/plain]
Saving to: `linux-kernel-3.4.2'

100%[=====================================>] 1,596       --.-K/s   in 0s      

2012-11-25 14:41:19 (325 MB/s) - `linux-kernel-3.4.2' saved [1596/1596]

scott@scott-P5QC:/tmp$ chmod +x linux-kernel-3.4.2 && sudo ./linux-kernel-3.4.2[sudo] password for scott: 
--2012-11-25 14:41:55--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.2-quantal/linux-headers-3.4.2-030402_3.4.2-030402.201206091355_all.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80... failed: Connection refused.
--2012-11-25 14:41:55--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.2-quantal/linux-headers-3.4.2-030402-generic_3.4.2-030402.201206091355_i386.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80... failed: Connection refused.
--2012-11-25 14:41:56--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.2-quantal/linux-image-3.4.2-030402-generic_3.4.2-030402.201206091355_i386.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80... failed: Connection refused.
--2012-11-25 14:41:56--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.2-quantal/linux-image-extra-3.4.2-030402-generic_3.4.2-030402.201206091355_i386.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
[B]Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80... failed: Connection refused.
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:[/B]
 *.deb
scott@scott-P5QC:/tmp$ 

```

---

### Post by IainP on 2012-11-26
well that fixed it.... thanks for the help.

---

### Post by sdowney717 on 2012-11-26
I am glad you got it.:)

So for others reading, tell what you did and also mark is solved under thread tools.

---

