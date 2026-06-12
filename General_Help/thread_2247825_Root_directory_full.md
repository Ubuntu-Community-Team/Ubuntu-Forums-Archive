---
title: "Root directory full"
date: 2014-10-10
forum: General Help
---

### Post by huwwevans on 2014-10-10
Greetings all.  

I have the following setup: 

9.6GB SSD partition Ubuntu root directory
200GB+ HDD partition Ubuntu Home directory.  

I am running Ubuntu 14.04 Trusty Tahr

The problem I have is that my root directory is now completly full and I can't seem to delete anything.  

Please let me know if you know how to solve this.  

Thanks,
Huw

---

### Post by grahammechanical on 2014-10-10
At the Grub boot menu open the Advanced Options for Ubuntu sub-menu and select Recovery mode. At the recovery menu select Clean - try to make free space. See, if that creates enough free space to load to a desktop. In recovery mode Resume will load to a desktop using an open source video driver that Ubuntu uses as a fall back video driver. Do not be surprised if the graphics seem a little slow.

Recovery mode Clean runs two commands - apt-get clean and apt-get autoremove. This is what autoremove does

> [COLOR=#333333][FONT=Ubuntu]This command removes packages that were installed by other packages and are no longer needed.[/FONT][/COLOR]

And this is what clean does

> [COLOR=#333333][FONT=Ubuntu]The same as above, except it removes [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]**all**[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] packages from the package cache. This may not be desirable if you have a slow Internet connection, since it will cause you to redownload any packages you need to install a program.[/FONT][/COLOR]

The reference to "the same as above" is a reference to the autoclean command which does

> [COLOR=#333333][FONT=Ubuntu]This command removes .deb files for packages that are no longer installed on your system. Depending on your installation habits, removing these files from [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/var/cache/apt/archives[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] may regain a significant amount of diskspace.[/FONT][/COLOR]

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Just so you know what is going to happen.

Regards.

---

### Post by yancek on 2014-10-10
9.6GB isn't much for a full Ubuntu install.  You should be able to move a partition (your /home partition) by using GParted from the Ubuntu Live CD/flash but it poses some risk of data loss so you should have a backup.  It is explained in the GParted Manual at the link below under Advanced Partition Actions:

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

---

### Post by huwwevans on 2014-10-10
@Yancek the /home directory is already on a separate partition.  

@grahammechanical I have tried those commands and neither work as there is literally no space left on the drive.

---

### Post by Bashing-om on 2014-10-10
huwwevans;

Sometimes in a condition of no overhead to operate in 'dpkg' is able to function. We can try to apply 'dpkg' directly and see if it can remove the old kernels.
Post back - between code tags - the output of terminal command:
```

dpkg -l | grep linux-

```

And we can craft up the command to try and remove the old kernels.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by yancek on 2014-10-10
> Yancek the /home directory is already on a separate partition.  


I'm fully aware of that which is why I suggested the link above.  You can move/resize your /home partition and give yourself room to resize/expand the root partition.  That's explained in the Gparted manual at the link I referred you to.  I'm curious as to why you can't delete anything on the / partition.  You are doing this as root user, correct?  What directories are you trying to delete from?

---

### Post by huwwevans on 2014-10-12
@Bashing-om here is the result of entering the command you posted.  

```
me@hevans:~$ dpkg -l | grep linux-ii  linux-firmware                                        1.127.7                                             all          Firmware for Linux kernel drivers
iU  linux-generic                                         3.13.0.37.44                                        amd64        Complete Generic Linux kernel and headers
iU  linux-generic-lts-saucy                               3.13.0.37.44                                        amd64        Generic Linux kernel image and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-27                               3.13.0-27.50                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-27-generic                       3.13.0-27.50                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-30                               3.13.0-30.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic                       3.13.0-30.55                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-33                               3.13.0-33.58                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic                       3.13.0-33.58                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                               3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                       3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.37.44                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-saucy                       3.13.0.37.44                                        amd64        Generic Linux kernel headers
rc  linux-image-3.11.0-15-generic                         3.11.0-15.25~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-18-generic                         3.11.0-18.32~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-19-generic                         3.11.0-19.33~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-27-generic                         3.13.0-27.50                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-30-generic                         3.13.0-30.55                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-33-generic                         3.13.0-33.58                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-27-generic                   3.13.0-27.50                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                   3.13.0-30.55                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic                   3.13.0-33.58                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.37.44                                        amd64        Generic Linux kernel image
iU  linux-image-generic-lts-saucy                         3.13.0.37.44                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-37.64                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
me@hevans:~$ 



```

@yancek What your suggesting may work but the /home directory is on a different physical drive.  The rest of the SSD is taken up by a windows partition.  I need this for printing as I only have a cannon printer.  I also run games on it sometimes.

---

### Post by ibjsb4 on 2014-10-12
I think Bashing has hit on a (the) problem.  Too many kernels.

You can remove all old kernels with one command.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users)

---

### Post by huwwevans on 2014-10-12
> **ibjsb4 said:**
> I think Bashing has hit on a (the) problem.  Too many kernels.

You can remove all old kernels with one command.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users)
That did the trick.  I now have 3.4 GB free.

Thanks for your help everyone.  This is why I love Linux:  It doesn't go wrong often and when it does there are always people like you to help put it right.

---

### Post by huwwevans on 2014-10-12
I spoke to soon.  My Ubuntu partition is now completely broken.  I can't tell what the problem is.  I'm going to try booting from a stick to see how bad the damage is.

---

### Post by huwwevans on 2014-10-12
Update.  The computer no longer seems to recognise my home directory as being that.  the home directory is not mounted upon startup and basically I get no programs or sidebar or topbar on login.

---

### Post by ibjsb4 on 2014-10-12
I have to run to the store, so this is a suggestion if you do not get anywhere.  I'll check back later.

Will it boot to the login screen?  If so, go to console (Ctrl + Alt + F1) and login.  Then enter these commands:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
```
And post any errors.
If you cannot get to console, can you get to recovery mode at the grub login?  The same commands will work without sudo.

I would also remove the 'solved' tag so others will not pass over your thread.

---

### Post by ibjsb4 on 2014-10-12
Ok, got back.
> The computer no longer seems to recognize my home directory
Two different /hdd/ssd/partitions.  Something else is going on.
You still see the home partition?

---

### Post by huwwevans on 2014-10-13
After a lot of effort I have managed to decrypt and back up the home directory onto an external drive.  I think I might try a reinstall now.

---

### Post by Bashing-om on 2014-10-13
huwwevans; Weeelll,

(RE-)install is always an option, take what you have learned to this point and apply it to this next install ! - perhaps this time no encryption (as it adds a layer of complexity that is difficult to over come in times of difficulty).

What ever you decide, we are here to assist.

[INDENT][INDENT]ways and means to an end
[/INDENT][/INDENT]

---

### Post by huwwevans on 2014-10-13
Ok. I did a full reinstall, managed to find a 4 GB section of SSD I hadn't been using and added that to the root partition.  I then succeeded in keeping the old home directory during the install!  Upgraded everything. ran sudo apt-get clean and then installed all the extra libraries I use.  

Everything is working better than ever now.  (apart from virtual-box I couldn't be bothered to reinstall that)

Result: 4.6GB used out of 13.6GB.

---

### Post by Bashing-om on 2014-10-13
huwwevans; Great !

You do good work. Appreciate that you informed the forum and of your solution.

As this matter is now concluded:
Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Michael_McKenney on 2014-10-13
Did you remove too many 3.13 kernels?  I did that once.   I had to run a bunch of updates, upgrades and dist-upgrades to get it to fix itself.

---

### Post by huwwevans on 2014-10-18
No, I still had two kernels left.  I'm not sure what I did but it wasn't that.

---

