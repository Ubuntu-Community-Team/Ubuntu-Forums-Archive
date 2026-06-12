---
title: "Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img"
date: 2013-01-21
forum: General Help
---

### Post by The Element on 2013-01-21
Running sudo apt-get dist-upgrade returns the following errors:

```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-3.5.0-22-generic.postinst line 614.
dpkg: error processing linux-image-3.5.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-22-generic:
 linux-image-extra-3.5.0-22-generic depends on linux-image-3.5.0-22-generic; however:
  Package linux-image-3.5.0-22-generic is not configured yet.

dpkg: error processing linux-image-extra-3.5.0-22-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-3.5.0-22-generic
 linux-image-extra-3.5.0-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

They also appear when I do any updates or installations.

---

### Post by The Element on 2013-01-27
Still having the issue, anyone have any ideas?

---

### Post by oldfred on 2013-01-27
Have you tried update first?

       sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by The Element on 2013-01-28
Yep, I tried the update. Sadly no luck. :-?

Here are the results from running each command you suggested in order (sans the update list for clarity).

```
Fetched 5,150 B in 38s (134 B/s)
Reading package lists... Done
element@Lanthinum:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6:i386 libc6-dev libc6-i386
  multiarch-support
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 16.8 MB of archives.
After this operation, 1,024 B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main libc-bin amd64 2.15-0ubuntu20.1 [1,181 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main libc6-i386 amd64 2.15-0ubuntu20.1 [4,000 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main libc-dev-bin amd64 2.15-0ubuntu20.1 [82.9 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main libc6-dev amd64 2.15-0ubuntu20.1 [2,944 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main libc6 i386 2.15-0ubuntu20.1 [3,942 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main libc6 amd64 2.15-0ubuntu20.1 [4,656 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main multiarch-support amd64 2.15-0ubuntu20.1 [4,478 B]
Fetched 16.8 MB in 4min 25s (63.4 kB/s)                                        
Preconfiguring packages ...
(Reading database ... 417129 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu20 (using .../libc-bin_2.15-0ubuntu20.1_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for lintian ...
Processing triggers for man-db ...
Setting up libc-bin (2.15-0ubuntu20.1) ...
(Reading database ... 417129 files and directories currently installed.)
Preparing to replace libc6-i386 2.15-0ubuntu20 (using .../libc6-i386_2.15-0ubuntu20.1_amd64.deb) ...
Unpacking replacement libc6-i386 ...
Replaced by files in installed package libc6:i386 ...
Preparing to replace libc-dev-bin 2.15-0ubuntu20 (using .../libc-dev-bin_2.15-0ubuntu20.1_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev:amd64 2.15-0ubuntu20 (using .../libc6-dev_2.15-0ubuntu20.1_amd64.deb) ...
Unpacking replacement libc6-dev:amd64 ...
Preparing to replace libc6:amd64 2.15-0ubuntu20 (using .../libc6_2.15-0ubuntu20.1_amd64.deb) ...
De-configuring libc6:i386 ...
Unpacking replacement libc6:amd64 ...
Preparing to replace libc6:i386 2.15-0ubuntu20 (using .../libc6_2.15-0ubuntu20.1_i386.deb) ...
Unpacking replacement libc6:i386 ...
Processing triggers for man-db ...
Setting up libc6:amd64 (2.15-0ubuntu20.1) ...
Setting up libc6:i386 (2.15-0ubuntu20.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 417128 files and directories currently installed.)
Preparing to replace multiarch-support 2.15-0ubuntu20 (using .../multiarch-support_2.15-0ubuntu20.1_amd64.deb) ...
Unpacking replacement multiarch-support ...
Setting up multiarch-support (2.15-0ubuntu20.1) ...
Setting up linux-image-extra-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-extra-3.5.0-22-generic.postinst line 614.
dpkg: error processing linux-image-extra-3.5.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Setting up libc6-i386 (2.15-0ubuntu20.1) ...
Setting up libc-dev-bin (2.15-0ubuntu20.1) ...
Setting up libc6-dev:amd64 (2.15-0ubuntu20.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-extra-3.5.0-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
element@Lanthinum:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-extra-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-extra-3.5.0-22-generic.postinst line 614.
dpkg: error processing linux-image-extra-3.5.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.5.0-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
element@Lanthinum:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-extra-3.5.0-22-generic.postinst line 614.
dpkg: error processing linux-image-extra-3.5.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-extra-3.5.0-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
element@Lanthinum:~$ sudo dpkg --configure -a
Setting up linux-image-extra-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-extra-3.5.0-22-generic.postinst line 614.
dpkg: error processing linux-image-extra-3.5.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-extra-3.5.0-22-generic
element@Lanthinum:~$ 


```

---

### Post by steeldriver on 2013-01-28
It looks like a particular problem with that postinstall script - I'm guessing a bit here but it might be worth doing an apt-get clean to remove the cached debs and then reinstalling the kernel metapackage?

```
sudo apt-get clean

sudo apt-get install --reinstall linux-image-generic
```Hopefully this will download a 'clean' version of the postinst script (although I'm not sure about that)

It might also be worth doing

```
 ls -l /initrd.img
```to see if there's anything funny that might be preventing the symlink

---

### Post by The Element on 2013-01-28
Tried the clean and reinstall, got this:

```
element@Lanthinum:~$ sudo apt-get clean
[sudo] password for element: 
element@Lanthinum:~$ sudo apt-get clean
element@Lanthinum:~$ clear
element@Lanthinum:~$ sudo apt-get clean
element@Lanthinum:~$ sudo apt-get install --reinstall linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2,524 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal-proposed/main linux-image-generic amd64 3.5.0.23.29 [2,524 B]
Fetched 2,524 B in 0s (6,270 B/s)                
(Reading database ... 417128 files and directories currently installed.)
Preparing to replace linux-image-generic 3.5.0.23.29 (using .../linux-image-generic_3.5.0.23.29_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Setting up linux-image-extra-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-extra-3.5.0-22-generic.postinst line 614.
dpkg: error processing linux-image-extra-3.5.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Setting up linux-image-generic (3.5.0.23.29) ...
Errors were encountered while processing:
 linux-image-extra-3.5.0-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
element@Lanthinum:~$ 

```

 ls -l /initrd.img returned:

```
element@Lanthinum:~$  ls -l /initrd.img
lrwxrwxrwx 1 root root 33 Jan 26 10:34 /initrd.img -> /boot/initrd.img-3.5.0-23-generic
element@Lanthinum:~$
```

---

### Post by The Element on 2013-01-28
I decided to try something simple, _**sudo mv /initrd.img initrd.img.bak**_

```
element@Lanthinum:~$ sudo mv /initrd.img initrd.img.bak
element@Lanthinum:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
Not updating image symbolic links since we are being updated/reinstalled 
(3.5.0-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-23-generic...
P: Writing config for /boot/vmlinuz-3.5.0-22-generic...
P: Writing config for /boot/vmlinuz-3.5.0-21-generic...
  No volume groups found
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.5.0-22-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
  No volume groups found
Found Ubuntu 12.10 (12.10) on /dev/sda6
done
element@Lanthinum:~$ 

```

I do believe that looks right, running _**sudo apt-get install -f**_ again returns:

```
element@Lanthinum:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
element@Lanthinum:~$ 
```

Does this look right?

---

### Post by steeldriver on 2013-01-28
Well I'm over my head here but it looks like you have a mismatch between the main kernel package and the linux-image-extra package...?

```
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ [COLOR=Red]**quantal-proposed**[/COLOR]/main linux-image-generic amd64 [COLOR=Red]**3.5.0.23.29**[/COLOR] [2,524 B]
Fetched 2,524 B in 0s (6,270 B/s)                
(Reading database ... 417128 files and directories currently installed.)
Preparing to replace **linux-image-generic [COLOR=Red]3.5.0.23.29[/COLOR]** (using .../linux-image-generic_3.5.0.23.29_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Setting up **linux-image-extra-[COLOR=Red]3.5.0-22[/COLOR]-generic ([COLOR=Red]3.5.0-22.34[/COLOR])** ...
Running depmod.
Failed to symbolic-link /boot/initrd.img-3.5.0-22-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-extra-3.5.0-22-generic.postinst line 614.
dpkg: error processing linux-image-extra-3.5.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Setting up **linux-image-generic ([COLOR=Red]3.5.0.23.29[/COLOR])** ...
Errors were encountered while processing:
 **linux-image-extra-[COLOR=Red]3.5.0-22[/COLOR]-generic**
E: Sub-process /usr/bin/dpkg returned an error code (1)
element@Lanthinum:~$
```

---

### Post by The Element on 2013-01-28
Yeah I just restarted and it seems to be working perfectly now.

So the solution for the error [COLOR="Red"]**Failed to symbolic-link /boot/initrd.img-***-*** to initrd.img:File exists at *****[/COLOR] [COLOR="red"](error exit status 17?)[/COLOR]

is

[B][U][COLOR="DarkGreen"]sudo mv /initrd.img initrd.img.bak

sudo apt-get -f

sudo dpkg --configure -a

sudo apt-get update[/COLOR][/U][/B]

after that I was prompted to restart, and everything seems to work fine!:)

---

