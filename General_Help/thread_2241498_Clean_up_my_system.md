---
title: "Clean up my system"
date: 2014-08-26
forum: General Help
---

### Post by alfirdaous on 2014-08-26
Hello everybody,  My system shows that there is no free space left, is there any method to clean up the system?    ```
 Filesystem      Size  Used Avail Use% Mounted on /dev/sda6        28G   26G     0 100% / udev            1.5G  4.0K  1.5G   1% /dev tmpfs           303M  920K  303M   1% /run none            5.0M     0  5.0M   0% /run/lock none            1.5G  428K  1.5G   1% /run/shm none            100M   52K  100M   1% /run/user 
```  How can I know where are located big files?  Thanks in advance

---

### Post by pfeiffep on 2014-08-26
I use bleachbit (available in software center) to keep my system humming.

---

### Post by whitesmith on 2014-08-26
In order to find the 25 largest files in your home directory open a terminal and enter:```
du -ah ~ | sort -nr | head -n 25
```If you want to start at the filesystem root, which your post suggests would be appropriate, change the tilde to a slash. Regards.

---

### Post by Bashing-om on 2014-08-26
alfirdaous; Hi !

Generally 2 things will cause that situation:
a) /boot partition full
IF You are running release 14.04, these commands might work to relieve /boot, IF 'apt' has the head room to operate in:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```
Else in 12.04 will have to manually intervene to remove old kernels.

b)
> 
How can I know where are located big files? Thanks in advance

To look about, my favorite way:
```

cd /
sudo du -sx * | sort -n

```
If you need to drill down or around further, use 'cd' to move to a directory of interest then repeat the 'du' command.
The results are in megabytes.
Often time are also found that the log files are run-a-muck reporting a system error,
Then again too much crammed into the /home directory; downloads, videos, pictures and so on.

[INDENT][INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT][/INDENT]

---

### Post by alfirdaous on 2014-08-27
How can I delete old kernels?

---

### Post by Ksiencha on 2014-08-27
> How can I delete old kernels?

See [**this answer**](http://askubuntu.com/a/100953/277426).

---

### Post by slickymaster on 2014-08-27
> **alfirdaous said:**
> How can I delete old kernels?

[How do I remove or hide old kernel versions to clean up the boot menu?]("http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu")
[Automating removal of old kernels from servers]("http://ubuntuforums.org/showthread.php?t=1961409")

---

### Post by Ksiencha on 2014-08-27
Also you can use Janitor in Ubuntu Tweak tool to clean up your system. You can find Ubuntu Tweak in Software Center or [**download here**](http://ubuntu-tweak.com/).

---

### Post by Impavidus on 2014-08-27
See this tutorial on what to do when your disk is full: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by alfirdaous on 2014-08-27
I rebooted my computer, and then I have some options to boot from:

```

Ubuntu
Advanced options for ubuntu
Memtest
Windows Vista

```

So I choosed "Advanced options for ubuntu" and then I have a list of options, some of them have a name recovery mode at the end, so which one can I delete? and how many can I keep? (I saw in previous posts that I should keep at least 2 or 3 kernels)

Shall I start from the end or from the beginning, because numbers are different (if I say versions)

---

### Post by grahammechanical on 2014-08-27
My advice would be to go into Advanced options, as you have done and select the first version of Linux in the list that says Recovery Mode. Then, at the Recovery menu select Clean - Try to make free space. Then when back at the Recovery menu select Resume. Then, when you are back at the desktop shutdown and reboot. Then enter Advanced options again and see if the list is smaller.

If the list is the same length make a written copy of the list. You will notice that the Linux kernels are in numerical order. For example, on my machine I have kernels 3.16.0-3; 3.16.0-4; 3.16.0-5; 3.16.0-6. They are in numerical order in the list. The two newest kernels on my machine are 3.16.0-6 and 3.16.0-5. Therefore, if I wanted to I could remove kernels 3.16.0-3 and 3.16.0-4.

You will have different kernels on your machine because you are not running the same version of Ubuntu as I am.

Regards.

---

### Post by alfirdaous on 2014-08-27
It is not deleted, is there a command line to delete a specific kernel?

---

### Post by slickymaster on 2014-08-27
> **alfirdaous said:**
> It is not deleted, is there a command line to delete a specific kernel?

Did you saw the second link provided in [post #7]("http://ubuntuforums.org/showthread.php?t=2241498&p=13109146&viewfull=1#post13109146")?

---

### Post by uRock on 2014-08-27
Hopefully this is to make room for upgrading to 14.04 from 12.10, though I am not sure you can upgrade directly to 14.04 from 12.10? [http://ubuntuforums.org/showthread.php?t=2241634](http://ubuntuforums.org/showthread.php?t=2241634)

---

### Post by alfirdaous on 2014-08-27
> **slickymaster said:**
> Did you saw the second link provided in [post #7]("http://ubuntuforums.org/showthread.php?t=2241498&p=13109146&viewfull=1#post13109146")?
Yes, I've seen it, this will delete all old kernels, I am looking to delete a specific kernel

> **uRock said:**
> Hopefully this is to make room for upgrading to 14.04 from 12.10, though I am not sure you can upgrade directly to 14.04 from 12.10? [http://ubuntuforums.org/showthread.php?t=2241634](http://ubuntuforums.org/showthread.php?t=2241634)
I don't have much free space to upgrade

---

### Post by Bashing-om on 2014-08-27
alfirdaous; Hey ;


Small things can have great impact.
> 
 I am looking to delete a specific kernel

Post back the output of terminal command:
```

dpkg -l | grep linux-

```
and indicate which kernel(s) to remove, we can and will provide the specific command.

As an aid to guide you in insuring you are not doing something harmful :
```

ls -al /
ls -al /boot
uname -r
lsb_release -a

``` and perhaps shed some light on the way forward.

[INDENT][INDENT]we do what we can
[INDENT][INDENT][INDENT]the impossible, takes a bit longer
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by alfirdaous on 2014-08-27
Here you are:

```

$ dpkg -l | grep linux-
ii  linux-firmware                            1.95.1                                    all          Firmware for Linux kernel drivers
ii  linux-generic                             3.5.0.51.67                               i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.5.0-43                    3.5.0-43.66                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-43-generic            3.5.0-43.66                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-44                    3.5.0-44.67                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-44-generic            3.5.0-44.67                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-45                    3.5.0-45.68                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-45-generic            3.5.0-45.68                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-46                    3.5.0-46.70                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46-generic            3.5.0-46.70                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-47                    3.5.0-47.71                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-47-generic            3.5.0-47.71                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-48                    3.5.0-48.72                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-48-generic            3.5.0-48.72                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-49                    3.5.0-49.74                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-49-generic            3.5.0-49.74                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-51                    3.5.0-51.76                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51-generic            3.5.0-51.76                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.5.0.51.67                               i386         Generic Linux kernel headers
ii  linux-headers-generic-pae                 3.5.0.51.67                               i386         Transitional package
ii  linux-image-3.5.0-17-generic              3.5.0-17.28                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-43-generic              3.5.0-43.66                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-44-generic              3.5.0-44.67                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-45-generic              3.5.0-45.68                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-46-generic              3.5.0-46.70                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-47-generic              3.5.0-47.71                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-48-generic              3.5.0-48.72                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-49-generic              3.5.0-49.74                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-51-generic              3.5.0-51.76                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-17-generic        3.5.0-17.28                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-43-generic        3.5.0-43.66                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-44-generic        3.5.0-44.67                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-45-generic        3.5.0-45.68                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-46-generic        3.5.0-46.70                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-47-generic        3.5.0-47.71                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-48-generic        3.5.0-48.72                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-49-generic        3.5.0-49.74                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-51-generic        3.5.0-51.76                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic                       3.5.0.51.67                               i386         Generic Linux kernel image
ii  linux-libc-dev:i386                       3.5.0-51.76                               i386         Linux Kernel Headers for development
ii  linux-sound-base                          1.0.25+dfsg-0ubuntu3.1                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                           2:4.05+dfsg-6                             all          collection of boot loaders (common files)
ii  syslinux-legacy                           2:3.63+dfsg-2ubuntu5                      i386         Bootloader for Linux/i386 using MS-DOS floppies
alfirdaous@alfirdaous:~$ 


```

---

### Post by slickymaster on 2014-08-28
> **alfirdaous said:**
> Yes, I've seen it, this will delete all old kernels, I am looking to delete a specific kernel<---snip--->

Sorry, my bad. I meant to say my first link, not the second one. Anyway, in that link you'll find a solution to delete a specific kernel, which is in fact similar to [COLOR=#000000]Bashing-om's suggestion.

Basically, you run [/COLOR][COLOR=#000000]command below to view/list all installed kernels on your system```
dpkg --list | grep linux-image 
```Then just run the command below to remove the kernel you want:```
sudo apt-get purge linux-image-x.x.x.x-generic 
```Reboot your system.[/COLOR]

---

### Post by alfirdaous on 2014-08-28
I delete some them, and I won a 900 MB of free space

---

