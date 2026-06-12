---
title: "Purged Kernel"
date: 2014-09-02
forum: General Help
---

### Post by bjamin82 on 2014-09-02
Hi... To make a long story short, I accidently deleted the current kernel while I was purging the old kernels as /boot was out of space. After that mistake I could only boot into Memtest. I was able to get the latest kernel reinstalled by using the live cd and updating the gub config. However, it appears all the drivers will not load, as the video is jerky and slow... and none of the external usb devices seem to work, including my keyboard and mouse. 

This is a Dell Latitude E4310 running 14.04 kernel 3.13.0-34-generic


Thanks

---

### Post by Bashing-om on 2014-09-02
bjamin82; Hello;

At this point I would want to verify what kernels are installed and how the system is set to boot what kernel.
```

dpkg -l | grep linux-
la -al /
ls -al /boot
ls -al /usr/src
ls -al /lib/modules

```
Are all 4 symlinks proper, to point to existing images and initrd.img  ?

And check in '/etc/default/grub' the entry that is to be booted:
```

cat /etc/default/grub

```

Depending on those outputs, I might consider (re-)installing grub, or even (re-)building the 'initramfs' image.

It is a process from point a (bios) to point f ( the GUI). Some things we can control, some things the kernel controls.

[INDENT][INDENT]we can look, and we can find out
[/INDENT][/INDENT]

---

### Post by bjamin82 on 2014-09-02
There are a bunch of kernels available... Currently booting [COLOR=#000000]3.13.0-34-generic.. everything else looks fine.[/COLOR]

---

### Post by Bashing-om on 2014-09-02
bjamin82; Then;

Maybe it is time to rebuild the image.
> 
and none of the external usb devices seem to work, including my keyboard and mouse. 

how are you presently able to access the system to gain a terminal ?

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by bjamin82 on 2014-09-02
Yes I am able to boot into the system, logs into the desktop... since its a laptop the keyboard/mouse that is builtin works fine... just seems like devices are broken... video drivers dont' work, video is slow and jerky... usb keyboard and mouse do not work. USB disk drives are not recognized. Whats interesting is dmesg shows that the USB devices connect fine... they just don't work.

---

### Post by bjamin82 on 2014-09-02
How do I rebuild the image?

---

### Post by Bashing-om on 2014-09-02
bjamin82; Well,

As you are sure the kernel is installed, and the symlinks are proper, see what results:
```

sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
sudo update-initramfs -u

```

Reboot to see the effect.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bjamin82 on 2014-09-02
Booted fine... no problems solved...

---

### Post by Bashing-om on 2014-09-02
bjamin82; Beats me.

That was my only thought to address these may divergent issues.
I have no other suggestion.

[INDENT][INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by bjamin82 on 2014-09-02
maybe i picked an incompatiable kernel? whats the best way to download and use the latest stable version?

---

### Post by ian-weisser on 2014-09-02
> **bjamin82 said:**
> Hi... To make a long story short, I accidently deleted the current kernel while I was purging the old kernels as /boot was out of space.

> **bjamin82 said:**
> There are a bunch of kernels available... Currently booting [COLOR=#000000]3.13.0-34-generic.. everything else looks fine.[/COLOR]


So...how many kernels do you still have installed? Was your purging unsuccessful?

3.13.0-35-generic was pushed a couple days ago, did your system pick it up?

Is apt-get working for normal updates/upgrades/installs?

---

### Post by bjamin82 on 2014-09-02
still on 34-generic

updates and upgrades seem to be working... video card isn't, usb devices are not as well as my wifi...

---

### Post by Bashing-om on 2014-09-02
bjamin82; Welp;

1 way:
You can update to the latest kernel via apt-get as follows
```

sudo apt-get update
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install linux-image-`uname -r`
sudo apt-get upgrade

```
Note those ` are back ticks, not quote marks.
Current:
```

sysop@1404mini:~$ uname -r
3.13.0-35-generic
sysop@1404mini:~$

```

[INDENT][INDENT][INDENT]there is some hope
[/INDENT][/INDENT][/INDENT]

---

### Post by bjamin82 on 2014-09-02
weird it let me install to .35-generic both image and headers... upgrade does nothing... did an update-grub it found 35 but after reboot it doesn't boot into 35

---

### Post by Bashing-om on 2014-09-02
bjamin82; Well,

We are back to the symlinks in / for the vmlinuz and initrd.img pointing to where in /boot ?
post back -Between code tags -the outputs of terminal commands:
```

ls -al /
ls -al /boot

```
and let's see what those symlinks are.

[INDENT][INDENT][INDENT]gotta be a reason.
[/INDENT][/INDENT][/INDENT]

---

### Post by bjamin82 on 2014-09-02
$ ls -al /
total 110
drwxr-xr-x  25 root root  4096 Sep  2 23:24 .
drwxr-xr-x  25 root root  4096 Sep  2 23:24 ..
drwxr-xr-x   2 root root  4096 Sep  2 23:11 bin
drwxr-xr-x   4 root root  2048 Sep  2 23:41 boot
drwxr-xr-x   2 root root  4096 Dec  8  2013 cdrom
drwx------   3 root root  4096 Apr  7 15:12 .config
drwxr-xr-x  15 root root  4080 Sep  2 23:48 dev
drwxr-xr-x 151 root root 12288 Sep  2 23:49 etc
drwxr-xr-x   3 root root  4096 Dec  8  2013 home
lrwxrwxrwx   1 root root    33 Sep  2 23:24 initrd.img -> boot/initrd.img-3.13.0-35-generic
lrwxrwxrwx   1 root root    33 Aug 24 10:36 initrd.img.old -> boot/initrd.img-3.13.0-34-generic
drwxr-xr-x  25 root root  4096 Sep  2 13:38 lib
drwxr-xr-x   2 root root  4096 Sep  2 13:38 lib64
drwx------   2 root root 16384 Dec  8  2013 lost+found
drwxr-xr-x   3 root root  4096 Dec  9  2013 media
drwxr-xr-x   2 root root  4096 Apr 19  2013 mnt
drwxr-xr-x   8 ben  ben   4096 May 16 09:04 mount
drwxr-xr-x   5 root root  4096 May 16 12:31 opt
dr-xr-xr-x 243 root root     0 Sep  2 23:48 proc
drwx------   7 root root  4096 May 20 12:41 root
drwxr-xr-x  25 root root   880 Sep  2 23:49 run
drwxr-xr-x   2 root root 12288 Sep  2 23:09 sbin
drwxr-xr-x   2 root root  4096 Apr 24  2013 srv
dr-xr-xr-x  13 root root     0 Sep  2 23:48 sys
drwxrwxrwt   6 root root  4096 Sep  2 23:50 tmp
drwxr-xr-x  10 root root  4096 Apr 24  2013 usr
drwxr-xr-x  13 root root  4096 Dec  8  2013 var
lrwxrwxrwx   1 root root    30 Sep  2 23:24 vmlinuz -> boot/vmlinuz-3.13.0-35-generic
lrwxrwxrwx   1 root root    30 Aug 24 10:36 vmlinuz.old -> boot/vmlinuz-3.13.0-34-generic


ls -al /boot
total 17371
drwxr-xr-x  4 root root    2048 Sep  2 23:41 .
drwxr-xr-x 25 root root    4096 Sep  2 23:24 ..
-rw-r--r--  1 root root 1163858 Aug 14 22:56 abi-3.13.0-35-generic
-rw-r--r--  1 root root  165652 Aug 14 22:56 config-3.13.0-35-generic
drwxr-xr-x  5 root root    1024 Sep  2 23:41 grub
-rw-r--r--  1 root root 6631848 Sep  2 23:40 initrd.img-3.13.0-35-generic
drwxr-xr-x  2 root root   12288 Dec  8  2013 lost+found
-rw-r--r--  1 root root  176500 Mar 12 08:31 memtest86+.bin
-rw-r--r--  1 root root  178176 Mar 12 08:31 memtest86+.elf
-rw-r--r--  1 root root  178680 Mar 12 08:31 memtest86+_multiboot.bin
-rw-------  1 root root 3386444 Aug 14 22:56 System.map-3.13.0-35-generic
-rw-------  1 root root 5806368 Aug 14 22:56 vmlinuz-3.13.0-35-generic

---

### Post by Bashing-om on 2014-09-03
bjamin82; Sheesshhh,

There are no image, initrd.img files in /boot for "3.13.0-34-generic" that can not be a good thing.

Ian, oh wise and benevolent one, what thinkist thou ? 
(Re-)install the -34 header and image ?? See if the symlink gets re-established ?

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by bjamin82 on 2014-09-03
I reinstalled -34 and even using grub customizer, forcing to boot to 35, uname -r still resolves -34.

---

### Post by ian-weisser on 2014-09-03
Well, since it looks like /boot can only boot to -35, you can go in a couple directions.

We can wonder why uname -r resolves to -34. (How did grub offer any other kernel choices?)
We can tackle your wi-fi.
We can tackle your USB.

Which direction do you wish to go first?

---

### Post by bjamin82 on 2014-09-03
Thanks @Ian-weisser ... Well I would like my USB devices to work along with the video card to be properly used so its not jerky...

---

### Post by Bashing-om on 2014-09-05
bjamin82; Hey;

It is not by intent that I leave you high and dry. I just do not have the experience to know how the hardware interface works in this instance.

I am willing to learn, and we can try and blunder through this; seeing what the system reports -> lsusb, before and after plugging in a USB device, and as well reading the logs. Presently I do not even know what modules should be loaded to detect the USB devices ..

[INDENT][INDENT]I can find out
[INDENT][INDENT][INDENT][INDENT]we can learn
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

