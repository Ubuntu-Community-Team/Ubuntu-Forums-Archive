---
title: "Umm, why is Ubuntu software updater telling me I have no room in my /boot folder..."
date: 2016-02-10
forum: General Help
---

### Post by GreysonB on 2016-02-10
...when there is over 900 GB available on my hard drive?

Seriously, why can't ubuntu see that for itself?

Why should I even have to ask this question?

Sorry if that sounded like Donald Trump..

---

### Post by howefield on 2016-02-10
Just what it says, your /boot partition which doesn't have access to your 900 GB of space is too full, first thing to try is running the command

```
sudo apt-get autoremove
```

This should remove packages which are no longer needed including older kernels (except for the current and previous one)

If that doesn't solve it, we can manually remove the older kernel packages.

---

### Post by GreysonB on 2016-02-10
Tried it.  This was the result.

---

### Post by GreysonB on 2016-02-10
Oh BTW - I also tried the sudo apt-get clean - that had no effect either...

---

### Post by vasa1 on 2016-02-10
Re.  "Umm, why is Ubuntu software updater telling me I have no room in my /boot folder... "
I don't know about the "Umm" part, but your /boot folder being full can happen regardless of how big your hard drive is.

Paste the output of **df -h** here using code tags.

Then, provide the output of **ls -l /boot** also using code tags.

PS: are you using encryption?

---

### Post by GreysonB on 2016-02-10
Encryption - yes. always.

```
thaumielx72@thaumielx72-MS-7593:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         5.9G  4.0K  5.9G   1% /dev
tmpfs                        1.2G  1.5M  1.2G   1% /run
/dev/mapper/ubuntu--vg-root  905G   62G  797G   8% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
none                         5.0M     0  5.0M   0% /run/lock
none                         5.9G   81M  5.8G   2% /run/shm
none                         100M   36K  100M   1% /run/user
/dev/sda1                    236M  161M   63M  72% /boot
/home/thaumielx72/.Private   905G   62G  797G   8% /home/thaumielx72
thaumielx72@thaumielx72-MS-7593
```

```
thaumielx72@thaumielx72-MS-7593:~$ ls -l /boot
total 155169
-rw-r--r-- 1 root root  1165260 Oct 23 10:39 abi-3.13.0-67-generic
-rw-r--r-- 1 root root  1165260 Nov  6 14:57 abi-3.13.0-68-generic
-rw-r--r-- 1 root root  1165334 Dec 17 19:42 abi-3.13.0-74-generic
-rw-r--r-- 1 root root  1165277 Jan 11 10:22 abi-3.13.0-75-generic
-rw-r--r-- 1 root root   165763 Oct 23 10:39 config-3.13.0-67-generic
-rw-r--r-- 1 root root   165763 Nov  6 14:57 config-3.13.0-68-generic
-rw-r--r-- 1 root root   165763 Dec 17 19:42 config-3.13.0-74-generic
-rw-r--r-- 1 root root   165918 Jan 11 10:22 config-3.13.0-75-generic
drwxr-xr-x 5 root root     1024 Jan 17 00:10 grub
-rw-r--r-- 1 root root 28870800 Nov  8 06:34 initrd.img-3.13.0-67-generic
-rw-r--r-- 1 root root 28874580 Nov 19 05:00 initrd.img-3.13.0-68-generic
-rw-r--r-- 1 root root 28875619 Dec 19 06:42 initrd.img-3.13.0-74-generic
-rw-r--r-- 1 root root 28879423 Jan 17 00:10 initrd.img-3.13.0-75-generic
drwx------ 2 root root    12288 Nov  8 04:33 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3392383 Oct 23 10:39 System.map-3.13.0-67-generic
-rw------- 1 root root  3392383 Nov  6 14:57 System.map-3.13.0-68-generic
-rw------- 1 root root  3392888 Dec 17 19:42 System.map-3.13.0-74-generic
-rw------- 1 root root  3393097 Jan 11 10:22 System.map-3.13.0-75-generic
-rw------- 1 root root  5822368 Oct 23 10:39 vmlinuz-3.13.0-67-generic
-rw------- 1 root root  5822400 Nov  6 14:57 vmlinuz-3.13.0-68-generic
-rw------- 1 root root  5825376 Dec 17 19:42 vmlinuz-3.13.0-74-generic
-rw------- 1 root root  5827136 Jan 11 10:22 vmlinuz-3.13.0-75-generic
thaumielx72@thaumielx72-MS-7593:~$ 

```

I hate looking stupid, but in in 34+ years of computing experience - I have never heard the phrase "code tags."

Thanks in advance.

---

### Post by dragonfly41 on 2016-02-10
> I have never heard the phrase "code tags."
At the very bottom of this page .. (forum FAQ) .. is a link .. "BB Code"
and see "code"

So for example I have just run the command .. uname -a .. which gives the latest version of kernel installed

and I post .. but bound by "code tags" 
```
Linux Inspiron-1720 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:59 UTC 2016 i686 i686 i686 GNU/Linux
```

...

re: tidying up .. I use Ubuntu Tweaks > Janitor > Old Kernel following tip found here ..

[http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot](http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot)

but I'm not sure how Ubuntu Tweaks copes with encryption.

---

### Post by slickymaster on 2016-02-10
> **GreysonB said:**
> <---snip--->

I hate looking stupid, but in in 34+ years of computing experience - I have never heard the phrase "code tags."

Thanks in advance.
[How to use [CODE] tags in your Posts]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168")

---

### Post by vasa1 on 2016-02-10
Re. encryption, it seems that /boot is particularly tiny: Take a look at ian-weisser's contribution here at [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

From there:> LVM installs and encrypted installs use a small separate /boot partition. The small partition is capable of holding only four or five kernels, and fills to capacity quickly. Regular maintenance is vital to prevent breaking your package manager. 

---

### Post by vasa1 on 2016-02-10
> **GreysonB said:**
> ...
I hate looking stupid, but in in 34+ years of computing experience - I have never heard the phrase "code tags."
...
Awesome!

---

### Post by grahammechanical on 2016-02-10
You tried autoremove and that did not work. I think it did but the Update manager is in a kind of loop. It is trying to install a new kernel but it cannot because /boot is full. You run autoremove and that most likely removed at least one kernel but then update manager tries to install the new kernel. And hits another problem.

My advice would be to try this before Ubuntu is loaded. At the Grub boot menu select Advanced options for Ubuntu and then select a recovery mode kernel. At the recovery menu select Clean - Try to make free space. That will run both apt-get clean & apt-get autoremove. You may need to run autoremove more that once to remove more than one kernel.

When back at the recovery menu select Resume to get to a desktop.

Regards.

---

### Post by coldraven on 2016-02-10
> grahammechanical: At the Grub boot menu select Advanced options for Ubuntu
You need to press the Shift key when booting. 
See here:
[http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time)

---

### Post by vasa1 on 2016-02-10
> **grahammechanical said:**
> You tried autoremove and that did not work. I think it did but the Update manager is in a kind of loop. ...
Won't *autoremove* inform the user about what it is planning to do? OP said only that it didn't work and didn't elaborate by posting the terminal output or by running *df -h* again :( :( :(

And in this context, isn't *apt-get clean* not relevant given that it only frees up space outside */boot* in */var/cache/apt/archives*?

---

### Post by ian-weisser on 2016-02-10
> **grahammechanical said:**
> You tried autoremove and that did not work. I think it did but the Update manager is in a kind of loop. It is trying to install a new kernel but it cannot because /boot is full. You run autoremove and that most likely removed at least one kernel but then update manager tries to install the new kernel. And hits another problem.

Perhaps one kernel was not removed by apt.

Apt, upon starting, looks at dpkg's tracking of the package system. While doing so, it discovers not-yet-completed package actions (like uninstalled updates) and queues those actions. Then it discovers and queues the autoremove command.

It's a fifo queue. The pending installs run before autoremove, and their failure ('no space left on device') aborts the entire queue. Autoremove never runs at all. The package actions are still not complete, and get picked up again the next time apt runs.

The simplest one-time way around apt's behavior is to carefully remove one old kernel using dpkg, freeing space for apt to work it's queue...including autoremove.
The simplest permanent way to prevent re-occurence is to enable autoremove in unattended-upgrades, so you don't run out of space.

---

### Post by GreysonB on 2016-02-11
Thank you to everyone who answered.

I learned a few new things and solved this mystifying problem by using synaptic to just remove the old linux images.

uh, sorry about the umm - that's just the way I think (talk, post).  Meant no offense.

(I always thought a little bit of personality would make the post more interesting -- more personal.)

---

