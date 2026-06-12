---
title: "Too many kernels ?"
date: 2017-09-04
forum: General Help
---

### Post by raleigh3 on 2017-09-04
I read where autoremove is supposed to remove all but 2 kernels.

After running it, I still have 4 kernels.

  
I tried to get a file listing but...

  ```

andy@7:/boot$ sudo ls > boot_dir_contents.txt
bash: boot_dir_contents.txt: Permission denied
```

Why is that ?

  ```

-rw-r--r-- 1 root 38054281 08-28-2017 initrd.img-4.4.0-93-generic
-rw-r--r-- 1 root 38048571 08-15-2017 initrd.img-4.4.0-92-generic
-rw-r--r-- 1 root  1247269 08-11-2017 abi-4.4.0-93-generic
-rw-r--r-- 1 root   190356 08-11-2017 config-4.4.0-93-generic
-rw------- 1 root  3885811 08-11-2017 System.map-4.4.0-93-generic
-rw------- 1 root  7097296 08-11-2017 vmlinuz-4.4.0-93-generic
-rw-r--r-- 1 root  1246835 08-10-2017 abi-4.4.0-92-generic
-rw-r--r-- 1 root   190356 08-10-2017 config-4.4.0-92-generic
-rw------- 1 root  3884798 08-10-2017 System.map-4.4.0-92-generic
-rw------- 1 root  7098032 08-10-2017 vmlinuz-4.4.0-92-generic
-rw-r--r-- 1 root 38055787 05-20-2017 initrd.img-4.4.0-75-generic
-rw-r--r-- 1 root 38056362 05-20-2017 initrd.img-4.4.0-77-generic
-rw-r--r-- 1 root  1246313 04-26-2017 abi-4.4.0-77-generic
-rw-r--r-- 1 root   190355 04-26-2017 config-4.4.0-77-generic
-rw------- 1 root  3883390 04-26-2017 System.map-4.4.0-77-generic
-rw------- 1 root  7081808 04-26-2017 vmlinuz-4.4.0-77-generic
-rw-r--r-- 1 root  1246246 04-20-2017 abi-4.4.0-75-generic
-rw-r--r-- 1 root   190214 04-20-2017 config-4.4.0-75-generic
-rw------- 1 root  3883390 04-20-2017 System.map-4.4.0-75-generic
-rw------- 1 root  7081872 04-20-2017 vmlinuz-4.4.0-75-generic
drwxr-xr-x 4 root     4096 03-10-2017 grub.bak
-rw-r--r-- 1 root   182704 01-28-2016 memtest86+.bin
-rw-r--r-- 1 root   184380 01-28-2016 memtest86+.elf
-rw-r--r-- 1 root   184840 01-28-2016 memtest86+_multiboot.bin


```

---

### Post by vasa1 on 2017-09-04
Have you run ```
sudo apt-get autoremove
```recently? You can always press "n" if you're uncertain but post the entire output here.

---

### Post by ajgreeny on 2017-09-04
It would also help to be sure exactly what kernels you do really have installed so run command ```
dpkg -l linux-image*
```and post the output back here.

Your first **ls** command shown did not need **sudo** as the output file is then owned by root; you can run that command as user and read the file without a problem.

---

### Post by deadflowr on 2017-09-04
> I tried to get a file listing but...
```
andy@7:/boot$ sudo ls > boot_dir_contents.txt
bash: boot_dir_contents.txt: Permission denied
```
Why is that ?

Do it without sudo and change the location to your home folder with ~/
like so
```
user@machine:/boot$ ls > ~/boot_dir_contents.txt
```
it'll then save in your home folder.
I think that's about the simplest way to do it.
Also since it's owned by you instead of root, you can do whatever you want with it.

---

### Post by raleigh3 on 2017-09-04
> **ajgreeny said:**
> It would also help to be sure exactly what kernels you do really have installed so run command ```
dpkg -l linux-image*
```and post the output back here.

Your first **ls** command shown did not need **sudo** as the output file is then owned by root; you can run that command as user and read the file without a problem.

```
un  linux-image                 <none>             <none>             (no description available)
rc  linux-image-4.4.0-21-generi 4.4.0-21.37        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-78-generi 4.4.0-78.99        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-79-generi 4.4.0-79.100       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-81-generi 4.4.0-81.104       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-83-generi 4.4.0-83.106       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-87-generi 4.4.0-87.110       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-89-generi 4.4.0-89.112       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-91-generi 4.4.0-91.114       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generi 4.4.0-92.115       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-93-generi 4.4.0-93.116       amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21- 4.4.0-21.37        amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-78- 4.4.0-78.99        amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-79- 4.4.0-79.100       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-81- 4.4.0-81.104       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-83- 4.4.0-83.106       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-87- 4.4.0-87.110       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-89- 4.4.0-89.112       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-91- 4.4.0-91.114       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
rc  linux-image-extra-4.4.0-92- 4.4.0-92.115       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
ii  linux-image-extra-4.4.0-93- 4.4.0-93.116       amd64              Linux kernel extra modules for version 4.4.0 on 64 bit x86 
ii  linux-image-generic         4.4.0.93.98        amd64              Generic Linux kernel image


```

---

### Post by raleigh3 on 2017-09-04
> **vasa1 said:**
> Have you run ```
sudo apt-get autoremove
```recently? You can always press "n" if you're uncertain but post the entire output here.

 ```
sudo apt-get autoremove
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.

```

---

### Post by raleigh3 on 2017-09-04
Do it without sudo and change the location to your home folder with ~/
like so
 	Code:
 	user@machine:/boot$ ls > ~/boot_dir_contents.txt

Thanks.

---

### Post by ian-weisser on 2017-09-04
autoremove is not magic and it's not clever. It's actually very simple.
The logic is easy-to-follow and conservative, and deliberately errs on the side keeping kernels.

It can be easily (and unintentionally) defeated many ways: Manual install, apt-pinning, unusual dependencies, changed major version numbers, and more.

Generally, the first step of troubleshooting kernels-not-autoremoving problem is to run autoremove manually.
If nothing autoremoves, then the second step is to figure out how you defeated it.

---

### Post by ajgreeny on 2017-09-04
You appear to have only one kernel installed, 4.4.0-93 which is the current most recent of the 4.4 series, so nothing is removable.

Running ```
sudo apt-get -s autoremove --purge
``` would show you exactly what packages would be removed, including all those kernel configurations, the ones starting with **rc** in your listed output.  It will also show all the unnecessary kernel header packages that can be purged.  The -s option will mean that nothing actually happens, just informtion will be shown in the output.

Once you are happy that nothing that you want to keep is going to be removed you can run that command again removing the -s (simulate) option.

---

### Post by raleigh3 on 2017-09-04
I ran Ukuu and it showed one kernel in use and 2 that were installed.

I deleted the oldest one.

I decided to not remove the other one nor install a newer kernel in order not to break anything. :-)

I saved 50 Mb of disk space.

---

