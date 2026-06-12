---
title: "Cannot remove or install applications"
date: 2015-03-23
forum: General Help
---

### Post by Dragonbite on 2015-03-23
I am running into an issue with my 64bit Ubuntu 12.04.? installation.

When I start up the software center, I get the message > Items cannot be installed or removed until the package catalog is repaired.and it offers to repair it (which obviously fails). 

It runs through and ends with Package operation failed with the Details:```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 908262 files and directories currently installed.)
Unpacking linux-image-3.2.0-79-generic (from .../linux-image-3.2.0-79-generic_3.2.0-79.115_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-79-generic_3.2.0-79.115_amd64.deb (--unpack):
 unable to create `/lib/modules/3.2.0-79-generic/kernel/drivers/media/dvb/pt1/earth-pt1.ko.dpkg-new' (while processing `./lib/modules/3.2.0-79-generic/kernel/drivers/media/dvb/pt1/earth-pt1.ko'): No space left on device
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-76-generic...
P: Writing config for /boot/vmlinuz-3.2.0-75-generic...
P: Writing config for /boot/vmlinuz-3.2.0-74-generic...
P: Writing config for /boot/vmlinuz-3.2.0-72-generic...
P: Writing config for /boot/vmlinuz-3.2.0-70-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
Unpacking linux-headers-3.2.0-79 (from .../linux-headers-3.2.0-79_3.2.0-79.115_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-79_3.2.0-79.115_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-79/arch/x86/include/asm/xen/page.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-79/arch/x86/include/asm/xen/page.h'): No space left on device
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-79-generic (from .../linux-headers-3.2.0-79-generic_3.2.0-79.115_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-79-generic_3.2.0-79.115_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-79-generic/include/config/net/sched.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-79-generic/include/config/net/sched.h'): No space left on device
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-79-generic_3.2.0-79.115_amd64.deb
 /var/cache/apt/archives/linux-headers-3.2.0-79_3.2.0-79.115_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-79-generic_3.2.0-79.115_amd64.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  Package linux-image-3.2.0-77-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.75.89); however:
  Version of linux-image-generic on system is 3.2.0.77.91.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-75-generic; however:
  Package linux-headers-3.2.0-75-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured

```

I have tried **apt-get -f install**, which I got from [Ask Ubuntu]("http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full"),  which also fails  ```
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic linux-headers-3.2.0-79 linux-headers-3.2.0-79-generic linux-headers-generic
  linux-image-3.2.0-79-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-79 linux-headers-3.2.0-79-generic linux-image-3.2.0-79-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 3 newly installed, 0 to remove and 144 not upgraded.
3 not fully installed or removed.
Need to get 0 B/51.4 MB of archives.
After this operation, 218 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 908262 files and directories currently installed.)
Unpacking linux-image-3.2.0-79-generic (from .../linux-image-3.2.0-79-generic_3.2.0-79.115_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-79-generic_3.2.0-79.115_amd64.deb (--unpack):
 unable to create `/lib/modules/3.2.0-79-generic/kernel/drivers/media/video/ks0127.ko.dpkg-new' (while processing `./lib/modules/3.2.0-79-generic/kernel/drivers/media/video/ks0127.ko'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-76-generic...
P: Writing config for /boot/vmlinuz-3.2.0-75-generic...
P: Writing config for /boot/vmlinuz-3.2.0-74-generic...
P: Writing config for /boot/vmlinuz-3.2.0-72-generic...
P: Writing config for /boot/vmlinuz-3.2.0-70-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-79-generic /boot/vmlinuz-3.2.0-79-generic
Unpacking linux-headers-3.2.0-79 (from .../linux-headers-3.2.0-79_3.2.0-79.115_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-79_3.2.0-79.115_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-79/arch/x86/include/asm/xen/trace_types.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-79/arch/x86/include/asm/xen/trace_types.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-79-generic (from .../linux-headers-3.2.0-79-generic_3.2.0-79.115_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-79-generic_3.2.0-79.115_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-79-generic/include/config/net/sb1000.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-79-generic/include/config/net/sb1000.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-79-generic_3.2.0-79.115_amd64.deb
 /var/cache/apt/archives/linux-headers-3.2.0-79_3.2.0-79.115_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-79-generic_3.2.0-79.115_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now I see it shows "No space left on device" but I cannot remove anything without risking breaking something or making matters worse.  Now it has been a while since I installed this and I may have installed it to boot from the MBR but I do not remember. ```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        15G   12G  2.0G  86% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           591M  1.1M  590M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G   47M  2.9G   2% /run/shm
/dev/sda3        58G   50G  4.5G  92% /home
/dev/sda4       142G   93G   42G  70% /home/SHARE

```

---

### Post by Dragonbite on 2015-03-23
Ok, looking through the information I see **/run** seems to be using 590MB out of 591!

Looking through /run the most suspicious section is ```
$ ls -lh /run/shm/
total 156K
-r-------- 1 lightdm lightdm 65M Mar 23 20:28 pulse-shm-1849304143
-r-------- 1 drew    drew    65M Mar 23 20:29 pulse-shm-2208994249
-r-------- 1 drew    drew    65M Mar 23 20:29 pulse-shm-2264630680
-r-------- 1 drew    drew    65M Mar 23 20:35 pulse-shm-3824202200
-r-------- 1 drew    drew    65M Mar 23 20:29 pulse-shm-4281674251
-r-------- 1 lightdm lightdm 65M Mar 23 20:28 pulse-shm-449593079

```This ends up being (65M * 6 = ) 390M!

Do I need all of these? Could I delete these? Would this even make a difference?

---

### Post by v3.xx on 2015-03-23
No space left on device.  Your /boot is full.
> dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-79-generic_3.2.0-79.115_amd64.deb (--unpack):..........: No space left on device
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
```
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by bardo2 on 2015-03-23
> **Dragonbite said:**
> Ok, looking through the information I see **/run** seems to be using 590MB out of 591!



No, In normal linux-installations, /run is a temporary (RAM-based) filesystem for kernel operations only. And it can grow as needed, if swap is configured properly.

I guess v3xx nailed it, but without explaining. His command (see --dry-run option) does nothing, so you can check its output before actually removing that option.
My guess would be, that there is some likelyhood of old unnecessary kernels/images being found that are waiting for removal.

From my own experience, 15 GB for sytem (/) CAN be sufficient, if the space gets continuous attention, someone caring for logfile sizes, cached content, trash and so on.
But if you "just use it" it is not enough.

---

### Post by sammiev on 2015-03-23
[Ubuntu Tweak]("http://ubuntu-tweak.com/") maybe your best friend here to do a little house cleaning if your not comfortable with the command line. Both do the job.

---

### Post by v3.xx on 2015-03-23
> **bardo2 said:**
> I guess v3xx nailed it, but without explaining.
I thought the link did a good job of explaining it.

---

### Post by Dragonbite on 2015-03-24
> **v3.xx said:**
> No space left on device.  Your /boot is full.

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
```
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Yup, I think I ran across this command (or some dpkg & awk command) and gave it a try before going to bed. It didn't work and I'll have to try again when I get home to get the actual fail message.  

It may have failed with a message similar to the **apt-get -f install**.

Ubuntu Tweaks may help, but unfortunately I cannot install or uninstall anything at this time.

---

### Post by sammiev on 2015-03-24
> **Dragonbite said:**
> Yup, I think I ran across this command (or some dpkg & awk command) and gave it a try before going to bed. It didn't work and I'll have to try again when I get home to get the actual fail message.  

It may have failed with a message similar to the **apt-get -f install**.

Ubuntu Tweaks may help, but unfortunately I cannot install or uninstall anything at this time.

I thought about that after I posted. :(

---

### Post by Dragonbite on 2015-03-24
> **v3.xx said:**
> I thought the link did a good job of explaining it.

I love this level of detail and explaining the parts that build it.

Now, come to think of it, I think the command I ran included the **--dry-run** which could (and I kinda hope it does) explain why nothing happened... ;)

I'm definitely stepping through it tonight and see if I can get anywhere with it.

---

### Post by bardo2 on 2015-03-24
Ok. let me think out loud:
apt-get requires more disk space than there is at present.
simple clean up doesnt seem to yield enough space.
radical cleanup (like deleting logfiles, apt-get clean/autoclean/autoremove) and such... *COULD* temporarily help, but certainly not stabilize the system forever.
I ran into similar situations twice a year on computers, where i reserved too little disk space for the OS.
The real fix - of course - is to provide disk space (by adding a disk, or by removing the empty space from another partition, or - if nothing else - to shrinken the swap area.
All of those can be done, have been done before, need special care, are non-standard operations, can - if not done right - break the system.
I am pretty comfortable with any of those, but - at home - i am aware of such things like 
- overall RAM
- disk partitionning scheme (MBR/GPT)
- other OS (eventually)
- boot loader (grub2 maybe?)
- time involved
- and so on...

That lets me hesitate as to guide someone, i dont know, into beginning something like that. But - if there were a skilled person around - i would certainly suggest one of those.
Got it?

---

### Post by Dragonbite on 2015-03-24
Hmm.. that didn't work either ```
$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)" | xargs sudo apt-get remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.75.89) but 3.2.0.77.91 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-75-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by ian-weisser on 2015-03-25
> **Dragonbite said:**
>  ```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
** /dev/sda2        15G   12G  2.0G  86% /**
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           591M  1.1M  590M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G   47M  2.9G   2% /run/shm
/dev/sda3        58G   50G  4.5G  92% /home
/dev/sda4       142G   93G   42G  70% /home/SHARE

```

What is taking 12G on your system partition?
That seems rather high, the core of the problem.

If you don't have a graphical disk analyzer tool installed, use 'du' to discover the big space hogs. Several easy ways to use it - search engine is your friend.

---

### Post by Dragonbite on 2015-03-25
> **ian-weisser said:**
> What is taking 12G on your system partition?
That seems rather high, the core of the problem.

If you don't have a graphical disk analyzer tool installed, use 'du' to discover the big space hogs. Several easy ways to use it - search engine is your friend.

If I remember right, Disk Analyzer shows /var/usr/ being the biggest culprit.  I'll run it tonight and see what comes up, and/or try the `du` command.  

I never heard of the `du` command before (but just tested it out on work's FreeBSD web server ;) ).  Looks like that may be handy to keep in my back pocking :)

---

### Post by v3.xx on 2015-03-25
Is /boot full of kernels or not?

---

### Post by Dragonbite on 2015-03-25
> **v3.xx said:**
> Is /boot full of kernels or not?

Yes, a whole bunch of them (~12+?). Basically I haven't cleaned out the kernels since I installed 12.04 back in 2013.

I moved a few of them out of the /boot directory (store them in a folder in my /home directory which is on a separate partition) to try and make space.

---

### Post by v3.xx on 2015-03-25
> I moved a few of them out of the /boot directory (store them in a folder in my /home directory which is on a separate partition) to try and make space.
That would free up /boot space, but I wonder if inodes are still full.
```
df -i
```

---

### Post by bardo2 on 2015-03-25
> **Dragonbite said:**
> If I remember right, Disk Analyzer shows /var/usr/ being the biggest culprit. 
highly unlikely.
probably some other directory.

Anyway: once you get apt to work again, you may use computer-janitor to clean up the rest of the system.

But... long-term, i seriously suggest enlarging the / partition. From my experience, that one is a bit low for long term use.

BTW: after running a system for such a long time, you may still find logfiles from the beginning (compressed by now) so there are plenty of unnecessary files.

I already mentioned this before - as a quick solution only

---

### Post by ian-weisser on 2015-03-25
> **Dragonbite said:**
> Yes, a whole bunch of them (~12+?). Basically I haven't cleaned out the kernels since I installed 12.04 back in 2013.

I moved a few of them out of the /boot directory (store them in a folder in my /home directory which is on a separate partition) to try and make space.

Use dpkg to uninstall those old, obsolete, unused kernel packages. The files you moved must be restored before dpkg will uninstall those particular packages.

When you have enough space, and apt finishes installing that newer kernel, then run 'sudo apt-get autoremove' to finish uninstalling the rest of those old kernel packages.

Example:
```
$ ls /boot
abi-**3.16.0-25-generic**         memtest86+.elf
abi**-3.16.0-30-generic**         memtest86+_multiboot.bin
abi-3.16.0-31-generic         System.map-3.16.0-25-generic
config-3.16.0-25-generic      System.map-3.16.0-30-generic
config-3.16.0-30-generic      System.map-3.16.0-31-generic
config-3.16.0-31-generic      vmlinuz-3.16.0-25-generic
grub                          vmlinuz-3.16.0-30-generic
initrd.img-3.16.0-25-generic  vmlinuz-3.16.0-30-generic.efi.signed
initrd.img-3.16.0-30-generic  vmlinuz-3.16.0-31-generic
initrd.img-3.16.0-31-generic  vmlinuz-3.16.0-31-generic.efi.signed
memtest86+.bin

$ uname -r
3.16.0-31-generic   ## Don't uninstall the running kernel! 

```

In this example, I can use dpkg to safely remove the following packages:
linux-signed-image-3.16.0-25-generic
linux-signed-image-3.16.0-30-generic
linux-image-3.16.0-25-generic
linux-image-3.16.0-30-generic
If you have old kernel header packages installed, or other kernel-specific dependencies, those can be removed, too.


The /etc/kernel/postinst.d/apt-auto-removal script is supposed to make old kernel packages eligible for autoremoval precisely so this mess doesn't occur for most users.
The setting to autoremove eligible packages is in /etc/apt/apt.conf.d/50unattended-upgrades , and is run daily by the cronjob /etc/cron.daily/apt .
Have you, by chance, disabled (or uninstalled) unattended upgrades? Or manually twiddled with the kernel packages using apt? Or disabled that cron job? Or changed the apt settings?

---

### Post by Dragonbite on 2015-03-25
> **ian-weisser said:**
> Use dpkg to uninstall those old, obsolete, unused kernel packages. The files you moved must be restored before dpkg will uninstall those particular packages.

I've already tried ```
$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)" | xargs sudo apt-get remove
``` and it failed.  Or is there another 'dpkg' command that may work?

---

### Post by ian-weisser on 2015-03-25
The error messages about *why* a command failed are important. Could be simple permission (forgot 'sudo'), could be dependencies, could be a typo, etc.

Try: sudo dpkg --remove <packagename>

---

### Post by Dragonbite on 2015-03-25
> **ian-weisser said:**
> The error messages about *why* a command failed are important. Could be simple permission (forgot 'sudo'), could be dependencies, could be a typo, etc.

Try: sudo dpkg --remove <packagename>

The error message was listed right under the command I ran in the prevous post.  This is all it showed in the terminal:

> **Dragonbite said:**
> Hmm.. that didn't work either ```
**$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)" | xargs sudo apt-get remove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.75.89) but 3.2.0.77.91 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-75-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Yes, now I see I did not use *sudo* and will have to try that tonight and see if it makes any difference.

---

### Post by bardo2 on 2015-03-25
Hi again,

i fully agree to ian-weiser. It is very difficult to guess at the pieces of information missing in this thread, and: we could be guessing wrong. So please give as much info as possible.

Of course, you are in a difficult spot, having to work with a partition, that has almost no free space. (I hope, you do not work FROM it, but use a LIVE-CD of some sort.) If you do, the system will be slow, but stable, and commands (like computer-janitor) would mostly not suffer from the limited space. At least not until you come back to the main system (hopefully fixed by then).

Also, i am uncertain about the level of understanding to expect from you. Did you create the /home partition on purpose? Or were you just following some standard install?

And finally: From what i got - up till now - i would describe your situation as follows:
apt/dpkg operations are failling due to lack of space on system partition.
The computer is running a (pretty much unmaintained installation of) precise.
You did not pick up any suggestion to get a long term solution (reasons unknown).
The thing you did was to manually move some kernels out of the way (which is quick & dirty anyways & also usually less effective than to move the corresponding initrd's with them).
I am not that fond of this aproach, because it is (in some sense) dirty, as someone said, to remove the pieces correctly, you will have to put them back first.
Also the provided commandline to remove kernels & images doesnt provide a safety-net (like i have on my machiines) of keeping a reserve kernel or two to fall back to in case of a problem.
There are other areas to get free space more easily (as i mentionned, maybe log files), and to keep EVERYTHING wouldnt make sense on a drive with that limited free space.
Nobody checked, if free space went down gradually over long time or if there has been a recent operation to exhaust free space recently (that could be undone first).

I may be able to assist you, but i dont like to make decisions for you. So you will have to take the steering wheel, ask questions, provide additional information of some sort to get me going.

Let me rephrase: The troubles you are in just happen (i am maintaining around 50 computers and i am running into this kind of problem about 2 times a year). Nothing serious about it, it can be resolved in different ways with different drawbacks. Would you please choose one? ;-) and i am going to hold your hand there. :-)

---

### Post by ian-weisser on 2015-03-25
> **Dragonbite said:**
> Hmm.. that didn't work either ```
$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)" | xargs sudo apt-get remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.75.89) but 3.2.0.77.91 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-75-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Most of it *did* work.
The problem is at the end, with apt. Those error messages are from apt.

If adding sudo still fails, use dpkg to remove the files.

Example:
```
$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)"
linux-headers-3.16.0-25
linux-headers-3.16.0-28
linux-headers-3.16.0-30
linux-headers-3.16.0-30-generic
linux-image-3.16.0-30-generic
linux-image-extra-3.16.0-30-generic
linux-signed-image-3.16.0-30-generic
```

I can use dpkg instead of apt to remove all those packages:
```
$ sudo dpkg --remove linux-headers-3.16.0-25 linux-headers-3.16.0-28 linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic linux-signed-image-3.16.0-30-generic
```

Petty stuff: See the use of sudo? 'dpkg -l' is merely informational, so  does not need sudo. 'dpkg --remove' changes the system, so requires  sudo.

---

### Post by Dragonbite on 2015-03-25
I am sorry if I am coming across the wrong way. I am very grateful for everybody here trying to help, just getting frustrated with not knowing what will and will not trash the system.

[LIST=1]
[*]For a quick answer to your questions, I set up the /home and /home/SHARE partitions myself to separate the users' files from the systems'.  
[*]I have been running the commands from the terminal on the system itself.  I didn't think about using a LiveUSB or how to make sure it is working on the installed portion rather than the LiveUSB itself.
[*]Of the 12 GB in use on the root partition, 7.3 GB alone was occupied in /usr [LIST]
[*]/usr/src for 3.2 GB (mostly the 64 *linux-header* directories occupying 89 MB or 14 MB (32 of each)
[*]/usr/lib for 2.3 GB
[*]/usr/share for 1.5 GB
[/LIST]
[/LIST]
My list of headers is a lot longer than yours. I notice that I have *linux-headers-3.2.0-40* and *linux-headers-3.2.0-40-generic* and I don't know why or whether this is supposed to be.  ```
drew@dragon:~$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)"
linux-headers-3.2.0-23
linux-headers-3.2.0-23-generic
linux-headers-3.2.0-36
linux-headers-3.2.0-36-generic
linux-headers-3.2.0-37
linux-headers-3.2.0-37-generic
linux-headers-3.2.0-38
linux-headers-3.2.0-38-generic
linux-headers-3.2.0-39
linux-headers-3.2.0-39-generic
linux-headers-3.2.0-40
linux-headers-3.2.0-40-generic
linux-headers-3.2.0-41
linux-headers-3.2.0-41-generic
linux-headers-3.2.0-43
linux-headers-3.2.0-43-generic
linux-headers-3.2.0-44
linux-headers-3.2.0-44-generic
linux-headers-3.2.0-45
linux-headers-3.2.0-45-generic
linux-headers-3.2.0-48
linux-headers-3.2.0-48-generic
linux-headers-3.2.0-49
linux-headers-3.2.0-49-generic
linux-headers-3.2.0-51
linux-headers-3.2.0-51-generic
linux-headers-3.2.0-52
linux-headers-3.2.0-52-generic
linux-headers-3.2.0-53
linux-headers-3.2.0-53-generic
linux-headers-3.2.0-54
linux-headers-3.2.0-54-generic
linux-headers-3.2.0-55
linux-headers-3.2.0-55-generic
linux-headers-3.2.0-56
linux-headers-3.2.0-56-generic
linux-headers-3.2.0-57
linux-headers-3.2.0-57-generic
linux-headers-3.2.0-58
linux-headers-3.2.0-58-generic
linux-headers-3.2.0-59
linux-headers-3.2.0-59-generic
linux-headers-3.2.0-60
linux-headers-3.2.0-60-generic
linux-headers-3.2.0-61
linux-headers-3.2.0-61-generic
linux-headers-3.2.0-63
linux-headers-3.2.0-63-generic
linux-headers-3.2.0-64
linux-headers-3.2.0-64-generic
linux-headers-3.2.0-65
linux-headers-3.2.0-65-generic
linux-headers-3.2.0-67
linux-headers-3.2.0-67-generic
linux-headers-3.2.0-68
linux-headers-3.2.0-68-generic
linux-headers-3.2.0-69
linux-headers-3.2.0-69-generic
linux-headers-3.2.0-70
linux-headers-3.2.0-70-generic
linux-headers-3.2.0-72
linux-headers-3.2.0-72-generic
linux-headers-3.2.0-74
linux-headers-3.2.0-74-generic
linux-image-3.2.0-63-generichave managed to run
linux-image-3.2.0-64-generic
linux-image-3.2.0-65-generic
linux-image-3.2.0-67-generic
linux-image-3.2.0-68-generic
linux-image-3.2.0-69-generic
linux-image-3.2.0-70-generic
linux-image-3.2.0-72-generic
linux-image-3.2.0-74-generic
linux-image-3.2.0-75-generic
drew@dragon:~$ 

```
I ran (with sudo ;) ) ```
sudo dpkg --remove linux-headers-3.2.0-3*
sudo dpkg --remove linux-headers-3.2.0-4*
sudo dpkg --remove linux-headers-3.2.0-5*
``` leaving me with with a much smaller list of linux-headers and more space in the partitions (/dev/sda2 was showing 100% IUse% when I ran **df -i** before!
```
drew@dragon:~$ df -h && echo && df -i
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        15G  9.7G  3.8G  73% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           591M  1.4M  590M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G   27M  2.9G   1% /run/shm
/dev/sda3        58G   51G  4.4G  92% /home
/dev/sda4       142G   93G   42G  70% /home/SHARE

Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda2       936560 497856  438704   54% /
udev            753554    513  753041    1% /dev
tmpfs           755753    446  755307    1% /run
none            755753      4  755749    1% /run/lock
none            755753    112  755641    1% /run/shm
/dev/sda3      3824928 349680 3475248   10% /home
/dev/sda4      9420800  88429 9332371    1% /home/SHARE
drew@dragon:~$ 

```


So it appears some space has been opened up.

---

### Post by Dragonbite on 2015-03-25
At least the error has changed.

After removing all of the packages so that the *linux-headers* have a corresponding *linux-image* I get ```
drew@dragon:/var/log$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)"
linux-headers-3.2.0-63
linux-headers-3.2.0-63-generic
linux-headers-3.2.0-64
linux-headers-3.2.0-64-generic
linux-headers-3.2.0-65
linux-headers-3.2.0-65-generic
linux-headers-3.2.0-67
linux-headers-3.2.0-67-generic
linux-headers-3.2.0-68
linux-headers-3.2.0-68-generic
linux-headers-3.2.0-69
linux-headers-3.2.0-69-generic
linux-headers-3.2.0-70
linux-headers-3.2.0-70-generic
linux-headers-3.2.0-72
linux-headers-3.2.0-72-generic
linux-headers-3.2.0-74
linux-headers-3.2.0-74-generic
linux-headers-3.2.0-79
linux-headers-3.2.0-79-generic
linux-image-3.2.0-63-generic
linux-image-3.2.0-64-generic
linux-image-3.2.0-65-generic
linux-image-3.2.0-67-generic
linux-image-3.2.0-68-generic
linux-image-3.2.0-69-generic
linux-image-3.2.0-70-generic
linux-image-3.2.0-72-generic
linux-image-3.2.0-74-generic
linux-image-3.2.0-75-generic
linux-image-3.2.0-79-generic
``` so I tried running **sudo apt-get -f install** and now get ```
drew@dragon:/var/log$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 0 newly installed, 0 to remove and 161 not upgraded.
3 not fully installed or removed.
Need to get 0 B/6,518 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  Package linux-image-3.2.0-77-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-75-generic; however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            Package linux-headers-3.2.0-75-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.75.89); however:
  Version of linux-image-generic on system is 3.2.0.77.91.
 linux-generic depends on linux-headers-generic (= 3.2.0.75.89); however:
  Package linux-headers-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                  Errors were encountered while processing:
 linux-image-generic
 linux-headers-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
drew@dragon:/var/log$ 
```Which points to ```

dpkg: dependency problems prevent configuration of *linux-image-generic*:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  **Package linux-image-3.2.0-77-generic is not installed.**
``` and ```
dpkg: dependency problems prevent configuration of* linux-headers-generic*:
 linux-headers-generic depends on linux-headers-3.2.0-75-generic; however:
No apport report written because the error message indicates its a followup error from a previous failure.
   **Package linux-headers-3.2.0-75-generic is not installed.** 
``` and ```

dpkg: dependency problems prevent configuration of *linux-generic*:
 linux-generic depends on linux-image-generic (= 3.2.0.75.89); however:
  Version of linux-image-generic on system is 3.2.0.77.91.
 linux-generic depends on linux-headers-generic (= 3.2.0.75.89); however:
  **Package linux-headers-generic is not configured yet.** 
```

Does this mean I need to manually install **linux-headers-3.2.0-77-generic** and **linux-headers-3.2.0-75-generic**?

---

### Post by ian-weisser on 2015-03-25
> **Dragonbite said:**
> Does this mean I need to manually install **linux-headers-3.2.0-77-generic** and **linux-headers-3.2.0-75-generic**?

No. Don't do that.

Try:
```
sudo apt-get update           ## Refresh the package database
sudo apt-get autoremove       ## OPTIONAL - Clear out any remaining unused dependencies (orphans). If there are orphans, read the list carefully before hitting 'Y'.
sudo apt-get upgrade          ## Update packages to the newest version. This may take a while - you have 161 upgrades queued
sudo apt-get dist-upgrade     ## Use only if kernel packages are not upgraded by the previous command
```

-f (--fix missing) is different from 'upgrade' (update everything to the latest version)
--fix  missing tells apt to download and install missing dependencies for  what is currently installed (older kernel versions)...which will fail, the older versions are no  longer in the repositories *and* the older versions are incompatible with newer versions that have not been downloaded and installed yet.
'upgrade' tells apt to try to move all the packages to the latest version...which have been tested to be compatible with each other.

Congratulations. You have made tremendous progress.
You have successfully cleaned out loads of old packages -- a proper way.
You have successfully freed up a ton of disk space.
You have successfully cleared the biggest problem blocking apt from functioning ('no space left on device').
Now that apt can (somewhat) function, everything else is *easy*.

Let us know how it goes. Especially cryptic output or errors.

---

### Post by bardo2 on 2015-03-25
> **Dragonbite said:**
> I am sorry if I am coming across the wrong way. I am very grateful for everybody here trying to help, just getting frustrated with not knowing what will and will not trash the system.

Ah, yes, of course. Sorry, i did not mean to be rude in any way.
> **Dragonbite said:**
>  
[LIST=1]
[*]For a quick answer to your questions, I set up the /home and /home/SHARE partitions myself to separate the users' files from the systems'. 
[*]I have been running the commands from the terminal on the system itself.  I didn't think about using a LiveUSB or how to make sure it is working on the installed portion rather than the LiveUSB itself. 
[*]Of the 12 GB in use on the root partition, 7.3 GB alone was occupied in /usr
[LIST]
[*]/usr/src for 3.2 GB (mostly the 64 *linux-header* directories occupying 89 MB or 14 MB (32 of each) 
[*]/usr/lib for 2.3 GB 
[*]/usr/share for 1.5 GB 
[/LIST]
   
[/LIST]
My list of headers is a lot longer than yours. I notice that I have *linux-headers-3.2.0-40* and *linux-headers-3.2.0-40-generic* and I don't know why or whether this is supposed to be.  

Ok, let me check something on an older precise install over here (most machines already upgraded to trusty)
Oh - coming back later: emergency over here: a backup on one of my machines failed... :-(
tbc...

---

### Post by bardo2 on 2015-03-25
Ok, i am back. The error message over here was just bogus. :-)

I have to agree, you achieved great progress in the meantime. You are doing fine!
And i am very grateful for all the info you provided, especially the questions, that came with them.

I will try to get there one by one:
One explanation upfront: the unattended-upgrades-package changed its behavior tremendously from precise to trusty. So on trusty, it is clearing up kernels behind itself - in a way - which precise couldnt.
-> dont even think about using it, while you still are on precise!

Next: i checked your directory: /usr/src and yes, there accumulated all sorts of kernel-related sources/headers, which mostly arent needed any more (except for removal).
When i ran my "old-kernel-remove-script", those directories got purged as well, although the script only did something similar to apt-get purge ... 
There comes my expectation: it is fantastic, that apt is working again. So the emergency status somehow changed into "mildly important maintenance" left over. 
Although this may be somewhat fragile. I still would be extremely careful installing/uninstalling kernel related stuff, since you moved kernels around without apt/dpkg knowing about that move.
I am not deep enough into those tools to hint you towards a shortcut (it may exist, though!). But for sure, those tools can operate, while & if you restore a state, they expect (like kernels, where they were,...)
But i can understand, you seem to have been using the breathing room immediately and without any prep, thus i am not certain, what state the package managers are in by now.

Luckily, there is no immediate time pressure, so we can investigate that slowly. :-)

Because of the many recent changes, my understanding/diagnosis is outdated anyway and i would like to get started looking fresh:

What is the situation? What is NOT as you want it to be? How can I/we help?
Certainly the lack of space no longer is the primary issue by now, which is a good thing!

> **Dragonbite said:**
> At least the error has changed.

Does this mean I need to manually install **linux-headers-3.2.0-77-generic** and **linux-headers-3.2.0-75-generic**?

No, this is induced be the movement of kernel files from /boot to /home and will in all likelyhood disappear, once you restored the missing files

---

### Post by Dragonbite on 2015-03-25
> **ian-weisser said:**
> No. Don't do that.

Try:
```
sudo apt-get update           ## Refresh the package database
sudo apt-get autoremove       ## OPTIONAL - Clear out any remaining unused dependencies (orphans). If there are orphans, read the list carefully before hitting 'Y'.
sudo apt-get upgrade          ## Update packages to the newest version. This may take a while - you have 161 upgrades queued
sudo apt-get dist-upgrade     ## Use only if kernel packages are not upgraded by the previous command
```

-f (--fix missing) is different from 'upgrade' (update everything to the latest version)
--fix  missing tells apt to download and install missing dependencies for  what is currently installed (older kernel versions)...which will fail, the older versions are no  longer in the repositories *and* the older versions are incompatible with newer versions that have not been downloaded and installed yet.
'upgrade' tells apt to try to move all the packages to the latest version...which have been tested to be compatible with each other.

Congratulations. You have made tremendous progress.
You have successfully cleaned out loads of old packages -- a proper way.
You have successfully freed up a ton of disk space.
You have successfully cleared the biggest problem blocking apt from functioning ('no space left on device').
Now that apt can (somewhat) function, everything else is *easy*.

Let us know how it goes. Especially cryptic output or errors.

Running *sudo apt-get update* then *sudo apt-get upgrade -f* seemed to have made somewhat a difference. It appears to have run through updating the other pending packages but continues to get caught on the same 3 dependency errors ```
 linux-generic : Depends: linux-image-generic (= 3.2.0.75.89) but 3.2.0.77.91 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-75-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not installed
```

Running *sudo apt-get autoremove* and *sudo apt-get autoremove -f * did not yield anything new.  Nor does running *sudo apt-get upgrade* (without **-f**).

Before I run *sudo apt-get dist-upgrade* I need to know, is that the command for updating Ubuntu from one version to anther (in this case from 12.04 to either 12.10 or 14.04)?

I know it sounds like a dangerous idea, but what if I [LIST=1]
[*]Boot into an oldest kernel (such as 3.2.0-63), though I don't know how...
[*]Using *dpkg --remove*, remove the NEWER kernels.. everything from -75 (which is mentioned as a failing point) on up
Not sure if should also remove *linux-generic*, *linux-headers-generic* and *linux-image-generic*
[*]Run the *sudo apt-get upgrade * in hopes that the system will try to skip over the ones in question and not finding any of the latest ones, install the latest version only
[/LIST]
Does this sound like something that might work, or that it is going to break something significant?

I'm not about to do it tonight since it is getting late.

---

### Post by bardo2 on 2015-03-25
> **Dragonbite said:**
> 
Before I run *sudo apt-get dist-upgrade* I need to know, is that the command for updating Ubuntu from one version to anther (in this case from 12.04 to either 12.10 or 14.04)?

sudo do-release-upgrade (do a man "do-release-upgrade" first to see the arguments available)

> **Dragonbite said:**
> 
I know it sounds like a dangerous idea, but what if I
[LIST=1]
[*]Boot into an oldest kernel (such as 3.2.0-63), though I don't know how... 
[*]Using *dpkg --remove*, remove the NEWER kernels.. everything from -75 (which is mentioned as a failing point) on up
Not sure if should also remove *linux-generic*, *linux-headers-generic* and *linux-image-generic* 
[*]Run the *sudo apt-get upgrade * in hopes that the system will try to skip over the ones in question and not finding any of the latest ones, install the latest version only 
[/LIST]
Does this sound like something that might work, or that it is going to break something significant?

I'm not about to do it tonight since it is getting late.

1. what would be the intention of booting an older kernel? (apart from NOT using the current one)?
no need to. IMO
2. no need to remove the newer ones either. The mess - as explained before - is certainly, that the package manager simply doesn't find the kernels you moved to /home. move those back and go on...
3. No, that doesnt sound so good.
The following info may not be necessary, but i am giving it anyway:
linux-generic (and some of the other as well) is a VIRTUAL package. That means, it doesnt contain any files. Instead, it is a configuration trick, because it contains PACKAGES, and the distro updates the pointer to the most current package only. Thus installing it will always get you the uptodate kernel, image, header files in one go. Neat, isn't it?
That is why you shouldn't touch those, unless you know what you are doing.

And i agree, good time to sleep over it. you made great progress today and will need some insight and especially self-control for the next steps to not just mess it up again.
BTW: you should NOT upgrade to trusty from a system with a dubious config: results will be unpredictable at best.

your options will be:
- Fix the old System and then upgrade
- install a fresh one directly

in both cases, i do strongly recommend to backup first!

---

### Post by v3.xx on 2015-03-26
I wonder if dpkg can do any good.
```
sudo dpkg --configure -a
man dpkg
```
I don't think your system will do a version upgrade until current repairs are made.  Even if you could, I would not recommend it because of the chance of more breakage.

Do the offending kernels appear in /boot?  At this point my vote would be to remove the offending kernels.  Ian-weisser may not agree, but thats my best guess :)

Be sure about what kernel you are currently using.
```
uname -r
```

---

### Post by ian-weisser on 2015-03-26
> **Dragonbite said:**
> ```
 linux-generic : Depends: linux-image-generic (= 3.2.0.75.89) but 3.2.0.77.91 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-75-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not installed
```

Running *sudo apt-get autoremove* and *sudo apt-get autoremove -f * did not yield anything new.  Nor does running *sudo apt-get upgrade* (without **-f**).

If you have tried dist-upgrade (which really should solve the problem), try:
```
sudo apt-get install **--reinstall** linux-generic linux-headers-generic linux-image-generic
```

dist-upgrade will upgrade you to the next release of Debian, **if you are running Debian*.***
On Ubuntu it most certainly does **not** upgrade you to the next release of Debian.

---

### Post by Dragonbite on 2015-03-26
Ok, I have a few moments before I have to leave the house.  Last night I moved the files previously moved from /boot back where they belong.

Running these commands[LIST]
[*]sudo apt-get dist-upgrade
[*]sudo dpkg --configure -a
[/LIST] Produces the following message:
```
drew@dragon:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.75.89) but 3.2.0.77.91 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-75-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

Running these command [LIST]
[*]sudo apt-get dist-upgrade
[*]sudo apt-get install --reinstall linux-generic linux-headers-generic linux-image-generic
[/LIST] Produces the following message:
```
drew@dragon:~$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/6,518 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  Package linux-image-3.2.0-77-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-75-generic; however:
  Package linux-headers-3.2.0-75-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.75.89); however:
  Version of linux-image-generic on system is 3.2.0.77.91.
 linux-generic depends on linux-headers-generic (= 3.2.0.75.89); however:
  Package linux-headers-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-generic
 linux-headers-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
drew@dragon:~$ 

```

I am able to install and remove applications using **dpkg** (e.g. *sudo dpkg --remove leafpad*), but not apt-get.

The offending files (*linux-image-3.2.0-77-generic* & *linux-headers-3.2.0-75-generic*) are not installed
```
drew@dragon:~$ dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)"
linux-headers-3.2.0-63
linux-headers-3.2.0-63-generic
linux-headers-3.2.0-64
linux-headers-3.2.0-64-generic
linux-headers-3.2.0-65
linux-headers-3.2.0-65-generic
linux-headers-3.2.0-67
linux-headers-3.2.0-67-generic
linux-headers-3.2.0-68
linux-headers-3.2.0-68-generic
linux-headers-3.2.0-69
linux-headers-3.2.0-69-generic
linux-headers-3.2.0-70
linux-headers-3.2.0-70-generic
linux-headers-3.2.0-72
linux-headers-3.2.0-72-generic
linux-headers-3.2.0-74
linux-headers-3.2.0-74-generic
linux-image-3.2.0-63-generic
linux-image-3.2.0-64-generic
linux-image-3.2.0-65-generic
linux-image-3.2.0-67-generic
linux-image-3.2.0-68-generic
linux-image-3.2.0-69-generic
linux-image-3.2.0-70-generic
linux-image-3.2.0-72-generic
linux-image-3.2.0-74-generic
linux-image-3.2.0-75-generic
linux-image-3.2.0-76-generic

``` and my current version running is ```
drew@dragon:~$ uname -r
3.2.0-79-generic

```

Is there another way to configure these 3 components, or to manually install the missing versions?  I will be reading the **dpkg** man pages and see what, if anything, can be done (--configure, --purge, dpkg-query, etc.)

*I just noticed that the version currently being run (3.2.0-79) is not in the list pulled up by the dpkg command.  I think this is on purpose, as the command was being built up to something to delete the non-latest kernel.  Would removing all, but the latest, kernel help or hurt in this situation?*

---

### Post by ian-weisser on 2015-03-26
Hmmmm.

Try:
```
sudo dpkg --remove linux-image-generic linux-headers-generic linux-generic
sudo apt-get update
sudo apt-get autoclean       ## Remove older versions of packages
sudo apt-get install linux-image-generic linux-headers-generic linux-generic
```

---

### Post by Dragonbite on 2015-03-26
> **ian-weisser said:**
> Hmmmm.

Try:
```
sudo dpkg --remove linux-image-generic linux-headers-generic linux-generic
sudo apt-get update
sudo apt-get autoclean       ## Remove older versions of packages
sudo apt-get install linux-image-generic linux-headers-generic linux-generic
```

And with **_[SIZE=4]that[/SIZE]_**, the errors are all gone! \\:D/ The system appears to be running fine with no errors using apt-get or the Ubuntu Software Center!

Thank you to everybody for your time and patience. :KS

To summarize the situation, and please correct me if I am wrong, there was 
[LIST=1]
[*]the root partition running out of space which did now show up with *df -h* but did show with *df -i*.  What exactly does the *-i*, or inode, show me?
[*]because the root partition ran out of space the kernels were not fully configured or had all of the bits in line
[*]cleared out the old, unused kernels to make space by using ```
#first, detect the list of kernels
dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -v -e `uname -r|cut -f1,2 -d"-"` | grep -e[0-9] | grep -E "(image|header)"

# then remove those kernels you do not want
sudo dpkg --remove linux-headers-3.2.0-63-generic linux-headers-3.2.0-63 linux-headers-3.2.0-64-generic linux-headers-3.2.0-64

```
[*]then seeing that the missing files were keeping from the kernel files (linux-image-generic, linux-headers-generic & linux-generic) from properly configuring, run ```
##remove the failing programs
sudo dpkg --remove linux-image-generic linux-headers-generic linux-generic

sudo apt-get update

## Remove older versions of packages
sudo apt-get autoclean       

## Reinstall the pieces previously removed
sudo apt-get install linux-image-generic linux-headers-generic linux-generic
```
[/LIST]

Thank you all again, because without you guys I probably would not have figured this out on my own!  Take a bow! =d>

Is there an easier way to maintain these kernels or safely remove them every once-in-a-while (but be able to leave 1-2+ for backups?

---

### Post by bardo2 on 2015-03-26
Heads up, very good post there, useful information, makes it a pleasure to help. :-)

> **Dragonbite said:**
> Ok, I have a few moments before I have to leave the house.  Last night I moved the files previously moved from /boot back where they belong.

Running these commands
[LIST]
[*]sudo apt-get dist-upgrade 
[*]sudo dpkg --configure -a 
[/LIST]
Produces the following message:
```
drew@dragon:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.75.89) but 3.2.0.77.91 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-75-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

Ok. you are on your way...
linux-generic (a VIRTUAL package)  points to an OLDER kernel than the one you have installed.
WOW! I cannot recall seeing this message ever on one of my computers. And because of that, i cannot safely suggest a proven solution from my own experience. doh!
Still, i will not run away. Only go slower than before, because from here on, i have nothing to compare, and even no idea, how we even got there.

...but wait, maybe i can introduce this situation artificially over here and see, how to get over it in a clean way...

(timeout ahead)

> **Dragonbite said:**
> 
Running these command
[LIST]
[*]sudo apt-get dist-upgrade 
[*]sudo apt-get install --reinstall linux-generic linux-headers-generic linux-image-generic 
[/LIST]
Produces the following message:
```
drew@dragon:~$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/6,518 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  Package linux-image-3.2.0-77-generic is not installed.

```
Ok. Useful again. dependency problem identified. will try my approach over here first before posting it.
> **Dragonbite said:**
> 
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-75-generic; however:
  Package linux-headers-3.2.0-75-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.75.89); however:
  Version of linux-image-generic on system is 3.2.0.77.91.
 linux-generic depends on linux-headers-generic (= 3.2.0.75.89); however:
  Package linux-headers-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-generic
 linux-headers-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
drew@dragon:~$ 
[/code]
I am able to install and remove applications using **dpkg** (e.g. *sudo dpkg --remove leafpad*), but not apt-get.

yes, i see. we will get to that one later.

> **Dragonbite said:**
> 
Is there another way to configure these 3 components, or to manually install the missing versions?  I will be reading the **dpkg** man pages and see what, if anything, can be done (--configure, --purge, dpkg-query, etc.)

yes, but... let me check a few things over here first. i do not want to mess up your system any further, since i still dont know, how we may have accidentally introduced it.
And just throwing powerful commands at the situation (like sudo ....) should be done understanding the responsibility involved.
> **Dragonbite said:**
> 
*I just noticed that the version currently being run (3.2.0-79) is not in the list pulled up by the dpkg command.  I think this is on purpose, as the command was being built up to something to delete the non-latest kernel.  Would removing all, but the latest, kernel help or hurt in this situation?*
Excellent observation. I think we are getting at the heart of the matter here.

Will now do some testing here before i come back to you.

Did i get your decision right? you are opting for
1) fix old install first, then backup, then upgrade release?

---

### Post by bardo2 on 2015-03-26
> **Dragonbite said:**
> And with **_[SIZE=4]that[/SIZE]_**, the errors are all gone! \\:D/ The system appears to be running fine with no errors using apt-get or the Ubuntu Software Center!

Wow. Hopefully, this will hold true. And it may...
> **Dragonbite said:**
> 
To summarize the situation, and please correct me if I am wrong, there was 
[LIST=1]
[*]the root partition running out of space which did now show up with *df -h* but did show with *df -i*.  What exactly does the *-i*, or inode, show me? 
[/LIST]

Seems like i missed that one... :-)
Now you had choices and opted for a short-term-solution only, leaving the longer lasting partition resize for later!

Ok, i am suffering just now from the limitations of this interface: properly quoting parts of your enumeration is very difficult. I wll stop that and just comment:
after removing the virtual packages, your system was temporarily hanging out in the dry (something i wouldnt have dared to recommend.)
lucky you did it and did fine with it.
apt-get autoclean removes packages FROM THE CACHE only, not from the system (fundamental misunderstanding! but who cares?)
> **Dragonbite said:**
> 
Is there an easier way to maintain these kernels or safely remove them every once-in-a-while (but be able to leave 1-2+ for backups?
Yes, i always used my "maintanance script" and executed it manually, when i felt the list grew too big. I even had the amount of kernels kept as a variable.
Only drawback: i wrote this script years ago and probably didnt do it the right way. I had one occurrence, where it failed on a machine with installed lts-enablement stack.
So you may finf a better one on the net.
but to get started: here it is.
```
#!/bin/bash
set -e # -v -x
# remove old kernels
KEEP=${1:-2}

apt-get -qy autoremove --purge
apt-get clean

pushd /usr/share/doc > /dev/null # That is NOT how it should be done!
EXCEPT=`ls -d1 linux-image-3* | tail -n $KEEP | awk 'BEGIN { s = ""; } { gsub ("-?[a-z]+", "");s = s "|" $0; } END { print substr (s,2);}'`
popd >/dev/null

dpkg -l "linux-*" | awk '/^ii\ *linux-(headers|image)-3/ {print $2;}' | grep -vEe "$EXCEPT" | xargs -r apt-get -y purge

```
and it requires sudo while executing it. (some checks have been removed because they refer to my local setups.)

---

### Post by ian-weisser on 2015-03-26
> **Dragonbite said:**
> And with that, the errors are all gone! 

Very happy to see that you got it sorted.


> **Dragonbite said:**
> Is there an easier way to maintain these kernels or safely remove them  every once-in-a-while (but be able to leave 1-2+ for backups?

Yes. The system usually does it automatically. The explanation is buried back in Post #18:

> **ian-weisser said:**
> The /etc/kernel/postinst.d/apt-auto-removal  script is supposed to make old kernel packages eligible for autoremoval  precisely so this mess doesn't occur for most users.
The setting to autoremove eligible packages is in  /etc/apt/apt.conf.d/50unattended-upgrades , and is run daily by the  cronjob /etc/cron.daily/apt .
Have you, by chance, disabled (or uninstalled) unattended upgrades? Or  manually twiddled with the kernel packages using apt? Or disabled that  cron job? Or changed the apt settings

Automatic remove won't work if you 1) Specify a kernel version, 2) Uninstall the 'unattended-upgrades' package, 3) Disable autoremoval in the apt settings, 4) Disable the cronjob, or 5) Have some unrelated bug.

If automatic removal doesn't seem to be working, then first try 'sudo apt-get autoremove' once each month or so.
If 'autoremove' doesn't work, then there's something fishy going on, but meanwhile you can order apt to remove the old, unused kernel packages. You now are experienced at finding which packages are eligible for safe removal.

---

### Post by bardo2 on 2015-03-27
-

---

### Post by v3.xx on 2015-03-27
Nice :D

---

### Post by TheFu on 2015-03-31
Didn't see the answer for the difference between 
df -h  # disk space available

df -i  # i-nodes available

this really goes back to how file systems maintain lists of blocks used.  There is a directory entry and an i-node.  The directory knows about the i-node and the i-node knows about the file's blocks on disk. This is handy because you can have different directories refer to teh same i-node - effectively putting the identical contents of a file (or thousands of files) into 2 or more directory locations.

A better i-node explanation: [https://en.wikipedia.org/wiki/Inode](https://en.wikipedia.org/wiki/Inode)

When a file system is created, some number of slots are made to hold i-nodes.  If those are full, then no more files can be created even if the disk is 99% empty.  For ext4 partitions with 10G or more storage, the default number of i-nodes hasn't been an issue for me or anyone I know. However, there are installation defaults - if you use LVM or encrypt the entire disk - where a relatively tiny partition is created for /boot - usually under 500MB.  If there are a few large files, i-nodes will not run out. However, on a 4G or smaller partition with thousands and thousands of small files - like a perl, python, php, ruby, website might have, running out of i-nodes can easily happen.  During the creation of the file system, it is possible to change the default number of i-nodes, but almost nobody does that. It usually doesn't become an issue for 2-4 yrs - then it is a huge issue.

For a separate /boot partition, it is much more likely that having more than 5 kernels will fill the space up, so I like to keep only 3 kernels on any machine.
There are other [maintenance items that an Ubuntu desktop]("http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs") needs - be certain to do them to keep out of trouble.

Oh - and you don't have to wait for people to answer questions. Your system has a built-in manual system - manpages - which contain about 60% of the answers you seek.  **man du** and check out the different options.

---

