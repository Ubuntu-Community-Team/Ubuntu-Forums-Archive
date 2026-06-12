---
title: "Out of space error when i have 55GB available"
date: 2008-06-18
forum: General Help
---

### Post by Leion on 2008-06-18
My ubuntu complains out of space after the latest patch upgrade.
But according to this picture, I still have lots of space.
[IMG]http://img141.imageshack.us/img141/8252/screenshotdiskusageanalie4.png[/IMG]

sda1 is the windows partition while sda8 is a drive which I am using to share files between the 2 OS. I am not sure why these 2 are counted as part of the root. 

Anyone can help me on this?

I have space but the system just locks me to the 18GB...:confused:

---

### Post by avtolle on 2008-06-18
Your /root partition is showing at 100%. Yes, you have other space available, but it is not accessible to the / partition, the size of which you likely set at installation. Quick and dirty remedy is to delete files from the / partition to free up some space (for now). I'm not sure what all you have installed, etc., but you've filled it up for sure.

---

### Post by ibutho on 2008-06-18
Run Applications -> Accessories -> Terminal and enter the command 
```
df -h
```
That should give you a better idea about disk space usage.

---

### Post by Leion on 2008-06-18
```
leion@leionuntu:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             5.0G  4.7G   32M 100% /
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   72K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   38M  214M  15% /lib/modules/2.6.24-19-generic/volatile
/dev/sda5             101M   96M     0 100% /boot
/dev/sda1              16G  8.3G  7.7G  52% /media/sda1
/dev/sda7              53G  5.9G   47G  12% /media/sda8
leion@leionuntu:/$ 

```

:( 
Did not install many things. only download things into sda8...

---

### Post by avtolle on 2008-06-18
You also have a "full" boot partition. You may safely remove older kernels from it to free up some space.

---

### Post by Leion on 2008-06-18
> **avtolle said:**
> You also have a "full" boot partition. You may safely remove older kernels from it to free up some space.

I have removed all the older kernels. the issue is still present for the full root though :D

---

### Post by plucky on 2008-06-18
```
sudo apt-get clean
sudo apt-get autoclean
``` 

This will clear out your download archive cache of installed software.i.e the deb files that are saved when you install software.


Good Luck

---

### Post by Leion on 2008-06-20
> **plucky said:**
> ```
sudo apt-get clean
sudo apt-get autoclean
``` 

This will clear out your download archive cache of installed software.i.e the deb files that are saved when you install software.


Good Luck

Thanks for the commands. I managed to clear the cache of the installed software. However this does not solve the problem. 

The problem still lies with the fact that the root directory still counts my /media files into its final size of 18GB... I do not want this.. it should have a total of 73GB, not 18GB....

---

### Post by drs305 on 2008-06-20
> **Leion said:**
> sda1 is the windows partition while sda8 is a drive which I am using to share files between the 2 OS. I am not sure why these 2 are counted as part of the root.


Disk Usage Analyzer, in my opinion, is one of the most confusing gui apps in ubuntu. You are not the first to ask about something they have seen in DUA. Root always shows 100% full - that's just the way the app depicts it. Of course, your / IS almost completely full. 

In your case, the sda1 and sda8 are included by DUA because they are mounted on /media, which is a subfolder of /, even though physically they are not part of the root partition. I know, it doesn't make a lot of sense to normal users like us. It's best to use commands such as the one ibutho gave you to see how your disk space is being used.

> 
The problem still lies with the fact that the root directory still counts my /media files into its final size of 18GB... I do not want this.. it should have a total of 73GB, not 18GB....

In fact, looking at the results of the "df -h" command, your system has:
/dev/sda6   5G root partition, almost all of which is being used.
/dev/sda1  16G partition,  7G free
/dev/sda7  53G partition, 47G free

These add up, approximately, to your 73G's.

By the way, it appears your fstab mounts /dev/sda7 to a partition named /media/sda8  ;-)

Bottom line: in your first post, you discuss thet lack of space. What you don't have is space in your / (root) partition. It is almost full (4.7/5G). You still have lots of space on your sda7 partition, but root doesn't use this for system files. 

If you have deleted all you can from root, several of your options would be to move /home to another partition, resize your root partition (some risk), backup your data and reinstall with different partition sizes.

---

### Post by Leion on 2008-06-20
> **drs305 said:**
> Disk Usage Analyzer, in my opinion, is one of the most confusing gui apps in ubuntu. You are not the first to ask about something they have seen in DUA. Root always shows 100% full - that's just the way the app depicts it. Of course, your / IS almost completely full. 

In your case, the sda1 and sda8 are included by DUA because they are mounted on /media, which is a subfolder of /, even though physically they are not part of the root partition. I know, it doesn't make a lot of sense to normal users like us. It's best to use commands such as the one ibutho gave you to see how your disk space is being used.



In fact, looking at the results of the "df -h" command, your system has:
/dev/sda6   5G root partition, almost all of which is being used.
/dev/sda1  16G partition,  7G free
/dev/sda7  53G partition, 47G free

These add up, approximately, to your 73G's.

By the way, it appears your fstab mounts /dev/sda7 to a partition named /media/sda8  ;-)

Bottom line: in your first post, you discuss thet lack of space. What you don't have is space in your / (root) partition. It is almost full (4.7/5G). You still have lots of space on your sda7 partition, but root doesn't use this for system files. 

If you have deleted all you can from root, several of your options would be to move /home to another partition, resize your root partition (some risk), backup your data and reinstall with different partition sizes.

Thank you. 
I have changed my fstab as pointed out
```
leion@leionuntu:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             5.0G  4.3G  462M  91% /
varrun                252M  104K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   72K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   38M  214M  15% /lib/modules/2.6.24-19-generic/volatile
/dev/sda5             101M   25M   71M  26% /boot
/dev/sda1              16G  8.3G  7.7G  52% /media/sda1
/dev/sda7              53G  5.9G   47G  12% /media/sda7

```

Think i should move my home directory away from / . 
I need to find a guide for it.
:)

---

### Post by avtolle on 2008-06-20
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) is a very good guide.

---

### Post by drs305 on 2008-06-20
> **Leion said:**
> 
Think i should move my home directory away from / . 
I need to find a guide for it.
:)


Here is a good one:
[ Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

Don't forget to backup your important files before doing this. ;-)

---

