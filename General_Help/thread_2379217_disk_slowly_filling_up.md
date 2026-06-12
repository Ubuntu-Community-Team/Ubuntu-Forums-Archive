---
title: "disk slowly filling up?"
date: 2017-12-02
forum: General Help
---

### Post by savager1 on 2017-12-02
Hi,

In the past I have installed Ubuntu 16.04 in various ways. I have tried installing with and without encryption and then running my SOE as a VM. What happened last time was still a mystery and have never gotten to the bottom of it. Initially, I thought it might be the fact that I was running Ubuntu encryption and then the Windows 7 SOE had it's own encryption (well Avecto)...I thought it might have been getting "double encrypted or something" as I set the VM to use only 200GB of the disk with 300GB for Ubuntu and not only did the VM grow larger than 200GB but kept on growing.

The reason for my background/history is that I think I have the same problem again with a fresh install and no SOE VM (basically using Ubuntu as a replacement for my SOE @ work). I am hoping with the disk slowly filling up that it is not just a matter of time before the disk starts getting overwhelmed and fills up in a matter of minutes until it's unusable. (also that's what happened last time, slowly increasing until one day it went crazy and just grew massively until all space used up).

I guess to start are there any troubleshooting tips I can do to try to figure out if something is wrong? 

At this stage I am doing this simple command and was concerned that it's growing when I am not really downloading much (youtube and browsingbut not really using any drive operations)
[Is this normal???]
```

December 2 @ 16:19
areblitz@areblitz-TECRA-Z50-C:~$ df |grep mapper
/dev/mapper/ubuntu--vg-root 475192424 36567192 414463748   9% /

December 2 @ 22:16
areblitz@areblitz-TECRA-Z50-C:~$ df |grep mapper
/dev/mapper/ubuntu--vg-root 475192424 36627000 414403940   9% /

December 2 @ 23:04
areblitz@areblitz-TECRA-Z50-C:~$ df |grep mapper
/dev/mapper/ubuntu--vg-root 475192424 36723476 414307464   9% /

```




General checks:

```

areblitz@areblitz-TECRA-Z50-C:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.8G     0  7.8G   0% /dev
tmpfs                        1.6G  9.6M  1.6G   1% /run
/dev/mapper/ubuntu--vg-root  454G   35G  396G   9% /
tmpfs                        7.8G   31M  7.8G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1                    472M  111M  337M  25% /boot
tmpfs                        1.6G   88K  1.6G   1% /run/user/1000
/home/areblitz/.Private      454G   35G  396G   9% /home/areblitz


areblitz@areblitz-TECRA-Z50-C:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                         2038374    538  2037836    1% /dev
tmpfs                        2043756    839  2042917    1% /run
/dev/mapper/ubuntu--vg-root 30187520 271004 29916516    1% /
tmpfs                        2043756     61  2043695    1% /dev/shm
tmpfs                        2043756      7  2043749    1% /run/lock
tmpfs                        2043756     16  2043740    1% /sys/fs/cgroup
/dev/sda1                     124928    308   124620    1% /boot
tmpfs                        2043756     37  2043719    1% /run/user/1000
/home/areblitz/.Private     30187520 271004 29916516    1% /home/areblitz

```






(I don't believe it's hardware as it runs the SOE Windows 7 just fine - my line of thinking is that if there was an issue with the disk, I thought I might have seen it there)

---

