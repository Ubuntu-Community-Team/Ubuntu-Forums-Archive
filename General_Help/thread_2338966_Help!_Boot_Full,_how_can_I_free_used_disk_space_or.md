---
title: "Help! /Boot Full, how can I free used disk space or enlarge"
date: 2016-10-03
forum: General Help
---

### Post by Daniel_Clarke on 2016-10-03
Hey All,

I am a NOOB when it comes to Linux, please be patient with me. I am trying to learn Linux and I am running into an issue. My /boot is full....seems like a common issue however I cannot get any of the fixes to work for me. Can someone PLEASE help?!? I have done a little research and am tying this command to clear teh old kernals I am no longer using:

```
sudo dpkg --get-selections|grep 'linux-image*'|awk '{print $1}'|egrep -v "linux-image-$(uname -r)|linux-image-generic" |while read n;do apt-get -y remove $n;done
```

**I get this as a result:**

```
daniel@NASBLAMP:~$ sudo dpkg --get-selections|grep 'linux-image*'|awk '{print $1}'|egrep -v "linux-image-$(uname -r)|linux-image-generic" |while read n;do apt-get -y remove $n;done
[sudo] password for daniel: 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
daniel@NASBLAMP:~$

```
Again, I am new and at this point don't know what to do, any help would be GREATLY appreciated.

Thanks

---

### Post by oldfred on 2016-10-03
I often get that error, as I have synaptic open, then try to run a command at the terminal. Or if you have Software Center or any other update app that sets lock.

Do you have more than one update program/terminal open at same time.

Is this 14.04? As 16.04 only keeps two kernels by default.
And then you must have the full drive encryption that uses LVM. I consider LVM an advanced partitioning that newer users should wait to use until they better understand Linux. But if you need full drive encryption, then you do have to use LVM.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[URL="https://wiki.ubuntu.com/Lvm"]https://wiki.ubuntu.com/Lvm

[/URL]
 /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove 

[URL="https://wiki.ubuntu.com/Lvm"]
[/URL]

---

### Post by Daniel_Clarke on 2016-10-04
Thank you for your quick response, just a reminder I am new so I may have some redundant questions. I apologize in advance. Here is where I am currently. I ran the following:

```
dpkg --list | grep linux-image
```

This is what was returned:

daniel@NASBLAMP:~$ dpkg --list | grep linux-image
ii  linux-image-3.19.0-25-generic                 3.19.0-25.26~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-51-generic                 3.19.0-51.58~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-56-generic                 3.19.0-56.62~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-58-generic                 3.19.0-58.64~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-59-generic                 3.19.0-59.66~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-61-generic                 3.19.0-61.69~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-64-generic                 3.19.0-64.72~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic           3.19.0-25.26~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-51-generic           3.19.0-51.58~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-56-generic           3.19.0-56.62~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-58-generic           3.19.0-58.64~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-59-generic           3.19.0-59.66~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-61-generic           3.19.0-61.69~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-64-generic           3.19.0-64.72~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-65-generic           3.19.0-65.73~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-extra-3.19.0-69-generic           3.19.0-69.77~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic-lts-vivid                 3.19.0.69.51                            amd64        Generic Linux kernel image

Then I tried:

```
sudo apt-get -s autoremove
```

This is what returned:

daniel@NASBLAMP:~$ sudo apt-get -s autoremove
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
**The following packages have unmet dependencies:**
 linux-image-extra-3.19.0-69-generic : Depends: linux-image-3.19.0-69-generic but it is not installed
 linux-image-generic-lts-vivid : Depends: linux-image-3.19.0-69-generic but it is not installed
                                 Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.


I have **BOLDED** a concerning line I have seen while trying to troubleshoot this issue, can anyone help with this and how I may resolve it?

Thanks in advance

-daniel

---

### Post by Geoffrey_Arndt on 2016-10-04
If you're running low on disk space, these kernels are not the main culprits.   Even if you remove them, you may still run short in a few days or maybe weeks.

How is the space on your system now allocated?   A picture would be invaluable.  You can use gparted to get the layout - - then do a screen grab and attach the thumbnail.

---

### Post by ian-weisser on 2016-10-04
> **Daniel_Clarke said:**
> **The following packages have unmet dependencies:**
 linux-image-extra-3.19.0-69-generic : Depends: linux-image-3.19.0-69-generic but it is not installed
 linux-image-generic-lts-vivid : Depends: linux-image-3.19.0-69-generic but it is not installed

That warning is expected and normal if your /boot is full.
It used to be a common issue...in encrypted and LVM installs in 14.04 and earlier. It's fixed in 16.04 and later.

Had you run 'autoremove' last month, or the month before, it would have likely prevented the entire problem from occurring. 
It's too late to run 'autoremove' now. Your package manager is already broken, and autoremove cannot repair that breakage.

To be clear: If you choose to run encrypted or LVM, you should enable unattended-upgrades...after you fix the problem. Oldfred's excellent links will tell you how.

---

### Post by oldfred on 2016-10-04
What version of Ubuntu?
Kernel 3.19 was 15.04 or enablement stack in 14.04.3 both are obsolete.
You may need to upgrade.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

---

### Post by Daniel_Clarke on 2016-10-04
I am using 14.04 LTS. I am unable to get gpart installed due to the /boot directory being full, I cannot upgrade ubuntu either. However I did run:

```
df -h
```

and returned this:

daniel@NASBLAMP:~$ df -h
Filesystem                     Size  Used Avail Use% Mounted on
udev                           3.8G  4.0K  3.8G   1% /dev
tmpfs                          779M  428K  779M   1% /run
/dev/mapper/NASBLAMP--vg-root   75G  5.5G   66G   8% /
none                           4.0K     0  4.0K   0% /sys/fs/cgroup
none                           5.0M     0  5.0M   0% /run/lock
none                           3.9G   80K  3.9G   1% /run/shm
none                           100M   52K  100M   1% /run/user
/dev/sda1                      236M  228M     0 100% /boot

I really appreciate the help so far any additional help is greatly appreciated!

Thanks again everyone!

-daniel

---

### Post by oldfred on 2016-10-04
/boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a 

You normally should not use rm to delete anything that is in dpkg as then dpkg gets out of sync.
But you may have to use rm to remove one kernel (part of set of all version files), but then reinstall and purge entire set of files correctly.

---

### Post by Daniel_Clarke on 2016-10-05
Ok,

So I am starting to feel like I am in over my head here and I do NOT want to mess up this server because it is in production status. I am new to the company and not very savvy with Linux. With that said would anyone be willing to help work me through this?

Thanks

-daniel

---

### Post by ian-weisser on 2016-10-05
Oldfred told you exactly what to do. Twice.
Read those links.
Everything you need, step by step, is there.

Do you understand the problem?
Do you know how to use the 'dpkg' command?

---

### Post by Daniel_Clarke on 2016-10-05
I'll take another look at the links, again I am new to Linux, new to  this position and feeling overwhlemed and do NOT want to mess up this  server as NO ONE here has any documentation on it from the previous Sys  Admin.  At this point we don't even think it is being backed up properly  yet he had it in production....

I understand my boot partition is  full, do I understand the "dpkg" command? NO, I don't even know Linux  as I have stated several times throughout this thread. I have gotten to  this point by dumb luck and google. I will take a look at the links he  sent, it just seemed like a bunch of information that confused me more. Maybe a second time through will help.

Thanks

-daniel

---

### Post by ian-weisser on 2016-10-05
Which of those kernels are you currently running?
```
uname -a
```

---

### Post by Daniel_Clarke on 2016-10-06
Ian,

```
uname -a
```

returned:

daniel@NASBLAMP:~$ uname -a
Linux NASBLAMP 3.19.0-64-generic #72~14.04.1-Ubuntu SMP Fri Jun 24 17:59:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
daniel@NASBLAMP:~$

Thanks again for any and all help!

-daniel

---

### Post by ian-weisser on 2016-10-06
First, delete one or two old kernels to free up enough space for apt to work.
```
sudo dpkg --remove linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic linux-image-3.19.0-51-generic linux-image-extra-3.19.0-51-generic
```


Apt should work now.
Second, delete the remaining obsolete kernels, test the package manager for proper function, complete installation of the incompletely-installed kernels, and install the latest security updates.
```
sudo apt autoremove
sudo apt update
sudo apt upgrade
```


Most apt and dpkg errors should be gone now.
There may be a few left, since the system is running a (obsolete) 15.10 kernel. Replacing that is the next step.

---

### Post by Daniel_Clarke on 2016-10-06
Ian and OldFred,

Thank you for you assistance in getting this matter resolved, I truly appreciate it. Now to see if there is a way to increase the size of this boot partition so I can upgrade to 16.04. :)

---

### Post by Geoffrey_Arndt on 2016-10-06
Just as an aside "FYI" . . .  .probably best (to avoid consfusion) to use a different term for the partition . . "boot" partition refers to a system where the actual /boot "directory" is a separate partition (which is not a requirement, or recommended practice for consumer systems).   Just call it your Ubuntu 14.04.1 partition . . . and use "gparted" via a Live linux cd/dvd/flashstick to resize the partition.      There are some excellent videos on youtube about resizing partitions using gparted.    [  https://www.youtube.com/results?search_query=gparted+live+tutorial]("https://www.youtube.com/results?search_query=gparted+live+tutorial")

One other optional recommendation - - an excellent Linux "Rescue" system can be obtained from the Parted Magic website.   While Parted Magic uses all free (FOSS) apps, the developer has put together a decent system and collection of packages that runs entirely in ram (meaning it's convenient and fast).   For his work, the download is not free (about $9.00 for latest verison).   BTW, I'm not connected in any way to that project, but appreciate a good value.

---

### Post by oygle on 2016-10-16
I couldn't login in today. Some msg about /tmp

Finally logged in and ran ..

```

sudo apt-get -s autoremove
```

but / is still very full - 16.58 Gb size and 14.99 Gb used. How do I use gparted to increase the size of /boot please ?

Or, should I be looking at more methods to clean up ? All 'trash' folders are empty.

---

### Post by ian-weisser on 2016-10-16
Removing unused kernels in /boot is very different from cleaning up /...and both are very different from handling a full /tmp.
Which one are you asking for help with?

---

### Post by oygle on 2016-10-16
> **ian-weisser said:**
> Which one are you asking for help with?

I have done the autoremove, therefore cleaning up, and/or increasing the size of /boot.  That said, surely 16 Gb is ample. KMail and it's associated 'akonadi' server has been playing up a lot lately, so possibly files left over from that, that can be cleaned up ?

```

$ **df -h**
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           789M   18M  772M   3% /run
/dev/sda1        17G   15G  1.2G  93% /
tmpfs           3.9G  108K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda6       896G   53G  798G   7% /home
tmpfs           789M     0  789M   0% /run/user/118
tmpfs           789M   16K  789M   1% /run/user/1000
 
$ **uname -a**
Linux ******************* 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by deadflowr on 2016-10-17
Remove the -s option from autoremove to actually clean.
The -s means simulate.
So nothing was done.

You have no separate boot partition, so nothing to do to expand that.

---

### Post by oygle on 2016-10-17
> **deadflowr said:**
> Remove the -s option from autoremove to actually clean.
The -s means simulate.
So nothing was done.

Thanks that showed as about 2 Gb to be removed, and now ..

> $ **df -h**
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           789M   34M  756M   5% /run
/dev/sda1        17G   12G  3.6G  77% /
tmpfs           3.9G  108K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda6       896G   53G  798G   7% /home
tmpfs           789M     0  789M   0% /run/user/118
tmpfs           789M   16K  789M   1% /run/user/1000


so that's much better now.  :)

> **deadflowr said:**
> You have no separate boot partition, so nothing to do to expand that.

Do you mean, not seperate, as in another physical drive ? Certainly it is a seperate logical drive. (see attachment).

---

### Post by oygle on 2016-10-25
Installed **baobab** and now can see where the space is being used.  ( ref erence - [https://ubuntuforums.org/showthread.php?t=2340970](https://ubuntuforums.org/showthread.php?t=2340970) )

/var/log/ was nearly 8Gb. Looked in there ..

/var/log/kernel.log*   totals 3.1 Gb
/var/log/ufw.log*  totals 3.9 Gb

hmm, now I remember I turned on full logging for ufw. Will turn that off. 

What processes can be put in place to continue to clean up log files ??

---

