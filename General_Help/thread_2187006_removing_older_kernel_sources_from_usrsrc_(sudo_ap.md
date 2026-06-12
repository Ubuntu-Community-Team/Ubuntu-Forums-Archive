---
title: "removing older kernel sources from /usr/src (sudo apt-get purge not working)"
date: 2013-11-10
forum: General Help
---

### Post by chiara-carlino on 2013-11-10
hi everybody!
it's my first post to this forum because any answer to any question or problem is usually already given... you are great!
but this time I can't get through it.

my root partition is full (it was 10GB and now it only has 213 MB free :-/) and I see really a lot of space used up by old kernels. 

I already followed a couple of guides about how to clean it up and did autoclean, autoremove and apt-get purge for every unused kernel except the one I'm using and the one before it.
still, in the /usr/src folder I see folders for kernels going back to 3.2.0 (while I'm actually using 3.8.0-31). I guess this might have to do with a previous cleanup where I only used uninstall instead of purge (might it?).

If I try sudo apt-get purge linux-headers-3.2.0-24 the output is that the package is impossible to find (I can copy paste output if you like, but it's in italian, sorry).
I tried dpkg -S /usr/src/* and I got a lot of "no path corresponding to /usr/src/linux-headers-3.2.0-48-generic-pae" and similar (same as before: I would copy paste the actual output but it's in italian).

so, how do I remove these folders? they are using up quite a lot of space and I don't know how else I could free up some.

thank you very much!

chiara

---

### Post by dargaud2 on 2013-11-10
Do "ls -alF /boot" to see which versions you have installed, then do the following on all but the last two: "sudo aptitude remove linux-image-3.8.0-31-generic"

---

### Post by jeanjd63 on 2013-11-10
Hello, 

Could you give the return of the command :
[B]dpkg  -l  |  grep  linux-

@+[/B]

---

### Post by chiara-carlino on 2013-11-10
@dargaud2
here it is (quite long! it goes back to those old kernel versions):

```
total 578456
drwxr-xr-x  3 root root     8192 nov 10 14:41 ./
drwxr-xr-x 25 root root     4096 nov 10 14:40 ../
-rw-r--r--  1 root root   740294 apr 20  2012 abi-3.0.0-19-generic-pae
-rw-r--r--  1 root root   797082 nov 15  2012 abi-3.2.0-34-generic
-rw-r--r--  1 root root   801759 nov 15  2012 abi-3.2.0-34-generic-pae
-rw-r--r--  1 root root   797121 dic  5  2012 abi-3.2.0-35-generic
-rw-r--r--  1 root root   801798 dic  5  2012 abi-3.2.0-35-generic-pae
-rw-r--r--  1 root root   797231 gen  8  2013 abi-3.2.0-36-generic
-rw-r--r--  1 root root   801908 gen  9  2013 abi-3.2.0-36-generic-pae
-rw-r--r--  1 root root   797231 gen 24  2013 abi-3.2.0-37-generic
-rw-r--r--  1 root root   801908 gen 24  2013 abi-3.2.0-37-generic-pae
-rw-r--r--  1 root root   799443 mar 25  2013 abi-3.2.0-40-generic
-rw-r--r--  1 root root   804120 mar 25  2013 abi-3.2.0-40-generic-pae
-rw-r--r--  1 root root   799506 apr 25  2013 abi-3.2.0-41-generic
-rw-r--r--  1 root root   804183 apr 25  2013 abi-3.2.0-41-generic-pae
-rw-r--r--  1 root root   799656 mag 16 21:43 abi-3.2.0-44-generic
-rw-r--r--  1 root root   804333 mag 16 21:59 abi-3.2.0-44-generic-pae
-rw-r--r--  1 root root   799656 mag 29 23:18 abi-3.2.0-45-generic
-rw-r--r--  1 root root   804333 mag 29 23:32 abi-3.2.0-45-generic-pae
-rw-r--r--  1 root root   799875 giu  6 22:53 abi-3.2.0-48-generic
-rw-r--r--  1 root root   804552 giu  6 23:07 abi-3.2.0-48-generic-pae
-rw-r--r--  1 root root   799875 lug 24 23:30 abi-3.2.0-51-generic
-rw-r--r--  1 root root   804552 lug 24 23:44 abi-3.2.0-51-generic-pae
-rw-r--r--  1 root root   799875 lug 26 19:31 abi-3.2.0-52-generic
-rw-r--r--  1 root root   804552 lug 26 19:46 abi-3.2.0-52-generic-pae
-rw-r--r--  1 root root   919661 ago 22 23:21 abi-3.8.0-30-generic
-rw-r--r--  1 root root   919745 set 10 22:29 abi-3.8.0-31-generic
-rw-r--r--  1 root root   919810 ott 23 11:42 abi-3.8.0-33-generic
-rw-r--r--  1 root root   142089 apr 20  2012 config-3.0.0-19-generic-pae
-rw-r--r--  1 root root   147514 nov 15  2012 config-3.2.0-34-generic
-rw-r--r--  1 root root   147452 nov 15  2012 config-3.2.0-34-generic-pae
-rw-r--r--  1 root root   147514 dic  5  2012 config-3.2.0-35-generic
-rw-r--r--  1 root root   147452 dic  5  2012 config-3.2.0-35-generic-pae
-rw-r--r--  1 root root   147514 gen  8  2013 config-3.2.0-36-generic
-rw-r--r--  1 root root   147452 gen  9  2013 config-3.2.0-36-generic-pae
-rw-r--r--  1 root root   147514 gen 24  2013 config-3.2.0-37-generic
-rw-r--r--  1 root root   147452 gen 24  2013 config-3.2.0-37-generic-pae
-rw-r--r--  1 root root   147595 mar 25  2013 config-3.2.0-40-generic
-rw-r--r--  1 root root   147533 mar 25  2013 config-3.2.0-40-generic-pae
-rw-r--r--  1 root root   147631 apr 25  2013 config-3.2.0-41-generic
-rw-r--r--  1 root root   147569 apr 25  2013 config-3.2.0-41-generic-pae
-rw-r--r--  1 root root   147631 mag 16 21:43 config-3.2.0-44-generic
-rw-r--r--  1 root root   147569 mag 16 21:59 config-3.2.0-44-generic-pae
-rw-r--r--  1 root root   147631 mag 29 23:18 config-3.2.0-45-generic
-rw-r--r--  1 root root   147569 mag 29 23:32 config-3.2.0-45-generic-pae
-rw-r--r--  1 root root   147631 giu  6 22:53 config-3.2.0-48-generic
-rw-r--r--  1 root root   147569 giu  6 23:07 config-3.2.0-48-generic-pae
-rw-r--r--  1 root root   147638 lug 24 23:30 config-3.2.0-51-generic
-rw-r--r--  1 root root   147576 lug 24 23:44 config-3.2.0-51-generic-pae
-rw-r--r--  1 root root   147638 lug 26 19:31 config-3.2.0-52-generic
-rw-r--r--  1 root root   147576 lug 26 19:46 config-3.2.0-52-generic-pae
-rw-r--r--  1 root root   154960 ago 22 23:21 config-3.8.0-30-generic
-rw-r--r--  1 root root   154960 set 10 22:29 config-3.8.0-31-generic
-rw-r--r--  1 root root   154961 ott 23 11:42 config-3.8.0-33-generic
drwxr-xr-x  5 root root     8192 nov 10 14:41 grub/
-rw-r--r--  1 root root 13692408 mag 13  2012 initrd.img-3.0.0-19-generic-pae
-rw-r--r--  1 root root 14138288 dic  1  2012 initrd.img-3.2.0-34-generic
-rw-r--r--  1 root root 14148827 dic  1  2012 initrd.img-3.2.0-34-generic-pae
-rw-r--r--  1 root root 14146665 dic 21  2012 initrd.img-3.2.0-35-generic
-rw-r--r--  1 root root 14157067 dic 21  2012 initrd.img-3.2.0-35-generic-pae
-rw-r--r--  1 root root 14150688 gen 19  2013 initrd.img-3.2.0-36-generic
-rw-r--r--  1 root root 14164718 feb  5  2013 initrd.img-3.2.0-36-generic-pae
-rw-r--r--  1 root root 14147256 feb  5  2013 initrd.img-3.2.0-37-generic
-rw-r--r--  1 root root 14154879 feb  5  2013 initrd.img-3.2.0-37-generic-pae
-rw-r--r--  1 root root 14175730 mag  1  2013 initrd.img-3.2.0-40-generic
-rw-r--r--  1 root root 14185323 mag  1  2013 initrd.img-3.2.0-40-generic-pae
-rw-r--r--  1 root root 14177467 mag 13 21:50 initrd.img-3.2.0-41-generic
-rw-r--r--  1 root root 14186754 mag 13 21:51 initrd.img-3.2.0-41-generic-pae
-rw-r--r--  1 root root 14177921 mag 25 13:41 initrd.img-3.2.0-44-generic
-rw-r--r--  1 root root 14187317 mag 25 13:42 initrd.img-3.2.0-44-generic-pae
-rw-r--r--  1 root root 14183999 giu 12 21:12 initrd.img-3.2.0-45-generic
-rw-r--r--  1 root root 14193732 giu 12 21:14 initrd.img-3.2.0-45-generic-pae
-rw-r--r--  1 root root 14187721 giu 30 03:58 initrd.img-3.2.0-48-generic
-rw-r--r--  1 root root 14198630 giu 30 03:59 initrd.img-3.2.0-48-generic-pae
-rw-r--r--  1 root root 14183691 ago 20 21:56 initrd.img-3.2.0-51-generic
-rw-r--r--  1 root root 14195108 ago 20 21:58 initrd.img-3.2.0-51-generic-pae
-rw-r--r--  1 root root 14185489 ago 20 21:59 initrd.img-3.2.0-52-generic
-rw-r--r--  1 root root 14194239 ago 20 22:01 initrd.img-3.2.0-52-generic-pae
-rw-r--r--  1 root root 16203148 set  6 22:56 initrd.img-3.8.0-30-generic
-rw-r--r--  1 root root 16213503 set 30 20:44 initrd.img-3.8.0-31-generic
-rw-r--r--  1 root root 16211782 nov 10 14:41 initrd.img-3.8.0-33-generic
-rw-r--r--  1 root root   176764 dic  5  2012 memtest86+.bin
-rw-r--r--  1 root root   178944 dic  5  2012 memtest86+_multiboot.bin
-rw-------  1 root root  2189099 apr 20  2012 System.map-3.0.0-19-generic-pae
-rw-------  1 root root  2252451 nov 15  2012 System.map-3.2.0-34-generic
-rw-------  1 root root  2313866 nov 15  2012 System.map-3.2.0-34-generic-pae
-rw-------  1 root root  2252128 dic  5  2012 System.map-3.2.0-35-generic
-rw-------  1 root root  2314162 dic  5  2012 System.map-3.2.0-35-generic-pae
-rw-------  1 root root  2252687 gen  8  2013 System.map-3.2.0-36-generic
-rw-------  1 root root  2314721 gen  9  2013 System.map-3.2.0-36-generic-pae
-rw-------  1 root root  2252511 gen 24  2013 System.map-3.2.0-37-generic
-rw-------  1 root root  2314545 gen 24  2013 System.map-3.2.0-37-generic-pae
-rw-------  1 root root  2256417 mar 25  2013 System.map-3.2.0-40-generic
-rw-------  1 root root  2318451 mar 25  2013 System.map-3.2.0-40-generic-pae
-rw-------  1 root root  2256808 apr 25  2013 System.map-3.2.0-41-generic
-rw-------  1 root root  2318965 apr 25  2013 System.map-3.2.0-41-generic-pae
-rw-------  1 root root  2257186 mag 16 21:43 System.map-3.2.0-44-generic
-rw-------  1 root root  2319343 mag 16 21:59 System.map-3.2.0-44-generic-pae
-rw-------  1 root root  2257186 mag 29 23:18 System.map-3.2.0-45-generic
-rw-------  1 root root  2319343 mag 29 23:32 System.map-3.2.0-45-generic-pae
-rw-------  1 root root  2258125 giu  6 22:53 System.map-3.2.0-48-generic
-rw-------  1 root root  2320444 giu  6 23:07 System.map-3.2.0-48-generic-pae
-rw-------  1 root root  2258337 lug 24 23:30 System.map-3.2.0-51-generic
-rw-------  1 root root  2320656 lug 24 23:44 System.map-3.2.0-51-generic-pae
-rw-------  1 root root  2258337 lug 26 19:31 System.map-3.2.0-52-generic
-rw-------  1 root root  2320656 lug 26 19:46 System.map-3.2.0-52-generic-pae
-rw-------  1 root root  3062704 ago 22 23:21 System.map-3.8.0-30-generic
-rw-------  1 root root  3062541 set 10 22:29 System.map-3.8.0-31-generic
-rw-------  1 root root  3062707 ott 23 11:42 System.map-3.8.0-33-generic
-rw-------  1 root root     1219 apr 20  2012 vmcoreinfo-3.0.0-19-generic-pae
-rw-------  1 root root  4795040 apr 20  2012 vmlinuz-3.0.0-19-generic-pae
-rw-------  1 root root  4862688 nov 15  2012 vmlinuz-3.2.0-34-generic
-rw-------  1 root root  5017504 nov 15  2012 vmlinuz-3.2.0-34-generic-pae
-rw-------  1 root root  4863712 dic  5  2012 vmlinuz-3.2.0-35-generic
-rw-------  1 root root  5017984 dic  5  2012 vmlinuz-3.2.0-35-generic-pae
-rw-------  1 root root  4864480 gen  8  2013 vmlinuz-3.2.0-36-generic
-rw-------  1 root root  5019456 gen  9  2013 vmlinuz-3.2.0-36-generic-pae
-rw-------  1 root root  4864928 gen 24  2013 vmlinuz-3.2.0-37-generic
-rw-------  1 root root  5018144 gen 24  2013 vmlinuz-3.2.0-37-generic-pae
-rw-------  1 root root  4867264 mar 25  2013 vmlinuz-3.2.0-40-generic
-rw-------  1 root root  5022272 mar 25  2013 vmlinuz-3.2.0-40-generic-pae
-rw-------  1 root root  4868896 apr 25  2013 vmlinuz-3.2.0-41-generic
-rw-------  1 root root  5023424 apr 25  2013 vmlinuz-3.2.0-41-generic-pae
-rw-------  1 root root  4870880 mag 16 21:43 vmlinuz-3.2.0-44-generic
-rw-------  1 root root  5024224 mag 16 21:59 vmlinuz-3.2.0-44-generic-pae
-rw-------  1 root root  4870880 mag 29 23:18 vmlinuz-3.2.0-45-generic
-rw-------  1 root root  5024224 mag 29 23:32 vmlinuz-3.2.0-45-generic-pae
-rw-------  1 root root  4872608 giu  6 22:53 vmlinuz-3.2.0-48-generic
-rw-------  1 root root  5026432 giu  6 23:07 vmlinuz-3.2.0-48-generic-pae
-rw-------  1 root root  4872544 lug 24 23:30 vmlinuz-3.2.0-51-generic
-rw-------  1 root root  5028224 lug 24 23:44 vmlinuz-3.2.0-51-generic-pae
-rw-------  1 root root  4872544 lug 26 19:31 vmlinuz-3.2.0-52-generic
-rw-------  1 root root  5028032 lug 26 19:46 vmlinuz-3.2.0-52-generic-pae
-rw-------  1 root root  5361936 ago 22 23:21 vmlinuz-3.8.0-30-generic
-rw-------  1 root root  5362320 set 10 22:29 vmlinuz-3.8.0-31-generic
-rw-------  1 root root  5364816 ott 23 11:42 vmlinuz-3.8.0-33-generic
```

@jeanjd63 
here it is (much shorter, I guess it only shows the kernels really in use)

```
ii  linux-firmware                            1.106                                  all          Firmware for Linux kernel drivers
ii  linux-generic                             3.8.0.33.51                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.8.0-30                    3.8.0-30.44                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic            3.8.0-30.44                            amd64        Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-31                    3.8.0-31.46                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic            3.8.0-31.46                            amd64        Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-33                    3.8.0-33.48                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-33-generic            3.8.0-33.48                            amd64        Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                     3.8.0.33.51                            amd64        Generic Linux kernel headers
ii  linux-image-3.8.0-30-generic              3.8.0-30.44                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-31-generic              3.8.0-31.46                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-33-generic              3.8.0-33.48                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-31-generic        3.8.0-31.46                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-33-generic        3.8.0-33.48                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.8.0.33.51                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                      3.8.0-33.48                            amd64        Linux Kernel Headers for development
ii  linux-sound-base                          1.0.25+dfsg-0ubuntu4                   all          base package for ALSA and OSS sound systems
ii  syslinux-common                           3:4.05+dfsg-6+deb7u2ubuntu1            all          collection of boot loaders (common files)
ii  syslinux-legacy                           2:3.63+dfsg-2ubuntu5                   amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

what's the difference between the two commands?
and... what now? :)

thanks a lot!!

---

### Post by jeanjd63 on 2013-11-10
You can first suppress old kernels in /boot :
[B]sudo  rm  /boot/*[COLOR=#000000]3.0.0*
[/COLOR]sudo  rm  /boot/*[/B][COLOR=#000000]**3.2.0***

and old headers in /usr/src

**sudo  rm -r /usr/src/**[/COLOR]*****[COLOR=#000000]**3.0.0***
[/COLOR]**[COLOR=#000000]sudo  rm -r /usr/src/[/COLOR]**[B]*[COLOR=#000000]3.0.2*

[/COLOR][/B][COLOR=#000000]
Then you can do a :

[B]df  -h
[/B]to verify if it is ok now[/COLOR][COLOR=#000000][/COLOR]

---

### Post by chiara-carlino on 2013-11-10
ok with the first one but then

 sudo rm -r /usr/src/*3.0.0*
rm: cannot remove &#8216;/usr/src/*3.0.0*&#8217;: No such file or directory

---

### Post by jeanjd63 on 2013-11-10
Can you give the return for :
[B]sudo  ls -l  /usr/src

[/B]and for verify do a :[B]
sudo  ls  -l  /boot[/B]

---

### Post by deadflowr on 2013-11-10
You can remove the older kernels much easier and safer through package managers such as synaptic, or 
if you must, the software center.
Simply run the uname -a command to get your currrent kernel and remove everyone with a number older then that.
You should probably try not removing any packages such as linux-headers( something without a number) if they are listed.
Simply look for the packages linux-image and linux-headers.

---

### Post by chiara-carlino on 2013-11-10
@jeanjd63
my fault, simply there actually was no folder for *3.0.0*, everything fine for *3.2.0*

@deadflowr
I tried, but those src stay there even after trying purge, autoremove and uninstall...

---

### Post by jeanjd63 on 2013-11-10
Ok now could you reply for :
[B]sudo  ls  -l  /boot
[/B]and[B]
df -h[/B]

---

### Post by chiara-carlino on 2013-11-10
sudo ls -l /boot

total 75844
-rw-r--r-- 1 root root   919661 ago 22 23:21 abi-3.8.0-30-generic
-rw-r--r-- 1 root root   919745 set 10 22:29 abi-3.8.0-31-generic
-rw-r--r-- 1 root root   919810 ott 23 11:42 abi-3.8.0-33-generic
-rw-r--r-- 1 root root   154960 ago 22 23:21 config-3.8.0-30-generic
-rw-r--r-- 1 root root   154960 set 10 22:29 config-3.8.0-31-generic
-rw-r--r-- 1 root root   154961 ott 23 11:42 config-3.8.0-33-generic
drwxr-xr-x 5 root root     8192 nov 10 14:41 grub
-rw-r--r-- 1 root root 16203148 set  6 22:56 initrd.img-3.8.0-30-generic
-rw-r--r-- 1 root root 16213503 set 30 20:44 initrd.img-3.8.0-31-generic
-rw-r--r-- 1 root root 16211782 nov 10 14:41 initrd.img-3.8.0-33-generic
-rw-r--r-- 1 root root   176764 dic  5  2012 memtest86+.bin
-rw-r--r-- 1 root root   178944 dic  5  2012 memtest86+_multiboot.bin
-rw------- 1 root root  3062704 ago 22 23:21 System.map-3.8.0-30-generic
-rw------- 1 root root  3062541 set 10 22:29 System.map-3.8.0-31-generic
-rw------- 1 root root  3062707 ott 23 11:42 System.map-3.8.0-33-generic
-rw------- 1 root root  5361936 ago 22 23:21 vmlinuz-3.8.0-30-generic
-rw------- 1 root root  5362320 set 10 22:29 vmlinuz-3.8.0-31-generic
-rw------- 1 root root  5364816 ott 23 11:42 vmlinuz-3.8.0-33-generic

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        11G  6,7G  3,0G  70% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            2,9G  4,0K  2,9G   1% /dev
tmpfs           589M  1,1M  588M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            2,9G  156K  2,9G   1% /run/shm
none            100M   20K  100M   1% /run/user
/dev/sda8       366G  223G  143G  61% /dati
/dev/sda6        16G  5,2G   10G  35% /home
/dev/sda1       100M   25M   76M  25% /media/chiara/SYSTEM


I think it's fine now... I just way to see if it still works after a restart ;-)

thanks!!

---

### Post by fantab on 2013-11-10
Deleted: As op seems to have solved the issue.

---

### Post by jeanjd63 on 2013-11-10
Ok Your problem seems to be resolved. In the future remind to remove older kernels and headers. You can keep only the 3 recents one.

By By

---

### Post by deadflowr on 2013-11-10
> **chiara-carlino said:**
> 
@deadflowr
I tried, but those src stay there even after trying purge, autoremove and uninstall...

 What is the output of the apt-get purge command you are using.
It should generate a long string of commands.
Listing a long list of items being removed. Per kernel.
Having as many old kernel as you have listed, I would assume it would take a minute or two to run a purge on them.

---

### Post by chiara-carlino on 2013-11-10
If I tried sudo apt-get purge linux-headers-3.2.0-24 the output was that the package is impossible to find

---

### Post by jeanjd63 on 2013-11-10
> **chiara-carlino said:**
> If I tried sudo apt-get purge linux-headers-3.2.0-24 the output was that the package is impossible to find


It is normal the response of :
**dpkg -l | grep linux-** 

was post #4

 > 
[COLOR=#000000]ii linux-firmware 1.106 all Firmware for Linux kernel drivers[/COLOR]
[COLOR=#000000]ii linux-generic 3.8.0.33.51 amd64 Complete Generic Linux kernel and headers[/COLOR]
[COLOR=#000000]ii linux-headers-3.8.0-30 3.8.0-30.44 all Header files related to Linux kernel version 3.8.0[/COLOR]
[COLOR=#000000]ii linux-headers-3.8.0-30-generic 3.8.0-30.44 amd64 Linux kernel headers for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-headers-3.8.0-31 3.8.0-31.46 all Header files related to Linux kernel version 3.8.0[/COLOR]
[COLOR=#000000]ii linux-headers-3.8.0-31-generic 3.8.0-31.46 amd64 Linux kernel headers for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-headers-3.8.0-33 3.8.0-33.48 all Header files related to Linux kernel version 3.8.0[/COLOR]
[COLOR=#000000]ii linux-headers-3.8.0-33-generic 3.8.0-33.48 amd64 Linux kernel headers for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-headers-generic 3.8.0.33.51 amd64 Generic Linux kernel headers[/COLOR]
[COLOR=#000000]ii linux-image-3.8.0-30-generic 3.8.0-30.44 amd64 Linux kernel image for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-image-3.8.0-31-generic 3.8.0-31.46 amd64 Linux kernel image for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-image-3.8.0-33-generic 3.8.0-33.48 amd64 Linux kernel image for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-image-extra-3.8.0-30-generic 3.8.0-30.44 amd64 Linux kernel image for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-image-extra-3.8.0-31-generic 3.8.0-31.46 amd64 Linux kernel image for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-image-extra-3.8.0-33-generic 3.8.0-33.48 amd64 Linux kernel image for version 3.8.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-image-generic 3.8.0.33.51 amd64 Generic Linux kernel image[/COLOR]
[COLOR=#000000]ii linux-libc-dev:amd64 3.8.0-33.48 amd64 Linux Kernel Headers for development[/COLOR]
[COLOR=#000000]ii linux-sound-base 1.0.25+dfsg-0ubuntu4 all base package for ALSA and OSS sound systems[/COLOR]
[COLOR=#000000]ii syslinux-common 3:4.05+dfsg-6+deb7u2ubuntu1 all collection of boot loaders (common files)[/COLOR]
[COLOR=#000000]ii syslinux-legacy 2:3.63+dfsg-2ubuntu5 amd64 Bootloader for Linux/i386 using MS-DOS floppies[/COLOR]


and there is no trace of linux-headers-3.2.0-24

---

### Post by deadflowr on 2013-11-10
> **chiara-carlino said:**
> If I tried sudo apt-get purge linux-headers-3.2.0-24 the output was that the package is impossible to find

That's because the package linux-headers-3.2-0-24 doesn't exist.
The package would be something like linux-headers-3.2-0-24.39-precise01. or whichever version you're on.

Are they still listed in /usr/src?

---

### Post by oldos2er on 2013-11-10
> **jeanjd63 said:**
> You can first suppress old kernels in /boot :
**sudo  rm **

Rather than suggesting people "rm" kernels offer the safer method of using a package manager. Thanks.

---

### Post by jeanjd63 on 2013-11-10
> **oldos2er said:**
> Rather than suggesting people "rm" kernels offer the safer method of using a package manager. Thanks.


Well if you analyse the post #4 you will see there is no référence in dpkg for the kernel suppress with rm. And there is no other méthod for suppress this kernels. Ok ?

---

### Post by deadflowr on 2013-11-10
By running the rm command, you only remove the files from which folder you remove them from.
You miss files anywhere else.
Example of the files on my current linux-image for trusty
```
 /./boot
/boot/System.map-3.12.0-2-generic
/boot/abi-3.12.0-2-generic
/boot/config-3.12.0-2-generic
/boot/vmlinuz-3.12.0-2-generic
/lib
/lib/firmware
/lib/firmware/3.12.0-2-generic
/lib/firmware/3.12.0-2-generic/3com
/lib/firmware/3.12.0-2-generic/3com/typhoon.bin
/lib/firmware/3.12.0-2-generic/bnx2
/lib/firmware/3.12.0-2-generic/bnx2/bnx2-mips-06-6.2.3.fw
/lib/firmware/3.12.0-2-generic/bnx2/bnx2-mips-09-6.2.1b.fw
/lib/firmware/3.12.0-2-generic/bnx2/bnx2-rv2p-06-6.0.15.fw
/lib/firmware/3.12.0-2-generic/bnx2/bnx2-rv2p-09-6.0.17.fw
/lib/firmware/3.12.0-2-generic/bnx2/bnx2-rv2p-09ax-6.0.17.fw
/lib/firmware/3.12.0-2-generic/bnx2x
/lib/firmware/3.12.0-2-generic/bnx2x/bnx2x-e1-7.8.17.0.fw
/lib/firmware/3.12.0-2-generic/bnx2x/bnx2x-e1h-7.8.17.0.fw
/lib/firmware/3.12.0-2-generic/bnx2x/bnx2x-e2-7.8.17.0.fw
/lib/firmware/3.12.0-2-generic/e100
/lib/firmware/3.12.0-2-generic/e100/d101m_ucode.bin
/lib/firmware/3.12.0-2-generic/e100/d101s_ucode.bin
/lib/firmware/3.12.0-2-generic/e100/d102e_ucode.bin
/lib/firmware/3.12.0-2-generic/emi26
/lib/firmware/3.12.0-2-generic/emi26/bitstream.fw
/lib/firmware/3.12.0-2-generic/emi26/firmware.fw
/lib/firmware/3.12.0-2-generic/emi26/loader.fw
/lib/firmware/3.12.0-2-generic/emi62
/lib/firmware/3.12.0-2-generic/emi62/bitstream.fw
/lib/firmware/3.12.0-2-generic/emi62/loader.fw
/lib/firmware/3.12.0-2-generic/emi62/midi.fw
/lib/firmware/3.12.0-2-generic/emi62/spdif.fw
/lib/firmware/3.12.0-2-generic/korg
/lib/firmware/3.12.0-2-generic/korg/k1212.dsp
/lib/firmware/3.12.0-2-generic/qlogic
/lib/firmware/3.12.0-2-generic/qlogic/1040.bin
/lib/firmware/3.12.0-2-generic/qlogic/12160.bin
/lib/firmware/3.12.0-2-generic/qlogic/1280.bin
/lib/firmware/3.12.0-2-generic/qlogic/sd7220.fw
/lib/firmware/3.12.0-2-generic/tigon
/lib/firmware/3.12.0-2-generic/tigon/tg3.bin
/lib/firmware/3.12.0-2-generic/tigon/tg3_tso.bin
/lib/firmware/3.12.0-2-generic/tigon/tg3_tso5.bin
/lib/firmware/3.12.0-2-generic/whiteheat.fw
/lib/firmware/3.12.0-2-generic/whiteheat_loader.fw
/lib/modules
/lib/modules/3.12.0-2-generic
/lib/modules/3.12.0-2-generic/initrd
/lib/modules/3.12.0-2-generic/kernel
/lib/modules/3.12.0-2-generic/kernel/arch
/lib/modules/3.12.0-2-generic/kernel/arch/x86
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/ablk_helper.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/aes-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/aesni-intel.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/blowfish-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/camellia-aesni-avx-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/camellia-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/cast5-avx-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/cast6-avx-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/crc32-pclmul.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/crct10dif-pclmul.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/ghash-clmulni-intel.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/glue_helper.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/salsa20-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/serpent-avx-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/serpent-sse2-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/sha1-ssse3.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/sha256-ssse3.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/sha512-ssse3.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/twofish-avx-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/twofish-x86_64-3way.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/crypto/twofish-x86_64.ko
/lib/modules/3.12.0-2-generic/kernel/arch/x86/kernel
/lib/modules/3.12.0-2-generic/kernel/arch/x86/kernel/cpu
/lib/modules/3.12.0-2-generic/kernel/arch/x86/kernel/cpu/mcheck
/usr
/usr/share
/usr/share/doc
/usr/share/doc/linux-image-3.12.0-2-generic
/usr/share/doc/linux-image-3.12.0-2-generic/changelog.Debian.gz
/usr/share/doc/linux-image-3.12.0-2-generic/copyright

```

I cut this way down.
But you can see that by only rm-ing a few files doesn't help in the overall removal.
And suppressing it only leaves a giant mess.

Using dpkg, sudo or a package manager will clean all these files up nicely.

---

### Post by jeanjd63 on 2013-11-10
For the last time i repeat that dpkg can only remove packages referenced in his base. In the present case the packages removed were not référenced. 
You can see the return for the apt-get command in post #15  --> package not found.

.final

---

### Post by deadflowr on 2013-11-10
> **jeanjd63 said:**
> For the last time i repeat that dpkg can only remove packages referenced in his base. In the present case the packages removed were not référenced. 
You can see the return for the apt-get command in post #15  --> package not found.

.final

Deleted.

Nevermind, was thinking something else.

But it stands that removal through a package manager is the best method.

---

