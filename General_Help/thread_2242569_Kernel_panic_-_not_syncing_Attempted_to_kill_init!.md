---
title: "Kernel panic - not syncing: Attempted to kill init!"
date: 2014-09-02
forum: General Help
---

### Post by Anil_Usumezbas on 2014-09-02
Greetings,

My workstation OS  has been Ubuntu 10.04 LTS for a while now. Yesterday I tried to install  Mumble using Ubuntu Software Center and the installation quit after  giving me some errors. When I restarted the system some time after that,  I started receiving kernel panic errors when trying to boot the OS. The exact error I receive is the following:


init[1]: segfault at 7f79766e8000 ip 00007f79766e8000 sp 00007fff9181eb68 error 15

Kernel panic - not syncing: Attempted to kill init!


When  I boot from LiveCD, I can access my data and everything seems in order.  I have tried some basic methods to regain access to my OS, such as the  following:


* fsck on my Ubuntu partition using LiveCD

* gparted on my Ubuntu partition using LiveCD

* choosing a recovery mode kernel during startup

* Ubuntu Boot-Repair tool

* reinstalling the kernel following the instructions here: [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)


None of the above methods worked for me. Disk/boot repair tools either do not find any problems, or cannot fix anything. Boot-Repair tool gives a mysterious-looking error and quits. For the kernel reinstallation, I get stuck right after chroot'ing into the partition because any command after that throws a "Segmentation fault (core dumped)". 

Before making the  decision to backup my data and do a fresh installation, I wanted to  consult some experts on whether the system could still be salvageable. 


 Can you provide assistance to me on this issue?

Thank you very much in advance for your time.
Best regards,
Anil Usumezbas

---

### Post by Bashing-om on 2014-09-02
Anil_Usumezbas; Hi Welcome to the forum .

This may prove to have great difficulties.
Be aware that though release 10.04 for the server edition continues to have support, the support for the desktop edition 'had' ended.
I have seen some hints where the 'desktop' sources may have been turned back on, I do not know that for sure.
 At some later time, when booting is re-established - Would be a good idea to disable all 3rd party sources for the time being and see the results.

As you have been using this system for some time now, let's make sure you have been doing the maintenance on it, and still have operational head room ( kernel panic, and out of disk space ??).
What are you looking like ?
From the liveDVD:
```

sudo fdisk -lu

```
to KNOW what partition the OS is installed onto;  and IF there is a setatate '/boot' partition.
then we mount that partition(s):
If we have a separate /boot partition, will also have to mount it and have a looksee there for sure ! 
```

mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work 
df -h
df -i
sudo umount /mnt/work

```
adjust 'sda1' to what is actual in your case for the root file system.
Once we know space is not a factor, we can then look at the boot process and see what the system is trying to boot up, and where the failure might lie.
From / and /boot we can see about following the path to boot which kernel.

[INDENT][INDENT]there is that process
[INDENT][INDENT][INDENT][INDENT]and we can look
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Anil_Usumezbas on 2014-09-02
Hello,

Thank you very much for your reply. I think my OS is in my /dev/sda1 partition and there's no separate boot partition.

When I call [FONT=monospace][/FONT]sudo fdisk -lu, I see the following result:

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c9d2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   479768575   239883264   83  Linux
/dev/sda2       479770622   500117503    10173441    5  Extended
/dev/sda5       479770624   500117503    10173440   82  Linux swap / Solaris

Then I followed your instructions to mount /dev/sda1. When I call df -h on this partition, I see the following:

Filesystem            Size  Used Avail Use% Mounted on
aufs                   12G  127M   12G   2% /
none                   12G  268K   12G   1% /dev
/dev/sr0              696M  696M     0 100% /cdrom
/dev/loop0            665M  665M     0 100% /rofs
none                   12G  276K   12G   1% /dev/shm
tmpfs                  12G  396K   12G   1% /tmp
none                   12G   92K   12G   1% /var/run
none                   12G  4.0K   12G   1% /var/lock
none                   12G     0   12G   0% /lib/init/rw
/dev/sda1             226G  178G   37G  84% /media/05c2669e-0bd2-4d49-8482-c3949374c303
/dev/sda1             226G  178G   37G  84% /mnt/work

And similarly, df -i gives me the following:

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
aufs                 3092803    1544 3091259    1% /
none                 3091485     743 3090742    1% /dev
/dev/sr0                   0       0       0    -  /cdrom
/dev/loop0            140041  140041       0  100% /rofs
none                 3092803       6 3092797    1% /dev/shm
tmpfs                3092803      60 3092743    1% /tmp
none                 3092803      49 3092754    1% /var/run
none                 3092803       2 3092801    1% /var/lock
none                 3092803       1 3092802    1% /lib/init/rw
/dev/sda1            14999552 1613802 13385750   11% /media/05c2669e-0bd2-4d49-8482-c3949374c303
/dev/sda1            14999552 1613802 13385750   11% /mnt/work

Does this look like a space issue? I am having trouble deciphering the meaning behind all these :)

Thanks again for your help.
Anil

---

### Post by Bashing-om on 2014-09-02
Anil; Hey;

No, close but not immediately distressing ( 84% ) but high enough to look twice:
```

sudo du -h --max-depth=1 /mnt/work
sudo du -h --max-depth=1 mnt/work/boot

```

Then we look at what is being booted.

[INDENT][INDENT][INDENT]just a look-a-bout
[/INDENT][/INDENT][/INDENT]

---

### Post by Anil_Usumezbas on 2014-09-03
Hello,

The output for sudo du -h --max-depth=1 /mnt/work:

8.0K    /mnt/work/media
32M    /mnt/work/lost+found
1.8G    /mnt/work/lib
445M    /mnt/work/opt
210M    /mnt/work/boot
4.0K    /mnt/work/mnt
2.6M    /mnt/work/tmp
8.5M    /mnt/work/sbin
13M    /mnt/work/lib32
22G    /mnt/work/usr
4.0K    /mnt/work/sys
4.0K    /mnt/work/proc
7.8M    /mnt/work/bin
17M    /mnt/work/etc
4.0K    /mnt/work/run
4.0K    /mnt/work/selinux
200K    /mnt/work/srv
20K    /mnt/work/dev
40K    /mnt/work/vision
555M    /mnt/work/var
3.8G    /mnt/work/root
4.0K    /mnt/work/cdrom
150G    /mnt/work/home
178G    /mnt/work

The output for sudo du -h --max-depth=1 /mnt/work/boot:

4.3M    /mnt/work/boot/grub
210M    /mnt/work/boot

Is this informative?

Thanks again for your help.
Anil

---

### Post by Bashing-om on 2014-09-03
Anil_Usumezbas; Well,

I see no obvious difficulties with the space utilization ( beside /lib and /root unexpectedly large).
Let's see how the system is booting, and then see if we can boot it manually.
Does not appear that space constraints are the source of the problem.

Now this is a for real server install, correct, and not a desktop used as a server ? As I have advised, the desktop edition is End_Of_Life.

Post back the outputs - between code tags - of the terminal commands:
From the liveDVD:
```

ls -la /mnt/work/
ls -la /mnt/work/boot

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we try and boot this sucker manually, see what happens.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by Anil_Usumezbas on 2014-09-03
Hello,

I will try the commands you've suggested and post the output here. But first, I wanted to make sure: I was using a desktop Ubuntu 10.04, not server. I know it was end of life, but I did not have time to update it. Do you think it would make sense to not try and fix this at all and reinstall a 12.04 or 14.04 instead?

Thank you

---

### Post by Bashing-om on 2014-09-03
Anil_Usumezbas; Well, Like this

Release 10.04 is history in just a few more months ir-regardless. Makes a lot of sense to release upgrade now.
But that is your call, we are here to assist in what you want to do.
Fixing this 10.04, however, might prove a learning experience for all. BUt, IF we have but limited access to the software repository, may prove a real challenge !

[INDENT][INDENT]we won't know for sure
[INDENT][INDENT][INDENT][INDENT]'til we try
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Anil_Usumezbas on 2014-09-04
Hello,

Yes this is the reason I was asking. Because I actually encountered similar problems to this in the past, but  simple tricks like the ones I tried fixed it in all cases until now. I'm guessing having limited access to software repository makes it much harder for me to deal with the problem, so I'm going to go ahead and install 12.04 LTS and be done with it :)

Thank you for the assistance you've provided so far. I would've tried to fix it just to see what happens, but I'm kind of under a time constraint, so I'm trying to move forward fast :)

Best,
Anil

---

### Post by Bashing-om on 2014-09-04
Anil; Yeah !

I fully agree that a clean install of a current release is in the long run the better option. With that 'long run' in mind how about release 14.04, as it is supported 'til 2019 ? As well, 14.04 has many enhancements over 12.04.
ubuntu has unity as the desk top environment
whereas lubuntu has the environment you are the more accustomed to.
There be many other options, the big thing is deciding on which of these many choices you want to go with !


We will keep this thread as open untill you are up and operational on a newer release.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

