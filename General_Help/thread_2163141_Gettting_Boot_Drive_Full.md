---
title: "Gettting Boot Drive Full"
date: 2013-07-17
forum: General Help
---

### Post by mistermsk on 2013-07-17
I have been using the server version of ubuntu for a while now. I am at 13.04. Anyway, upgrading and doing dist-upgrades just fine. Until I got errors with apt-get... Not sure what happening until I saw this. 

```
gzip: stdout: No space left on device
```

Well, I was think I got space left what is wrong but then I realized it was with the boot portion.

```
/dev/mapper/a-root 135310552  66180664  62249840  52% /none                                  4         0         4   0% /sys/fs/cgroup
udev                            2059600         4   2059596   1% /dev
tmpfs                            413624      1460    412164   1% /run
none                               5120         0      5120   0% /run/lock
none                            2068120         0   2068120   0% /run/shm
none                             102400         0    102400   0% /run/user
/dev/sda1                        233191    224341         0 100% /boot
/dev/sdb1                     976728060 227543136 749184924  24% /media/usb
```

Currently, this is what my boot partition looks like
```
    2 drwxr-xr-x  4 root root     2048 Jul 17 08:32 .    4 drwxr-xr-x 23 root root     4096 Jul 17 08:32 ..
  839 -rw-r--r--  1 root root   853738 Oct  9  2012 abi-3.5.0-17-generic
  839 -rw-r--r--  1 root root   853793 Oct 19  2012 abi-3.5.0-18-generic
  839 -rw-r--r--  1 root root   853737 Nov 13  2012 abi-3.5.0-19-generic
  842 -rw-r--r--  1 root root   856464 Dec 11  2012 abi-3.5.0-21-generic
  842 -rw-r--r--  1 root root   856743 Jan  8  2013 abi-3.5.0-22-generic
  846 -rw-r--r--  1 root root   860818 Mar 25 16:29 abi-3.5.0-27-generic
  909 -rw-r--r--  1 root root   925685 May  1 13:12 abi-3.8.0-19-generic
  910 -rw-r--r--  1 root root   925769 Jun  6 17:19 abi-3.8.0-25-generic
  910 -rw-r--r--  1 root root   925769 Jun 17 18:19 abi-3.8.0-26-generic
  152 -rw-r--r--  1 root root   154429 Oct  9  2012 config-3.5.0-17-generic
  152 -rw-r--r--  1 root root   154429 Oct 19  2012 config-3.5.0-18-generic
  152 -rw-r--r--  1 root root   154403 Nov 13  2012 config-3.5.0-19-generic
  152 -rw-r--r--  1 root root   154427 Dec 11  2012 config-3.5.0-21-generic
  152 -rw-r--r--  1 root root   154427 Jan  8  2013 config-3.5.0-22-generic
  153 -rw-r--r--  1 root root   154652 Mar 25 16:29 config-3.5.0-27-generic
  159 -rw-r--r--  1 root root   160890 May  1 13:12 config-3.8.0-19-generic
  159 -rw-r--r--  1 root root   160891 Jun  6 17:19 config-3.8.0-25-generic
  159 -rw-r--r--  1 root root   160893 Jun 17 18:19 config-3.8.0-26-generic
    1 drwxr-xr-x  5 root root     1024 Jul 17 08:17 grub
15399 -rw-r--r--  1 root root 15705410 Nov  5  2012 initrd.img-3.5.0-17-generic
15401 -rw-r--r--  1 root root 15707314 Nov  6  2012 initrd.img-3.5.0-18-generic
15399 -rw-r--r--  1 root root 15705562 Dec  6  2012 initrd.img-3.5.0-19-generic
15401 -rw-r--r--  1 root root 15707634 Jan  1  2013 initrd.img-3.5.0-21-generic
15405 -rw-r--r--  1 root root 15711869 Apr 11 10:27 initrd.img-3.5.0-22-generic
15591 -rw-r--r--  1 root root 15900943 Apr 26 10:22 initrd.img-3.5.0-27-generic
16307 -rw-r--r--  1 root root 16631168 May 14 08:14 initrd.img-3.8.0-19-generic
16310 -rw-r--r--  1 root root 16634001 Jun 14 11:14 initrd.img-3.8.0-25-generic
16312 -rw-r--r--  1 root root 16636150 Jul 17 08:16 initrd.img-3.8.0-26-generic
   12 drwxr-xr-x  2 root root    12288 Oct 30  2012 lost+found
  174 -rw-r--r--  1 root root   176764 Dec  5  2012 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Dec  5  2012 memtest86+_multiboot.bin
 2277 -rw-------  1 root root  2320733 Oct  9  2012 System.map-3.5.0-17-generic
 2278 -rw-------  1 root root  2321612 Oct 19  2012 System.map-3.5.0-18-generic
 2277 -rw-------  1 root root  2321402 Nov 13  2012 System.map-3.5.0-19-generic
 2278 -rw-------  1 root root  2322150 Dec 11  2012 System.map-3.5.0-21-generic
 2279 -rw-------  1 root root  2323082 Jan  8  2013 System.map-3.5.0-22-generic
 2276 -rw-------  1 root root  2320304 Mar 25 16:29 System.map-3.5.0-27-generic
 2398 -rw-------  1 root root  2443743 May  1 13:12 System.map-3.8.0-19-generic
 2398 -rw-------  1 root root  2444283 Jun  6 17:19 System.map-3.8.0-25-generic
 2399 -rw-------  1 root root  2444419 Jun 17 18:19 System.map-3.8.0-26-generic
 5072 -rw-------  1 root root  5171760 Oct  9  2012 vmlinuz-3.5.0-17-generic
 5076 -rw-------  1 root root  5176048 Oct 19  2012 vmlinuz-3.5.0-18-generic
 5076 -rw-------  1 root root  5175696 Nov 13  2012 vmlinuz-3.5.0-19-generic
 5077 -rw-------  1 root root  5176464 Dec 11  2012 vmlinuz-3.5.0-21-generic
 5077 -rw-------  1 root root  5176592 Jan  8  2013 vmlinuz-3.5.0-22-generic
 5070 -rw-------  1 root root  5169520 Mar 25 16:29 vmlinuz-3.5.0-27-generic
 5265 -rw-------  1 root root  5368560 May  1 13:12 vmlinuz-3.8.0-19-generic
 5267 -rw-------  1 root root  5370096 Jun  6 17:19 vmlinuz-3.8.0-25-generic
 5266 -rw-------  1 root root  5369008 Jun 17 18:19 vmlinuz-3.8.0-26-generic
```

What can I remove out of there safely and still be able to boot?


Thanks for any help.

---

### Post by oldfred on 2013-07-17
You need to remove all but one old kernel. I always save 2, one that I boot with and one old one just in case.

I prefer to use synaptic. But if you are a server without a gui you have to do it all from command line. 

 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic

#current install:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by mistermsk on 2013-07-17
@[COLOR=#000000]oldfred

Thank your for your help. I did the** uname -a** and the **uname -r**[/COLOR][COLOR=#000000] to find out which kernel I was currently running. I did a **ls /boot** to find out what kernels I had in my boot directory. I found the two oldest ones and did the following command:

[/COLOR]```
sudo apt-get purge linux-image-3.5.0.17-generic linux-image-3.5.0-18-generic
```

This actually worked beautifully. I still got a lot of older kernels in there but there is room on my boot partition to so apt-get can complete. I finally did a **sudo reboot** to test and crossed my fingers.

This worked beautifully. 

Thanks again.

---

### Post by oldfred on 2013-07-17
Glad that worked.

I would still uninstall a lot more kernels. Somewhere users have posted scripts to automate the process, but the one script I copied deletes all but the current when it should not, so I need to figure out that count error.

---

