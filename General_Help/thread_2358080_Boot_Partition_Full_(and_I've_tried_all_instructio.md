---
title: "Boot Partition Full (and I've tried all instruction I've found in other threads)"
date: 2017-04-09
forum: General Help
---

### Post by ussmith on 2017-04-09
I seem to be stuck in a loop.  I went through the steps to remove old kernels, but they won't die.

I've run

   ```
 uname -r 
sudo dpkg --list 'linux-image*'
sudo apt-get remove -f linux-image-4.4.0-21-generic linux-image-4.4.0-57-generic  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic 
```


But I get 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-21-generic : Depends: linux-image-4.4.0-21-generic but it is not going to be installed
 linux-image-extra-4.4.0-57-generic : Depends: linux-image-4.4.0-57-generic but it is not going to be installed
 linux-image-extra-4.4.0-59-generic : Depends: linux-image-4.4.0-59-generic but it is not going to be installed
 linux-image-extra-4.4.0-62-generic : Depends: linux-image-4.4.0-62-generic but it is not going to be installed
 linux-image-extra-4.4.0-63-generic : Depends: linux-image-4.4.0-63-generic but it is not going to be installed
 linux-image-extra-4.4.0-64-generic : Depends: linux-image-4.4.0-64-generic but it is not going to be installed
 linux-image-extra-4.4.0-72-generic : Depends: linux-image-4.4.0-72-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-72-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

If I follow the suggestions I get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-72-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-72-generic
0 upgraded, 1 newly installed, 0 to remove and 134 not upgraded.
8 not fully installed or removed.
Need to get 0 B/21.8 MB of archives.
After this operation, 66.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 470450 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-72-generic_4.4.0-72.93_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-72-generic (4.4.0-72.93) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-72-generic_4.4.0-72.93_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-72-generic' to '/boot/System.map-4.4.0-72-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-72-generic_4.4.0-72.93_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


So I need to clear space in my boot partition to do the install but can't clear space in my boot partition until I do the install?

Any help will be greatly appreciated.

---

### Post by SeijiSensei on 2017-04-09
Start with the oldest image and remove the "extra" package as well.
```
sudo apt-get remove linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
```
If that works, move onto the next one.

---

### Post by ussmith on 2017-04-09
Same problem

 sudo apt-get remove linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-72-generic : Depends: linux-image-4.4.0-72-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-72-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by KenUBF on 2017-04-09
There is a script I run called purge-old-kernels. It removes all but the two most recent kernels by default unless you tell it to leave more. Here are instructions on how to install it. It seems like the quickest method I've found. [http://blog.dustinkirkland.com/2016/06/purge-old-kernels.html](http://blog.dustinkirkland.com/2016/06/purge-old-kernels.html)

---

### Post by SeijiSensei on 2017-04-09
See [https://ubuntuforums.org/showthread.php?t=2357793&p=13630042&viewfull=1#post13630042](https://ubuntuforums.org/showthread.php?t=2357793&p=13630042&viewfull=1#post13630042) and following.

---

### Post by ussmith on 2017-04-10
Thanks, I've used that before too, but I'm unable to install anything without resolving the problem described above.  I tried to throw that on and got the same error.

---

### Post by Impavidus on 2017-04-10
Can you use a deeper level command?```
sudo dpkg -P linux-image-extra-4.4.0-21-generic
```If it works, repeat for the later versions.

---

### Post by ussmith on 2017-04-16
Sorry for the late response.  Doing a simple rm in the /boot partition cleared enough space to let the apt-get remove of and the apt-get install -f to complete.

---

