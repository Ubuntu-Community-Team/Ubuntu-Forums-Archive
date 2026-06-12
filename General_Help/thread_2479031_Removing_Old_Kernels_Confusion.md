---
title: "Removing Old Kernels Confusion"
date: 2022-09-12
forum: General Help
---

### Post by w-kym-wittal on 2022-09-12
I am having space issues and would like to remove some older kernels, but I have 2 different apps giving somewhat conflicting information about these kernels.

First, the space issue with '/boot', which I believe is causing large updates to show not enough space and backup claiming there is not enough temp space to run:
```

kym@ubuntu:~$ sudo du -hs /*
13M    /bin
151M    /boot
4.0K    /cdrom
5.3M    /dev
42M    /etc
du: cannot access '/home/kym/.gvfs': Permission denied
du: cannot access '/home/kym/xrdp_client': Permission denied
44G    /home
0    /initrd.img
0    /initrd.img.old
1.2G    /lib
6.1M    /lib32
4.0K    /lib64
0    /libnss3.so
16K    /lost+found
2.4T    /media
4.0K    /mnt
878M    /opt
du: cannot read directory '/proc/5401/task/5401/net': Invalid argument
du: cannot read directory '/proc/5401/net': Invalid argument
du: cannot access '/proc/6831/task/6831/fd/4': No such file or directory
du: cannot access '/proc/6831/task/6831/fdinfo/4': No such file or directory
du: cannot access '/proc/6831/fd/3': No such file or directory
du: cannot access '/proc/6831/fdinfo/3': No such file or directory
0    /proc
47G    /root
du: cannot access '/run/user/1000/doc': Permission denied
du: cannot access '/run/user/1000/gvfs': Permission denied
6.4M    /run
17M    /sbin
5.4G    /snap
204K    /srv
0    /sys
2.0M    /tmp
586M    /ums-9.2.0
298M    /ums-9.8.1
4.0K    /undef.log
6.5G    /usr
15G    /var
0    /vmlinuz
0    /vmlinuz.old
4.0K    /webmin-setup.out


```

The kernel information from app 1:
```

kym@ubuntu:~$ uname -r
4.15.0-180-generic
kym@ubuntu:~$ uname --all
Linux ubuntu 4.15.0-180-generic #189-Ubuntu SMP Wed May 18 14:13:57 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
kym@ubuntu:~$

```

Kernel information from app 2:
See screenshot attachment below.

My questions are:
1.  Can I safely remove the 2 older kernels? (will have to use Grub Customizer since it is the only app to see these additional kernels)
2.  Why are these older kernels still there after running removal commands such as 'sudo apt-get --purge autoremove' and 'sudo ukuu --purge-old-kernels'?
```

kym@ubuntu:~$ sudo apt-get --purge autoremove
[sudo] password for kym: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```
```

kym@ubuntu:~$ sudo ukuu --purge-old-kernels
[sudo] password for kym: 
ukuu v18.9.1
Distribution: Ubuntu 18.04.6 LTS
Architecture: amd64
Running kernel: 4.15.0-180-generic
Kernel version: 4.15.0.180.189
Cache: /home/kym/.cache/ukuu
Temp: /tmp/ukuu/ZsvcQsZM
----------------------------------------------------------------------
Found installed: 4.15.0-180.189
----------------------------------------------------------------------
Could not find any kernels to remove
----------------------------------------------------------------------

```
3.  How can I verify if these 2 older kernels are being used by something or are just remnants of past life?
4. Will removing these older kernels actually solve my space issue (for both large updates and backup)?  If not, any suggestions?

Thanks.

---

### Post by deadflowr on 2022-09-12
Post back the outputs for
```
dpkg -l | grep linux-image
df -h
```

That said, looking at the output I see 47G in /root
Why?

---

### Post by grahammechanical on 2022-09-12
The --all switch for the uname command does not mean list all kernels. According the uname man page it means "print all information in the following order". I have two kernels on my 20.04, the latest and the previous but uname only lists one kernel, the latest. It is beneficial to have at least two kernels, If an update breaks something in the OS using the latest kernel we can use Grub>Advanced Options for Ubuntu to boot into the previous kernel and see if we get a working OS.

Grub will show you all the kernels if you run this command:

```
sudo update-grub
```

Watch the printout. Grub>Advanced Options will let us boot any of the kernels listed.

Regards

---

### Post by w-kym-wittal on 2022-09-12
Output as requested:

```

kym@ubuntu:~$ dpkg -l | grep linux-image
rc  linux-image-2.6.32-38-server               2.6.32-38.83                                     amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-57-server               2.6.32-57.119                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-58-server               2.6.32-58.121                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-60-server               2.6.32-60.122                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-61-server               2.6.32-61.124                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-62-server               2.6.32-62.126                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-64-server               2.6.32-64.128                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-65-server               2.6.32-65.131                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-66-server               2.6.32-66.132                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-67-server               2.6.32-67.134                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-68-server               2.6.32-68.135                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-70-server               2.6.32-70.137                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-71-server               2.6.32-71.138                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-72-server               2.6.32-72.139                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-73-server               2.6.32-73.141                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-2.6.32-74-server               2.6.32-74.142                                    amd64        Linux kernel image for version 2.6.32 on x86_64
rc  linux-image-3.13.0-108-generic             3.13.0-108.155                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-109-generic             3.13.0-109.156                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-110-generic             3.13.0-110.157                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-116-generic             3.13.0-116.163                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-117-generic             3.13.0-117.164                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-101-generic              3.2.0-101.141                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-102-generic              3.2.0-102.142                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-104-generic              3.2.0-104.145                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-105-generic              3.2.0-105.146                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-106-generic              3.2.0-106.147                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-107-generic              3.2.0-107.148                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-109-generic              3.2.0-109.150                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-110-generic              3.2.0-110.151                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-113-generic              3.2.0-113.155                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-115-generic              3.2.0-115.157                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-116-generic              3.2.0-116.158                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-118-generic              3.2.0-118.161                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-119-generic              3.2.0-119.162                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-120-generic              3.2.0-120.163                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-99-generic               3.2.0-99.139                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-4.15.0-135-generic             4.15.0-135.139                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-136-generic             4.15.0-136.140                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-137-generic             4.15.0-137.141                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-139-generic             4.15.0-139.143                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-140-generic             4.15.0-140.144                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-142-generic             4.15.0-142.146                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-143-generic             4.15.0-143.147                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-144-generic             4.15.0-144.148                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-147-generic             4.15.0-147.151                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-151-generic             4.15.0-151.157                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-153-generic             4.15.0-153.160                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-154-generic             4.15.0-154.161                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-156-generic             4.15.0-156.163                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-158-generic             4.15.0-158.166                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-159-generic             4.15.0-159.167                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-161-generic             4.15.0-161.169                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-162-generic             4.15.0-162.170                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-163-generic             4.15.0-163.171                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-166-generic             4.15.0-166.174                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-167-generic             4.15.0-167.175                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-169-generic             4.15.0-169.177                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-171-generic             4.15.0-171.180                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-173-generic             4.15.0-173.182                                   amd64        Signed kernel image generic
rc  linux-image-4.15.0-175-generic             4.15.0-175.184                                   amd64        Signed kernel image generic
ii  linux-image-4.15.0-180-generic             4.15.0-180.189                                   amd64        Signed kernel image generic
rc  linux-image-4.4.0-154-generic              4.4.0-154.181                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-159-generic              4.4.0-159.187                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-161-generic              4.4.0-161.189                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-164-generic              4.4.0-164.192                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-165-generic              4.4.0-165.193                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-166-generic              4.4.0-166.195                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-168-generic              4.4.0-168.197                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-169-generic              4.4.0-169.198                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-170-generic              4.4.0-170.199                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-171-generic              4.4.0-171.200                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-173-generic              4.4.0-173.203                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-174-generic              4.4.0-174.204                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-176-generic              4.4.0-176.206                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-177-generic              4.4.0-177.207                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-178-generic              4.4.0-178.208                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-179-generic              4.4.0-179.209                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-184-generic              4.4.0-184.214                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-185-generic              4.4.0-185.215                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-186-generic              4.4.0-186.216                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-187-generic              4.4.0-187.217                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-189-generic              4.4.0-189.219                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-193-generic              4.4.0-193.224                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-194-generic              4.4.0-194.226                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-197-generic              4.4.0-197.229                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-198-generic              4.4.0-198.230                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-200-generic              4.4.0-200.232                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-201-generic              4.4.0-201.233                                    amd64        Signed kernel image generic
rc  linux-image-4.4.0-72-generic               4.4.0-72.93~14.04.1                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-108-generic       3.13.0-108.155                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-109-generic       3.13.0-109.156                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-110-generic       3.13.0-110.157                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-116-generic       3.13.0-116.163                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-117-generic       3.13.0-117.164                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-generic         4.4.0-72.93~14.04.1                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-unsigned-4.15.0-142-generic    4.15.0-142.146                                   amd64        Linux kernel image for version 4.15.0 on 64 bit x86 SMP
rc  linux-image-unsigned-4.4.0-143-generic     4.4.0-143.169~14.04.2                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-unsigned-4.4.0-144-generic     4.4.0-144.170~14.04.1                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-unsigned-4.4.0-146-generic     4.4.0-146.172                                    amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP

```

```

kym@ubuntu:~$ df -h
df: /home/kym/xrdp_client: Transport endpoint is not connected
Filesystem               Size  Used Avail Use% Mounted on
udev                     3.9G     0  3.9G   0% /dev
tmpfs                    798M  4.1M  794M   1% /run
/dev/mapper/ubuntu-root  129G  123G   13M 100% /
tmpfs                    3.9G  8.4M  3.9G   1% /dev/shm
tmpfs                    5.0M   52K  5.0M   2% /run/lock
tmpfs                    3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                92M   92M     0 100% /snap/gtk-common-themes/1535
/dev/loop6                18M   18M     0 100% /snap/gedit/626
/dev/loop1               9.0M  9.0M     0 100% /snap/canonical-livepatch/146
/dev/loop16              114M  114M     0 100% /snap/core/13308
/dev/loop3               401M  401M     0 100% /snap/gnome-3-38-2004/112
/dev/loop4               9.0M  9.0M     0 100% /snap/canonical-livepatch/138
/dev/loop12              128K  128K     0 100% /snap/bare/5
/dev/loop14              6.4M  6.4M     0 100% /snap/gedit/653
/dev/loop11              114M  114M     0 100% /snap/core/13425
/dev/loop8               347M  347M     0 100% /snap/gnome-3-38-2004/115
/dev/loop10              165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop2               163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop9                82M   82M     0 100% /snap/gtk-common-themes/1534
/dev/loop13               62M   62M     0 100% /snap/core20/1611
/dev/sdb                 202G  187G  4.9G  98% /media/Music
/dev/sdc                 688G  646G  7.0G  99% /media/Video
tmpfs                    798M   16K  798M   1% /run/user/116
tmpfs                    798M  2.5M  795M   1% /run/user/1000
/dev/sdd1                1.9T  1.6T  284G  85% /media/kym/Seagate Backup Plus Drive
/dev/loop17               56M   56M     0 100% /snap/core18/2560
/dev/loop5                64M   64M     0 100% /snap/core20/1623
/dev/loop7                56M   56M     0 100% /snap/core18/2566
kym@ubuntu:~$ 

```

To answer the question why /root is so large, I found the culprits:
1.  /root/.cache is 5.7G
2.  /root/.local/share/trash/files is 43.7G

Am I correct in assuming that the trash folder can just be deleted?  If not, what is the proper way to delete it?

Thanks.

---

### Post by w-kym-wittal on 2022-09-12
I ran the suggested 'sudo update-grub', it found all of the existing kernels.  Thanks for the clarification

```

kym@ubuntu:~$ sudo update-grub
[sudo] password for kym: 
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-180-generic
Found initrd image: /boot/initrd.img-4.15.0-180-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-3.13.0-112-generic
Found initrd image: /boot/initrd.img-3.13.0-112-generic
done
kym@ubuntu:~$ 

```

---

### Post by oldfred on 2022-09-12
Your 3.13 is from Trusty Tahr  or 14.04, so you do not need those kernels.
Looks like you have upgraded multiple times leaving older kernels. 
Not sure if dpkg or apt then housecleans those kernels as they are not really in list of installed files.

Left overs like this and probably other files elsewhere are why a new clean install & restore from backup may make sense.

---

### Post by Impavidus on 2022-09-13
I see you're running Ubuntu 18.04. Kernel 4.15 belongs to Ubuntu 18.04 and is still supported for 7 more months (but should be at 4.15.0-192 by now). update-grub and grub customizer (a great tool to break grub) also see a 4.4 and a 3.13 kernel, but those aren't properly installed or the other tools would see them too. There are some older kernels not fully removed (4.15, 4.4, 3.13, 3.2, 2.6.32). They cause clutter in apt's output and tell us this system has been upgraded from one LTS release to the next for ages. I think all the way from 10.04.

All that stuff in /root/.local/share/trash/files indicates you've used the file manager as root to delete a bunch of system files. Normally such files get managed by the package manager, so your system looks to be in a somewhat unclean state. So I agree with oldfred: it's time for a clean install.

Release upgrades usually work, but aren't perfect. I had one computer upgraded LTS to LTS from 6.06&#8594;8.04&#8594;10.04, but decided on a fresh install for 12.04 as too much cruft was building up.

---

### Post by w-kym-wittal on 2022-09-13
Thanks for the feedback and information.

Clearly I have never done a 'clean' install before.  How does one go about that without losing any installed apps or data?

---

### Post by Impavidus on 2022-09-13
Make a backup of your documents.

You can make a list of the manually installed packages and reinstall them after your fresh install. But this may not always work. Packages containing applications (but usually not those with libraries) that get installed by default are usually marked as manually installed, but you may no longer need need them if they have been replaced by another default. Many applications have been replaced since 10.04, but the old ones may still be available. You don't want those duplicates. On the other hand, some software is no longer available, so reinstalling the same packages may not be possible. When I fresh install a new Ubuntu release, I have a list of about 5 to 10 applications that I want to add. I just use synaptic or the command line for that.

Moving to a new release of Ubuntu isn't always straightforward, but you can't stay on 18.04 forever. If you have some home-made code, you may have to adapt it. Maybe you want to skip 20.04 and move directly to 22.04.

---

### Post by w-kym-wittal on 2022-09-15
Thanks for all of the assistance, very informative.

---

