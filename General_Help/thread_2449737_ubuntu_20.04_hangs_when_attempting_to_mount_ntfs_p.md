---
title: "ubuntu 20.04 hangs when attempting to mount ntfs partition"
date: 2020-09-01
forum: General Help
---

### Post by alemsqdt on 2020-09-01
Hello,  The issue I have is that my system completely hangs when I mount a ntfs partition.

  I am using a Ubuntu 20.04 system with dual boot organized as follows: 

Ext4 partition (/dev/sda7) mounted on /home - which is automatically mounted when I turn on my computer, and is my Ubuntu 20.04 system 
NTFS partition (/dev/sda3) unmounted by default 
Other smaller sections such as swap... etc.   

When I boot I can choose alternatively to start in the NTFS partition with Windows10, and it works OK. However, I usually start in the Ext4 (ubuntu). From ubuntu I attempt to mount the NTFS partition manually simply by navigating to "+ Other locations" (I guess that's the EN translation of my ES version) and click on the OS disc icon. This usually hanged the computer for few seconds up to 1-2 minutes. But now it turned to be a persistent hang (more than 15 min) from where the systems does not recover and I am forced to restart. 

When it hangs I can barely move the mouse, and nothing else works except Alt+Ctrl+F4 (I don't know what to do there anyway) and Alt+Ctrl+F1 from where I can restart the computer. But restarting doesn't help  
I will give some other info below 
I appreciate any help 
Cheers!

---

### Post by alemsqdt on 2020-09-01
Things I have already done: 

1---
I already tried doing this:
```
ntfsfix /dev/sda3
```
It returned
```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda3 was processed successfully.

```
and 
```
sudo mount -t ntfs-3g /dev/sda3 /media/alemsqdt/
```

It hanged... 

2----
A similar post I found was (in mint, although): 
[https://forums.linuxmint.com/viewtopic.php?t=296629](https://forums.linuxmint.com/viewtopic.php?t=296629)
But the solution there was to change the NTFS system by an Ext4 system but I can't since I need that partition to run in Windows.

3--- 
I did 
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

and restarted
But It still hangs (always when attempting to mount ntfs, otherwise the system works perfectly)

4----
This has happened to me once before, using Ubuntu 19.10 and the same ntfs partition with Windows 10. I couldn't solve the issue. What I did was wait until Ubuntu 20.04 was developed and installed it from scratch. But I don't want to do another fresh install, I suppose this can be solved...

---

