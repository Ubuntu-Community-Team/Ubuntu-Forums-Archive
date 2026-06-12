---
title: "/boot is 100% full, unable to remove any kernel images"
date: 2013-12-25
forum: General Help
---

### Post by hokie79 on 2013-12-25
I have Ubuntu 12.04 with a boot partition.  I had a friend set it up as I am a total novice at this.  After routine package updates over the past 6 six months, they fail now.  I read through the forum and realize I need to delete old kernel images that have been accumulating over the past several months.  However, I have tried several commands from solutions posted in other threads in the terminal to remove them and they all fail (purge, remove, autoremove).  I also tried to install UBUNTU Tweak and the install failed.  I could use some detailed help to remove these packages so I can continue the package updates.

---

### Post by ian-weisser on 2013-12-25
Show us the exact sequence of commands you are using to remove the old kernels,
and please show us the entire session that ends in a failure or error message.

---

### Post by sisco311 on 2013-12-25
Also please post the content of the /boot directory:```
ls -alh /boot
``` Hopefully there are some backup files which you can remove manually to free up some space.

---

### Post by hokie79 on 2013-12-25
```
bartholic@home-cam:~$ ls -alh /boot
total 220M
drwxr-xr-x  4 root root 2.0K Dec 22 10:44 .
drwxr-xr-x 23 root root 4.0K Nov  8 12:03 ..
-rw-r--r--  1 root root 829K Jan 25  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root 833K Jun  7  2013 abi-3.5.0-34-generic
-rw-r--r--  1 root root 833K Jun 20  2013 abi-3.5.0-36-generic
-rw-r--r--  1 root root 833K Jul 10 14:09 abi-3.5.0-37-generic
-rw-r--r--  1 root root 834K Aug 14 12:03 abi-3.5.0-39-generic
-rw-r--r--  1 root root 834K Aug 23 13:59 abi-3.5.0-40-generic
-rw-r--r--  1 root root 834K Sep 12 13:11 abi-3.5.0-41-generic
-rw-r--r--  1 root root 834K Oct  2 17:19 abi-3.5.0-42-generic
-rw-r--r--  1 root root 834K Oct 24 11:16 abi-3.5.0-43-generic
-rw-r--r--  1 root root 145K Jan 25  2013 config-3.5.0-23-generic
-rw-r--r--  1 root root 145K Jun  7  2013 config-3.5.0-34-generic
-rw-r--r--  1 root root 145K Jun 20  2013 config-3.5.0-36-generic
-rw-r--r--  1 root root 145K Jul 10 14:09 config-3.5.0-37-generic
-rw-r--r--  1 root root 145K Aug 14 12:03 config-3.5.0-39-generic
-rw-r--r--  1 root root 145K Aug 23 13:59 config-3.5.0-40-generic
-rw-r--r--  1 root root 145K Sep 12 13:11 config-3.5.0-41-generic
-rw-r--r--  1 root root 145K Oct  2 17:19 config-3.5.0-42-generic
-rw-r--r--  1 root root 145K Oct 24 11:16 config-3.5.0-43-generic
drwxr-xr-x  3 root root 5.0K Dec 22 10:41 grub
-rw-r--r--  1 root root  16M Jul  3 16:16 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root  16M Jul  3 16:29 initrd.img-3.5.0-34-generic
-rw-r--r--  1 root root  16M Jul  7 09:08 initrd.img-3.5.0-36-generic
-rw-r--r--  1 root root  16M Aug 25 07:37 initrd.img-3.5.0-37-generic
-rw-r--r--  1 root root  16M Sep  7 17:41 initrd.img-3.5.0-39-generic
-rw-r--r--  1 root root  16M Sep 13 14:40 initrd.img-3.5.0-40-generic
-rw-r--r--  1 root root  16M Sep 29 19:31 initrd.img-3.5.0-41-generic
-rw-r--r--  1 root root  16M Oct 26 12:51 initrd.img-3.5.0-42-generic
-rw-r--r--  1 root root  16M Nov  8 12:03 initrd.img-3.5.0-43-generic
drwxr-xr-x  2 root root  12K Jun 13  2013 lost+found
-rw-r--r--  1 root root 173K Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root 175K Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root 2.9M Jan 25  2013 System.map-3.5.0-23-generic
-rw-------  1 root root 2.9M Jun  7  2013 System.map-3.5.0-34-generic
-rw-------  1 root root 2.9M Jun 20  2013 System.map-3.5.0-36-generic
-rw-------  1 root root 2.9M Jul 10 14:09 System.map-3.5.0-37-generic
-rw-------  1 root root 2.9M Aug 14 12:03 System.map-3.5.0-39-generic
-rw-------  1 root root 2.9M Aug 23 13:59 System.map-3.5.0-40-generic
-rw-------  1 root root 2.9M Sep 12 13:11 System.map-3.5.0-41-generic
-rw-------  1 root root 2.9M Oct  2 17:19 System.map-3.5.0-42-generic
-rw-------  1 root root 2.9M Oct 24 11:16 System.map-3.5.0-43-generic
-rw-------  1 root root 5.0M Jan 25  2013 vmlinuz-3.5.0-23-generic
-rw-------  1 root root 5.0M Jun  7  2013 vmlinuz-3.5.0-34-generic
-rw-------  1 root root 5.0M Jun 20  2013 vmlinuz-3.5.0-36-generic
-rw-------  1 root root 5.0M Jul 10 14:09 vmlinuz-3.5.0-37-generic
-rw-------  1 root root 5.0M Aug 14 12:03 vmlinuz-3.5.0-39-generic
-rw-------  1 root root 5.0M Aug 23 13:59 vmlinuz-3.5.0-40-generic
-rw-------  1 root root 5.0M Sep 12 13:11 vmlinuz-3.5.0-41-generic
-rw-------  1 root root 5.0M Oct  2 17:19 vmlinuz-3.5.0-42-generic
-rw-------  1 root root 5.0M Oct 24 11:16 vmlinuz-3.5.0-43-generic
bartholic@home-cam:~$
```

---

### Post by hokie79 on 2013-12-25
bartholic@home-cam:~$ sudo apt-get purge linux-image-3.5.0-36-generic
[sudo] password for bartholic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-quantal : Depends: linux-image-3.5.0-44-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by hokie79 on 2013-12-25
all remove commands are not removing anything...!

bartholic@home-cam:~$ sudo apt-get autoremove linux-image-3.5.0-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-quantal : Depends: linux-image-3.5.0-44-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by egeezer on 2013-12-25
I have done the following to remove old kernels.  Some people say it is not a good idea because it “Screws up the packager”, but it has never failed me yet.  In your case, the instruction would be:

```
sudo rm *3.5.0-3[4,5,6,7,9]*
```

Then your password, then:

```
sudo update-grub
```

It will start working, then return and show you what's left, i.e. the 4 kernels from -40 to -43

To repeat, this method has never failed me.  YMMV

---

### Post by Iowan on 2013-12-25
There is another method [here]("http://ubuntuforums.org/showthread.php?t=2191894&page=4&p=12866952#post12866952")...

---

### Post by ian-weisser on 2013-12-25
> You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 [COLOR=#ff0000]linux-image-generic-lts-quantal : Depends: linux-image-3.5.0-44-generic [/COLOR]but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

You may or may not have a full /boot partition, but that's not your biggest problem.
Your biggest problem is the package* linux-image-generic-lts-quantal*. That's the package causing your package manager to choke.

I recommend against egeezer's advice. Use the package manager properly - it's there to help. Don't try to work around it...or you will certainly wind up reinstalling.

Is there a reason you need the backported 12.10 kernel? It's pretty old at this point.

1) Do the command **uname -r** to see the kernel you currently have. Whatever else happens, *don't* remove that kernel...until after you have rebooted into another kernel that works.

2) Disable *all* your PPAs and non-Ubuntu repositories.

3) Try the command **sudo apt-get remove linux-image-generic-lts-quantal** .
If it doesn't work or you get an error message, show us the session.

4) If it works, then you should be able to easily remove all those old  kernels using the package manager (example: sudo apt-get remove  linux-image-3.5.0-23-generic).

5) (Optional) After the old kernels are removed, and the updated kernels are installed (thru -44), then you can reinstall linux-image-generic-lts-quantal

---

### Post by hokie79 on 2013-12-25
ian-wesser...no luck...what should I try next?
bartholic@home-cam:~$  sudo apt-get remove linux-image-generic-lts-quantal
[sudo] password for bartholic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-lts-quantal : Depends: linux-image-generic-lts-quantal but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by hokie79 on 2013-12-25
bartholic@home-cam:~$ uname -r
3.5.0-43-generic

I don't understand how to do instruction #2....

---

### Post by ian-weisser on 2013-12-25
> **hokie79 said:**
> I don't understand how to do instruction #2....

Open Software Center
Open the Edit Menu
Select Software Sources
Uncheck any PPAs or unofficial reposiotries you may have added.

---

### Post by hokie79 on 2013-12-25
ok.  I unchecked to PPAs.  Software catalog cannot repair.  
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 284713 files and directories currently installed.) 
Unpacking linux-image-3.5.0-44-generic (from .../linux-image-3.5.0-44-generic_3.5.0-44.67~precise1_amd64.deb) ... 
Done. 
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-44-generic_3.5.0-44.67~precise1_amd64.deb (--unpack): 
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.5.0-44-generic': No space left on device 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-3.5.0-44-generic_3.5.0-44.67~precise1_amd64.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up initramfs-tools (0.99ubuntu13.4) ... 
update-initramfs: deferring update (trigger activated) 
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal: 
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-44-generic; however: 
  Package linux-image-3.5.0-44-generic is not installed. 
dpkg: error processing linux-image-generic-lts-quantal (--configure): 
 dependency problems - leaving unconfigured 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-3.5.0-43-generic 
 
gzip: stdout: No space left on device 
cpio: write error: Broken pipe 
E: mkinitramfs failure cpio 1 gzip 1 
update-initramfs: failed for /boot/initrd.img-3.5.0-43-generic with 1. 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1

---

### Post by ian-weisser on 2013-12-25
That's expected in step 2. It's telling you the partition is full.
Proceed to step 3. You don't need an updated package index to remove old kernels.

After you have removed the kernels, the system will have room to store the updated package index.

---

### Post by hokie79 on 2013-12-26
ian-weisser

I retried step 3 and here are the results, same as before:
bartholic@home-cam:~$  sudo apt-get remove linux-image-generic-lts-quantal
[sudo] password for bartholic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-lts-quantal : Depends: linux-image-generic-lts-quantal but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by sisco311 on 2013-12-27
What happens when you try to run the command suggested by apt-get?
```
sudo apt-get -f install
```

---

### Post by ian-weisser on 2013-12-27
> **hokie79 said:**
> linux-generic-lts-quantal : Depends: linux-image-generic-lts-quantal but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Let's approach it from a different direction. Try this command (yes, it's one big command). If you get an error, stop and post it here.
```
sudo apt-get autoremove linux-image-3.5.0-23-generic linux-image-3.5.0-34-generic linux-image-3.5.0-36-generic linux-image-3.5.0-37-generic linux-image-3.5.0-39-generic linux-image-3.5.0-40-generic linux-image-3.5.0-41-generic
```

---

### Post by Impavidus on 2013-12-27
Not using the package manager to remove packages can leave the package manager in an inconsistent state, which is why we prefer using the package manager. However, your package manager is already in an inconsistent state because it failed to install the latest kernel update, and therefore you cannot use the package manager to create room for the kernel update. It's really a deadlock: you can't fix the package manager without installing the latest kernel update, you can't install the latest kernel update without first removing some old kernel versions and you can't remove some old kernel version without first fixing the package manager.

There is a way out. You can manually delete some big files from /boot, then fix the package manager and finally bring everything into a consistent state by properly uninstalling some old kernels. Run```
sudo rm /boot/initrd.img-3.5.0-23-generic
sudo rm /boot/initrd.img-3.5.0-34-generic
sudo rm /boot/initrd.img-3.5.0-36-generic
sudo rm /boot/initrd.img-3.5.0-37-generic
```to get some space. Then fix the package manager with```
sudo apt-get -f install
```. This should install the kernel update. Finally, properly uninstall the packages with```
sudo apt-get purge linux-image-3.5.0-23-generic
sudo apt-get purge linux-image-3.5.0-34-generic
sudo apt-get purge linux-image-3.5.0-36-generic
sudo apt-get purge linux-image-3.5.0-37-generic
```(If you wish, you can put it into a small one-liner, but I think this is clearer.)

---

### Post by hokie79 on 2013-12-27
sisco 311  Here is your result:
```

bartholic@home-cam:~$ sudo apt-get -f install
[sudo] password for bartholic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-39-generic linux-headers-3.5.0-39
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.5.0-44-generic
Suggested packages:
  fdutils linux-lts-quantal-doc-3.5.0 linux-lts-quantal-source-3.5.0
  linux-lts-quantal-tools
The following NEW packages will be installed:
  linux-image-3.5.0-44-generic
0 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
2 not fully installed or removed.
Need to get 0 B/40.6 MB of archives.
After this operation, 157 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 284713 files and directories currently installed.)
Unpacking linux-image-3.5.0-44-generic (from .../linux-image-3.5.0-44-generic_3.5.0-44.67~precise1_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-44-generic_3.5.0-44.67~precise1_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.5.0-44-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-44-generic_3.5.0-44.67~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by hokie79 on 2013-12-27
It worked!!!   THANK YOU!!!
```

bartholic@home-cam:~$ sudo rm /boot/initrd.img-3.5.0-23-generic
bartholic@home-cam:~$ sudo rm /boot/initrd.img-3.5.0-34-generic
bartholic@home-cam:~$ sudo rm /boot/initrd.img-3.5.0-36-generic
bartholic@home-cam:~$ sudo rm /boot/initrd.img-3.5.0-37-generic
bartholic@home-cam:~$ sudo apt-get -f install
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-39-generic linux-headers-3.5.0-39
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.5.0-44-generic
Suggested packages:
  fdutils linux-lts-quantal-doc-3.5.0 linux-lts-quantal-source-3.5.0
  linux-lts-quantal-tools
The following NEW packages will be installed:
  linux-image-3.5.0-44-generic
0 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
2 not fully installed or removed.
Need to get 0 B/40.6 MB of archives.
After this operation, 157 MB of additional disk space will be used.
(Reading database ... 284713 files and directories currently installed.)
Unpacking linux-image-3.5.0-44-generic (from .../linux-image-3.5.0-44-generic_3.5.0-44.67~precise1_amd64.deb) ...
Done.
Setting up initramfs-tools (0.99ubuntu13.4) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.5.0-44-generic (3.5.0-44.67~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-44-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-44-generic /boot/vmlinuz-3.5.0-44-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-44-generic
Found initrd image: /boot/initrd.img-3.5.0-44-generic
Found linux image: /boot/vmlinuz-3.5.0-43-generic
Found initrd image: /boot/initrd.img-3.5.0-43-generic
Found linux image: /boot/vmlinuz-3.5.0-42-generic
Found initrd image: /boot/initrd.img-3.5.0-42-generic
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic-lts-quantal (3.5.0.44.50) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-44-generic
bartholic@home-cam:~$ 
bartholic@home-cam:~$ 
bartholic@home-cam:~$ sudo apt-get purge linux-image-3.5.0-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-39-generic linux-headers-3.5.0-39
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.5.0-23-generic*
0 upgraded, 0 newly installed, 1 to remove and 46 not upgraded.
After this operation, 156 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 288954 files and directories currently installed.)
Removing linux-image-3.5.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-44-generic
Found initrd image: /boot/initrd.img-3.5.0-44-generic
Found linux image: /boot/vmlinuz-3.5.0-43-generic
Found initrd image: /boot/initrd.img-3.5.0-43-generic
Found linux image: /boot/vmlinuz-3.5.0-42-generic
Found initrd image: /boot/initrd.img-3.5.0-42-generic
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.5.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
bartholic@home-cam:~$ sudo apt-get purge linux-image-3.5.0-34-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-39-generic linux-headers-3.5.0-39
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.5.0-34-generic*
0 upgraded, 0 newly installed, 1 to remove and 46 not upgraded.
After this operation, 157 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 284723 files and directories currently installed.)
Removing linux-image-3.5.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-44-generic
Found initrd image: /boot/initrd.img-3.5.0-44-generic
Found linux image: /boot/vmlinuz-3.5.0-43-generic
Found initrd image: /boot/initrd.img-3.5.0-43-generic
Found linux image: /boot/vmlinuz-3.5.0-42-generic
Found initrd image: /boot/initrd.img-3.5.0-42-generic
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.5.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
bartholic@home-cam:~$ sudo apt-get purge linux-image-3.5.0-36-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-39-generic linux-headers-3.5.0-39
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-3.5.0-36-generic*
0 upgraded, 0 newly installed, 1 to remove and 46 not upgraded.
After this operation, 157 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 280481 files and directories currently installed.)
Removing linux-image-3.5.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-44-generic
Found initrd image: /boot/initrd.img-3.5.0-44-generic
Found linux image: /boot/vmlinuz-3.5.0-43-generic
Found initrd image: /boot/initrd.img-3.5.0-43-generic
Found linux image: /boot/vmlinuz-3.5.0-42-generic
Found initrd image: /boot/initrd.img-3.5.0-42-generic
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.5.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
```

---

