---
title: "I can no longer update or install anything"
date: 2014-09-08
forum: General Help
---

### Post by qwrules on 2014-09-08
14.04 LTS. I was running apt-get dist-upgrade, when the system froze and I had to do hard-reboot. After that, I can no longer update or install anything, because:
```
$ sudo apt-get -f install
[sudo] password for cc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  firefox-locale-pl libjavascriptcoregtk-1.0-0 libmkv0 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-3.13.0-33
  linux-headers-3.13.0-33-generic linux-image-3.13.0-32-generic
  linux-image-3.13.0-33-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-33-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic
The following packages will be upgraded:
  linux-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,784 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 346573 files and directories currently installed.)
Preparing to unpack .../linux-generic_3.13.0.35.42_amd64.deb ...
Unpacking linux-generic (3.13.0.35.42) over (3.13.0.34.40) ...
[COLOR=#ff0000]dpkg: error processing archive /var/cache/apt/archives/linux-generic_3.13.0.35.42_amd64.deb (--unpack):
 unable to make backup symlink for `./usr/share/doc/linux-generic/changelog.gz': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/linux-generic_3.13.0.35.42_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```

I also tried apt-get clean and dpkg --configure -a, but with no result.

---

### Post by Bashing-om on 2014-09-08
qwrules; Hello;

Don't rightly know what is not going on here. But I am willing to try and blunder through this, and perhaps between all of us we can figure this out.

Let's see what is: From the hint "unable to make backup symlink for `./usr/share/doc/linux-generic/changelog.gz': No such file or directory":
What do we presently have in place ?
Post back the results:
```

ls -al /usr/share/doc/linux-generic
ls -al /usr/share/doc/linux-image-generic

```
What kernel are you presently running ?
```

uname -r

```
What kernels are presently installed and their status:
```

dpkg -l | grep linux-

```
And what is in the /boot directory ?
```

ls -al /boot
ls -al /usr/src

```

Once we know what is, and that we are on safe solid ground, we can poke at the 3.13.0.35.42 kernel and see what it will take to get it installed.

[INDENT][INDENT]I am all for a learning experience
[/INDENT][/INDENT]
[/code]

---

### Post by qwrules on 2014-09-08
Thank you for your interest!

```
$ ls -al /usr/share/doc/linux-generic
total 4
drwxr-xr-x 1 root root    42 Sep  8 18:55 .
drwxr-xr-x 1 root root 59764 Sep  8 17:45 ..
lrwxrwxrwx 1 root root     0 Aug 18 22:43 changelog.gz -> 
-rw-r--r-- 1 root root     0 Apr 29 16:25 copyright


$ ls -al /usr/share/doc/linux-image-generic
total 8
drwxr-xr-x 1 root root    42 Sep  8 17:44 .
drwxr-xr-x 1 root root 59764 Sep  8 17:45 ..
-rw-r--r-- 1 root root   512 Aug 18 22:43 changelog.gz
-rw-r--r-- 1 root root  1598 Apr 29 16:25 copyright
```

```
$ uname -r
3.13.0-35-generic


$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.5                                             all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.34.40                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
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
ii  linux-headers-generic                                 3.13.0.35.42                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-30-generic                         3.13.0-30.55                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-33-generic                         3.13.0-33.58                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                   3.13.0-30.55                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic                   3.13.0-33.58                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.35.42                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-35.62                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
```


```
$ ls -al /boot
total 62464
drwxr-xr-x 5 root root     3072 Sep  8 18:04 .
drwxr-xr-x 1 root root      246 Sep  8 17:42 ..
-rw-r--r-- 1 root root  1162712 Aug 13 18:45 abi-3.13.0-34-generic
-rw-r--r-- 1 root root  1163858 Aug 15 04:56 abi-3.13.0-35-generic
-rw-r--r-- 1 root root   165611 Aug 13 18:45 config-3.13.0-34-generic
-rw-r--r-- 1 root root   165652 Aug 15 04:56 config-3.13.0-35-generic
drwxr-xr-x 5 root root     1024 Sep  8 17:42 grub
-rw-r--r-- 1 root root 29393879 Aug 26 13:38 initrd.img-3.13.0-34-generic
-rw-r--r-- 1 root root 12720071 Sep  8 17:43 initrd.img-3.13.0-35-generic
drwx------ 2 root root    12288 Jul  1 22:56 lost+found
-rw-r--r-- 1 root root   176500 Mar 12 13:31 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12 13:31 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12 13:31 memtest86+_multiboot.bin
-rw------- 1 root root  3381262 Aug 13 18:45 System.map-3.13.0-34-generic
-rw------- 1 root root  3386444 Aug 15 04:56 System.map-3.13.0-35-generic
drwx------ 4 root root     1024 Sep  8 18:02 .Trash-0
-rw------- 1 root root  5797728 Aug 13 18:45 vmlinuz-3.13.0-34-generic
-rw------- 1 root root  5806368 Aug 15 04:56 vmlinuz-3.13.0-35-generic
```
I manually deleted all but 2 latest kernels from this folder, because I started getting warnings that my boot partition has only 700kb of free space left.


```
$ ls -al /usr/src
total 0
drwxr-xr-x 1 root root 648 Sep  8 17:45 .
drwxr-xr-x 1 root root  84 Jul  2 07:43 ..
drwxr-xr-x 1 root root 278 Jul  1 23:27 linux-headers-3.13.0-24
drwxr-xr-x 1 root root 406 Jul  1 23:27 linux-headers-3.13.0-24-generic
drwxr-xr-x 1 root root 278 Jul 13 16:47 linux-headers-3.13.0-30
drwxr-xr-x 1 root root 406 Jul 13 16:48 linux-headers-3.13.0-30-generic
drwxr-xr-x 1 root root 278 Jul 24 08:18 linux-headers-3.13.0-32
drwxr-xr-x 1 root root 406 Jul 24 08:18 linux-headers-3.13.0-32-generic
drwxr-xr-x 1 root root 278 Aug 13 11:56 linux-headers-3.13.0-33
drwxr-xr-x 1 root root 406 Aug 13 11:57 linux-headers-3.13.0-33-generic
drwxr-xr-x 1 root root 278 Aug 26 13:31 linux-headers-3.13.0-34
drwxr-xr-x 1 root root 406 Aug 26 13:32 linux-headers-3.13.0-34-generic
drwxr-xr-x 1 root root 278 Sep  8 17:45 linux-headers-3.13.0-35
drwxr-xr-x 1 root root 406 Sep  8 17:45 linux-headers-3.13.0-35-generic
```


Also, due to the error message, I thought it worthwhile to include this output:
```
$ sudo apt-get -f install linux-image-extra-3.13.0-34-generic
[sudo] password for cc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-extra-3.13.0-34-generic is already the newest version.
linux-image-extra-3.13.0-34-generic set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.13.0.34.40) but 3.13.0.35.42 is to be installed
                 Depends: linux-headers-generic (= 3.13.0.34.40) but 3.13.0.35.42 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by grahammechanical on 2014-09-08
You are part the way through installing linux-generic_3.13.0.35.42_amd64.deb
 
Try installing linux-image-generic 3.13.0.35.42 instead of 3.13.0-34 which is already installed. Otherwise, try to un-install it.

Regards.

---

### Post by qwrules on 2014-09-08
I can't because I don't know what are the package names for them. Besides, even if it is "linux-image-generic", I can't do it because I get the same error as in the last output above.

---

### Post by Bashing-om on 2014-09-08
Graham;

That symlink for "/usr/share/doc/linux-generic/changelog.gz" is broken.
It should be:
> 
lrwxrwxrwx   1 root root    35 Aug 18 15:43 changelog.gz -> ../linux-image-generic/changelog.gz

From the syntax, I am not confident of how how to restore it .. any ideas in this respect ?

@ qwrules; Removing things manually behind the package manager's back is not a good thing to do. Will see what we can do to repair the damage and get those old kernels removed using the tools within the package manager.
As Graham advises I bet we have to (re-)install before we can properly remove them .. 

[INDENT][INDENT]when we practice to deceive
[/INDENT][/INDENT]

---

### Post by qwrules on 2014-09-08
I will just add that I removed those kernels manually AFTER the problem started.

How do I install a kernel if it was installed as incremental instances of linux-image-generic? What package name should I use for apt-get?

---

### Post by Bashing-om on 2014-09-08
qwrules; Well;;

I have in mind to fix that symlink and as you are booting the latest kernel and get all it's dependencies satisfied.
Then look about at removing the older kernels.
I would rather it were the voice of experience that spoke in re-establishing that symlink, rather than my own.
I think that is the place to start in unraveling this situation.
No voice speaking up, will endeavor to make up the syntax to make that symbolic link  (symlink) to point to the correct file.

Let's cross the bridge of kernelization when we come to it.

[INDENT][INDENT][INDENT]just my thoughts
[/INDENT][/INDENT][/INDENT]

---

### Post by qwrules on 2014-09-08
Ok. So how do I go about fixing that symlink?

---

### Post by Bashing-om on 2014-09-08
qwrules; Well.

Wont hurt a thing to try:
```

sudo ln -s /usr/share/doc/linux-image-generic/changelog.gz /usr/share/doc/linux-generic/changelog.gz

```
Now let's see the result that I hope and kinda expect to be correct:
```

ls -al /usr/share/doc/linux-generic

```

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by qwrules on 2014-09-08
I though it worked because
```
$ ls -al /usr/share/doc/linux-generic
total 8
drwxr-xr-x 1 root root    42 Sep  8 23:56 .
drwxr-xr-x 1 root root 59764 Sep  8 17:45 ..
lrwxrwxrwx 1 root root    35 Aug 18 22:43 changelog.gz -> ../linux-image-generic/changelog.gz
-rw-r--r-- 1 root root  1598 Apr 29 16:25 copyright


```

alas no:
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  firefox-locale-pl libjavascriptcoregtk-1.0-0 libmkv0 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-3.13.0-33
  linux-headers-3.13.0-33-generic linux-image-3.13.0-32-generic
  linux-image-3.13.0-33-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-33-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic
The following packages will be upgraded:
  linux-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,784 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 346573 files and directories currently installed.)
Preparing to unpack .../linux-generic_3.13.0.35.42_amd64.deb ...
Unpacking linux-generic (3.13.0.35.42) over (3.13.0.34.40) ...
Setting up linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-35-generic
) points to /boot/initrd.img-3.13.0-35-generic
 (/boot/initrd.img-3.13.0-35-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-35-generic
) points to /boot/vmlinuz-3.13.0-35-generic
 (/boot/vmlinuz-3.13.0-35-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-35-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postinst line 1025.
dpkg: error processing package linux-image-extra-3.13.0-35-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-35-generic; however:
  Package linux-image-extra-3.13.0-35-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.35.42); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Still, I think it's a progress.

---

### Post by Bashing-om on 2014-09-08
qwrules; yepper;

that did indeed turn out well ( sometimes I even surprise myself !)

OK, now we are back to that point that you were already aware of:
> 
gzip: stdout: [color=red]No space left on device[/color]
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-35-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1


UnGood! as there is but the 2 kernels residing there, but let's check and make sure of what we are looking at:
```

df -h
df -i
sudo du -h --max-depth=1 /boot

```

I already have a suspicion of what might be at the root of  this . Holding off my opinion 'till we know for sure.

[INDENT][INDENT]one small step at a time
[/INDENT][/INDENT]

---

### Post by qwrules on 2014-09-08
I posted too hastily. How I solved the problem:
1 - create the link (thanks  Bashing-om)
2 - apt-get purge all the unneeded kernels
3 - /boot partition still stuffed, so remove the /boot/.Trash
4 - apt-get -f install

Thanks!

---

### Post by Bashing-om on 2014-09-08
qwrules; Outstanding !

BUT, still want to verify that you are not also a victim of a known bug.
Let's do check:
```

df -h
df -i
sudo du -h --max-depth=1 /boot

```

just so we know.

[INDENT][INDENT][INDENT]knowledge is power
[/INDENT][/INDENT][/INDENT]

---

### Post by qwrules on 2014-09-09
```
$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  295G   73G  221G  25% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.7G  4.0K  1.7G   1% /dev
tmpfs                        334M  1.4M  332M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.7G  244M  1.4G  15% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda1                    236M   86M  138M  39% /boot

$ df -i
Filesystem                  Inodes IUsed  IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root      0     0      0     - /
none                        426526     2 426524    1% /sys/fs/cgroup
udev                        422582   531 422051    1% /dev
tmpfs                       426526   596 425930    1% /run
none                        426526     4 426522    1% /run/lock
none                        426526  2820 423706    1% /run/shm
none                        426526    27 426499    1% /run/user
/dev/sda1                    62248   308  61940    1% /boot

$ sudo du -h --max-depth=1 /boot
12K    /boot/lost+found
6.8M    /boot/grub
84M    /boot
```

Everything apart from boot is btrfs, so free space indication with df is not valid, but in this case also irrelevant.

---

### Post by Bashing-om on 2014-09-09
qwrules; Hey.

Great you have a handle on this situation, and you know what is going on.

I still have the suspicion that when you installed the operating system you chose "LVM" in the install process. -> *Bug: /boot created to small:
See: 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
If this pertains also to you, you are encouraged to add you voice and express your pique in the bug report.

[INDENT][INDENT]make things right
[/INDENT][/INDENT]

---

### Post by qwrules on 2014-09-09
Well, I was using default Ubuntu installation with full-disk-encryption, so it was Ubuntu installer's idea to use LVM. I did not want to mess around with the defaults because this installer is very annoying when trying to use non-standard settings, and this is my mum's computer so it's not like it's gonna have rocket science carried out on it.

On my own machine, I am using Arch with much more complex and customised dm-crypt+lvm2+btrfs setup, which works flawless and unlocks automatically if my tiny 64gb Sandisk USB thumb-drive is present (which also works as regular thumbdrive as the unlock key is dd'ed outside of the partitions).

---

### Post by Bashing-om on 2014-09-09
qwrules; Yepper;

That is the bug. Quite frankly, I do not know of a way around this as the machine is not in your direct care to keep an eye on the /boot partition.
Encryption is not within my sphere of knowledge.
The solution is of course, to make the /boot partition larger !

[INDENT][INDENT]some things I just do not want to know
[/INDENT][/INDENT]

---

