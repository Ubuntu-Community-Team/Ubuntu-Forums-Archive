---
title: "Problem with removing &quot;linux-image-3.13.0-45-generic&quot; package"
date: 2015-05-08
forum: General Help
---

### Post by Ahmad_Ahmadi on 2015-05-08
After installing Windows 8.1 over ubuntu 14.04 installation and fixed dual boot problem by Boot-Repair tool, I had several problems with *linux-image-3.13.0-45-generic* package.
I tried to reconfigure this package or install its depency but I always get same error.

How can I get rid of these problems?

```
hakan@hakan-ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 324 not upgraded.
3 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package linux-image-3.13.0-45-generic (--configure):
 package linux-image-3.13.0-45-generic is not ready for configuration
 cannot configure (current status `half-installed')
Setting up extlinux (3:4.05+dfsg-6+deb8u1) ...
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-52-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Writing config for Windows 8 (loader) on /dev/sda2...
P: Installing debian theme...cp: cannot stat ‘/usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin’: No such file or directory
dpkg: error processing package extlinux (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-45-generic:
 linux-image-extra-3.13.0-45-generic depends on linux-image-3.13.0-45-generic; however:
  Package linux-image-3.13.0-45-generic is not installed.

dpkg: error processing package linux-image-extra-3.13.0-45-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-3.13.0-45-generic
 extlinux
 linux-image-extra-3.13.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QDR06VV9 on 2015-05-08
Not real sure I can get you sorted out.
but at least we will get the ball rolling here, and maybe someone else will step in.
Will you open a terminal and input.
The code below will show installed kernels
```
dpkg -l linux-* | awk '/^ii/{ print $2 }'

```
And paste the results back here.
kind regards

---

### Post by Ahmad_Ahmadi on 2015-05-09
Here is the result:

```
hakan@hakan-ubuntu:~$ dpkg -l linux-* | awk '/^ii/{ print $2 }'
linux-firmware
linux-generic
linux-headers-3.13.0-45
linux-headers-3.13.0-45-generic
linux-headers-3.13.0-52
linux-headers-3.13.0-52-generic
linux-headers-generic
linux-image-3.13.0-52-generic
linux-image-extra-3.13.0-52-generic
linux-image-generic
linux-libc-dev:amd64
linux-libc-dev:i386
linux-sound-base
```

---

### Post by Bucky Ball on 2015-05-09
Welcome. That image is old. Open a terminal and try:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Report any and all errors. These commands 'should' remove any redundant kernels (like the -45). It will ask first. These commands will NOT upgrade you to the newest release, just upgrade any software in your current release that needs it. 

You can also remove that kernel by opening Synaptic Package Manager, searching for 'linux image 3.13.0-45' and deleting.

Do you want to keep that kernel or try and fix it? If so, I wouldn't bother as, as I say, it is dated. We're up to -52 now, as I think you are running it.

PS: Prior to removing kernels, open a terminal and check you are not removing the one you are currently running with 'uname -a'.

---

### Post by Ahmad_Ahmadi on 2015-05-09
When I tried to remove *linux-image-3.13.0-45-generic* by Synaptic, I got same error message as my first post in detailed view and this short message:
```
E: linux-image-extra-3.13.0-45-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-3.13.0-45-generic: package is in a very bad inconsistent state; you should  reinstall it before attempting a removal
```

I tried reinstall *linux-image-3.13.0-45-generic*, but again I got same error.

After running *sudo apt-get autoremove* I got that error message again:

```
hakan@hakan-ubuntu:~$ sudo apt-get autoclean
[sudo] password for hakan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hakan@hakan-ubuntu:~$ sudo apt-get clean
hakan@hakan-ubuntu:~$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 324 not upgraded.
3 not fully installed or removed.
Need to get 15.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://ir.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-45-generic amd64 3.13.0-45.74 [15.1 MB]
Fetched 15.1 MB in 4min 14s (59.4 kB/s)                                        
dpkg: error processing package linux-image-3.13.0-45-generic (--configure):
 package linux-image-3.13.0-45-generic is not ready for configuration
 cannot configure (current status `half-installed')
Setting up extlinux (3:4.05+dfsg-6+deb8u1) ...
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-52-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Writing config for Windows 8 (loader) on /dev/sda2...
P: Installing debian theme...cp: cannot stat &#8216;/usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin&#8217;: No such file or directory
dpkg: error processing package extlinux (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-45-generic:
 linux-image-extra-3.13.0-45-generic depends on linux-image-3.13.0-45-generic; however:
  Package linux-image-3.13.0-45-generic is not installed.

dpkg: error processing package linux-image-extra-3.13.0-45-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-3.13.0-45-generic
 extlinux
 linux-image-extra-3.13.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


By running **uname -a** I noticed my kernel version is **3.13.0-52-generic**.

I dont want to do anything special with the kernel, I just want to fix this problem. :D

I think there is a problem with **extlinux**, but I dont know what it is. Maybe the answer is in the error itself, but I can't read it. :D

Thanks for your helps.

---

### Post by QDR06VV9 on 2015-05-09
I think one more try  if you don't mind.
This next command is just a dry-run it won't do anything but show what will be removed.
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e  `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"  | xargs sudo apt-get --dry-run remove


```
And again paste the results.
regards

---

### Post by Ahmad_Ahmadi on 2015-05-09
Oh, I love these commands...

```
hakan@hakan-ubuntu:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e  `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"  | xargs sudo apt-get --dry-run remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-3.13.0-52-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following packages will be REMOVED:
  linux-headers-3.13.0-45 linux-headers-3.13.0-45-generic
  linux-image-extra-3.13.0-45-generic
The following packages will be upgraded:
  linux-image-3.13.0-52-generic
1 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
5 not fully installed or removed.
Remv linux-image-extra-3.13.0-45-generic [3.13.0-45.74]
Inst linux-image-3.13.0-52-generic [3.13.0-52.85] (3.13.0-52.86 Ubuntu:14.04/trusty-security [amd64])
Remv linux-headers-3.13.0-45-generic [3.13.0-45.74]
Remv linux-headers-3.13.0-45 [3.13.0-45.74]
Conf linux-image-3.13.0-45-generic (3.13.0-45.74 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-3.13.0-52-generic (3.13.0-52.86 Ubuntu:14.04/trusty-security [amd64])
Conf extlinux (3:4.05+dfsg-6+deb8u1 Ubuntu:14.04/trusty [amd64])
Conf linux-image-extra-3.13.0-52-generic (3.13.0-52.86 Ubuntu:14.04/trusty-security [amd64])
```

I ran another command too, to fix/recovery this bad state:

```
hakan@hakan-ubuntu:~$ sudo dpkg --configure -a
Setting up extlinux (3:4.05+dfsg-6+deb8u1) ...
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-52-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Writing config for Windows 8 (loader) on /dev/sda2...
P: Installing debian theme...cp: cannot stat &#8216;/usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin&#8217;: No such file or directory
dpkg: error processing package extlinux (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-52-generic:
 linux-image-extra-3.13.0-52-generic depends on linux-image-3.13.0-52-generic; however:
  Package linux-image-3.13.0-52-generic is not installed.

dpkg: error processing package linux-image-extra-3.13.0-52-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 extlinux
 linux-image-extra-3.13.0-52-generic
```

Just extlinux and its errors...

---

### Post by QDR06VV9 on 2015-05-09
I wish you would have waited to run that second command.
But lets see if we can get things right with this.
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```
As i am not in front of your monitor probably would be a good idea to paste those results back here again before saying yes.
Thanks for your patience.
Regards

---

### Post by Ahmad_Ahmadi on 2015-05-09
```
hakan@hakan-ubuntu:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
[sudo] password for hakan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-3.13.0-52-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following packages will be REMOVED:
  linux-headers-3.13.0-45* linux-headers-3.13.0-45-generic*
  linux-image-extra-3.13.0-45-generic
The following packages will be upgraded:
  linux-image-3.13.0-52-generic
1 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/30.3 MB of archives.
After this operation, 229 MB disk space will be freed.
(Reading database ... 286979 files and directories currently installed.)
Removing linux-image-extra-3.13.0-45-generic (3.13.0-45.74) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-45-generic
grep: /boot/config-3.13.0-45-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_Keje8H/lib/modules/3.13.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_Keje8H/lib/modules/3.13.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-52-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Writing config for Windows 8 (loader) on /dev/sda2...
P: Installing debian theme...cp: cannot stat &#8216;/usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin&#8217;: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QDR06VV9 on 2015-05-09
At this point I am at a loss???
It would appear something got deleted or renamed.(Just a Guess)
As it is maybe this post would of help [http://ubuntuforums.org/showthread.php?t=2264110](http://ubuntuforums.org/showthread.php?t=2264110)
Post #3 [COLOR=#ff0000]_**But Read it very carefully**_[/COLOR]
As it Warns Make sure you have Back-ups!
Best Regards

---

### Post by Ahmad_Ahmadi on 2015-05-09
I already have seen that post, but I thought there should be a better (safer) solution.

Should I wait for better solutions or I just have to follow that post?

---

### Post by QDR06VV9 on 2015-05-09
> **Ahmad_Ahmadi said:**
> I already have seen that post, but I thought there should be a better (safer) solution.

Should I wait for better solutions or I just have to follow that post?
You could wait for more posters, But it has been over 24 hrs now and over 200 views.
There was multiple posts on that very subject(In My Search's), So ether reinstall or follow that link.(Rarely do I suggest reinstalling OS's) 
But the time spent trying to figure a solution versus a Reinstall can be enormous not to mention exhausting! ](*,)
Wish I had better news for you.;)

---

### Post by deadflowr on 2015-05-09
I think the dpkg command given earlier will only give you the output for all the properly installed linux packages.
I think you might want to look at all the linux packages installed or otherwise.
try a similar command but change the /ii/ part like so:
```
dpkg -l linux* | awk '{print $1,$2}'
```
this should show the current state of all the linux packages, be it fully installed or not.

also, do you know which kernel is currently in use?
```
uname -a
```
can help with that.

Of course, not as if any of this will be helpful, but it might...

---

### Post by alex375 on 2015-05-09
try 'mark for reinstall' in Synaptic Package Manager

---

### Post by Ahmad_Ahmadi on 2015-05-09
I think this problem was because of *wrong usage or problems with Boot-Repair tool*.I did everything with package manager, but nothing has changed.

**My solution:**
Finally I read errors and* I created several files which was noticed in errors (those which was not found)*, and reinstalled *linux-image-extra-3.13.0-45-generic* followed by *sudo apt-get install -f* .

Thanks for you helps :)

---

