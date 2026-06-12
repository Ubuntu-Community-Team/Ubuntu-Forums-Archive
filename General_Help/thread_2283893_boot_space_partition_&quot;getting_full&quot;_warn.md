---
title: "/boot space partition &quot;getting full&quot; warning message when installing Kernel updates"
date: 2015-06-25
forum: General Help
---

### Post by Bill Dubinski on 2015-06-25
Good Day, Thanks to all in advance. 

Weird dilemma recently arisen during new kernel updates. 
A dialog box pops up telling me the /boot partition space is getting low. Than after opening the system monitor section in Ubuntu classic mode in 12.04 LTS (Precise), and clicked on the file systems tab to view the /boot partition and sure enough it reads 95% full. 

My /boot partition is currently 1 gb or as it registers in System Monitor 944.6 MiB. 
Previously I was running 10.04 LTS (Lucid) and have always used 1 gb for /boot.

Ironically, on my wifes laptop (also running 12.04 LTS (Precise), in which she was running 12.04 longer than I have since it took me a while to migrate to Precise from Lucid. 
Also using 1 gb for /boot and her disk usage is only 36%.

I was running Lucid for double as long as I have been Precise and I have never ran out of /boot partition space. 
Plus, on my wife's laptop using only 36% of that same size partition, I feel this is all weird. 

What does the community think about this?
What went wrong (if any)?
How do I fix this situation w/o having to upgrade to 14.4 or reload 12.04 to I can relieve more space in the /boot partition?

The current kernel I am running is 3.13.0.55

Thanks all, 
Bill

---

### Post by v3.xx on 2015-06-25
This is a ongoing problem.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=boot+partition+full+launchpad&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=boot+partition+full+launchpad&sa=Search&cof=FORID:9)

Are you sure you have a boot partition and not a boot folder?

---

### Post by coffeecat on 2015-06-25
It's not quite clear whether you made a clean install of 12.04, or upgraded from 10.04, but if you did the latter and have accumulated many old kernels, then it is possible to fill up a 1GB boot partition. Let's see what you have got. Post the output of:

```
ls -l --block-size=M /boot
```

@v3.xx, it you are thinking of the situation where a LVM installation creates an inadequately sized boot partition, this is not it. With LVM the installer creates a boot partition of just under 250MB. The OP says they have a boot partition of 1GB.

---

### Post by TheFu on 2015-06-25
Clean up old kernels.  I keep 3 around, no more, just 3.

A script that will help create the command you want to do the cleanup:
[http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt)

Just to be VERY CLEAR - the script only creates a command - it DOES NOT DO ANYTHING ELSE.  You'll have to copy/paste the command and run it, if any action is desired.  For example:
```
$ ./kernel-cleanup.sh 

INFO: Current kernel is: linux-image-3.13.0-55-generic


INFO: Below is the command to clean up old kernels from APT-based Linux systems.
INFO: Please carefully read and understand the warnings below prior to use.

/usr/bin/sudo /usr/bin/aptitude purge linux-image-3.13.0-52-generic linux-image-3.13.0-53-generic

WARNING: May wish to remove the last 2 kernels from this command to retain
WARNING: backup kernels should something bad happen with the current 
WARNING: kernel like file corruption.

INFO: Current kernel has been removed from the sorted list already.

```

So ... with that example run, I have 3 kernels on this system 52, 53, 55.  I'm happy with 3 kernels, so I will not copy the **sudo** line and run it.
After running this, it is smart to run an autoremove cycle to remove dependencies not needed anymore (mainly kernel headers). Hope this clears things up about the script.

---

### Post by v3.xx on 2015-06-25
@ coffeecat
One of these days I will figure out what I'm doing :)

Thanks

---

### Post by Bill Dubinski on 2015-06-25
Thanks for reply. 
Actually, 10.04 is on a separate 1 TB HDD than the one that 12.04 is on. 
I still use 10.04 on the other HDD as a testing OS if something is not working correctly in 12.04 and that is a storage HDD. 

So on this newer 1TB HDD, this is a fresh install. 

But I will post output of ls -l --block-size=M /boot
```
~$ ls -l --block-size=M /boot
total 838M
-rw-r--r-- 1 root root  2M Jul 14  2014 abi-3.13.0-32-generic
-rw-r--r-- 1 root root  2M Jul 30  2014 abi-3.13.0-33-generic
-rw-r--r-- 1 root root  2M Aug 13  2014 abi-3.13.0-34-generic
-rw-r--r-- 1 root root  2M Aug 18  2014 abi-3.13.0-35-generic
-rw-r--r-- 1 root root  2M Sep  4  2014 abi-3.13.0-36-generic
-rw-r--r-- 1 root root  2M Sep 24  2014 abi-3.13.0-37-generic
-rw-r--r-- 1 root root  2M Oct 29  2014 abi-3.13.0-39-generic
-rw-r--r-- 1 root root  2M Nov 14  2014 abi-3.13.0-40-generic
-rw-r--r-- 1 root root  2M Dec  9  2014 abi-3.13.0-43-generic
-rw-r--r-- 1 root root  2M Jan 15 14:46 abi-3.13.0-45-generic
-rw-r--r-- 1 root root  2M Mar 10 15:50 abi-3.13.0-46-generic
-rw-r--r-- 1 root root  2M Mar 12 14:56 abi-3.13.0-48-generic
-rw-r--r-- 1 root root  2M Mar 25 11:58 abi-3.13.0-49-generic
-rw-r--r-- 1 root root  2M Apr 15 17:10 abi-3.13.0-51-generic
-rw-r--r-- 1 root root  2M May  5 13:33 abi-3.13.0-52-generic
-rw-r--r-- 1 root root  2M May 20 12:59 abi-3.13.0-53-generic
-rw-r--r-- 1 root root  2M May 27 06:15 abi-3.13.0-54-generic
-rw-r--r-- 1 root root  2M Jun 18 05:19 abi-3.13.0-55-generic
-rw-r--r-- 1 root root  1M Aug 14  2013 abi-3.8.0-29-generic
-rw-r--r-- 1 root root  1M Sep 11  2013 abi-3.8.0-31-generic
-rw-r--r-- 1 root root  1M Oct  2  2013 abi-3.8.0-32-generic
-rw-r--r-- 1 root root  1M Oct 24  2013 abi-3.8.0-33-generic
-rw-r--r-- 1 root root  1M Nov 13  2013 abi-3.8.0-34-generic
-rw-r--r-- 1 root root  1M Jan 30  2014 abi-3.8.0-35-generic
-rw-r--r-- 1 root root  1M Feb  3  2014 abi-3.8.0-36-generic
-rw-r--r-- 1 root root  1M Feb 19  2014 abi-3.8.0-37-generic
-rw-r--r-- 1 root root  1M Mar 13  2014 abi-3.8.0-38-generic
-rw-r--r-- 1 root root  1M May  2  2014 abi-3.8.0-39-generic
-rw-r--r-- 1 root root  1M May 15  2014 abi-3.8.0-41-generic
-rw-r--r-- 1 root root  1M Jul  4  2014 abi-3.8.0-42-generic
-rw-r--r-- 1 root root  1M Jul 14  2014 abi-3.8.0-44-generic
-rw-r--r-- 1 root root  1M Jul 14  2014 config-3.13.0-32-generic
-rw-r--r-- 1 root root  1M Jul 30  2014 config-3.13.0-33-generic
-rw-r--r-- 1 root root  1M Aug 13  2014 config-3.13.0-34-generic
-rw-r--r-- 1 root root  1M Aug 18  2014 config-3.13.0-35-generic
-rw-r--r-- 1 root root  1M Sep  4  2014 config-3.13.0-36-generic
-rw-r--r-- 1 root root  1M Sep 24  2014 config-3.13.0-37-generic
-rw-r--r-- 1 root root  1M Oct 29  2014 config-3.13.0-39-generic
-rw-r--r-- 1 root root  1M Nov 14  2014 config-3.13.0-40-generic
-rw-r--r-- 1 root root  1M Dec  9  2014 config-3.13.0-43-generic
-rw-r--r-- 1 root root  1M Jan 15 14:46 config-3.13.0-45-generic
-rw-r--r-- 1 root root  1M Mar 10 15:50 config-3.13.0-46-generic
-rw-r--r-- 1 root root  1M Mar 12 14:56 config-3.13.0-48-generic
-rw-r--r-- 1 root root  1M Mar 25 11:58 config-3.13.0-49-generic
-rw-r--r-- 1 root root  1M Apr 15 17:10 config-3.13.0-51-generic
-rw-r--r-- 1 root root  1M May  5 13:33 config-3.13.0-52-generic
-rw-r--r-- 1 root root  1M May 20 12:59 config-3.13.0-53-generic
-rw-r--r-- 1 root root  1M May 27 06:15 config-3.13.0-54-generic
-rw-r--r-- 1 root root  1M Jun 18 05:19 config-3.13.0-55-generic
-rw-r--r-- 1 root root  1M Aug 14  2013 config-3.8.0-29-generic
-rw-r--r-- 1 root root  1M Sep 11  2013 config-3.8.0-31-generic
-rw-r--r-- 1 root root  1M Oct  2  2013 config-3.8.0-32-generic
-rw-r--r-- 1 root root  1M Oct 24  2013 config-3.8.0-33-generic
-rw-r--r-- 1 root root  1M Nov 13  2013 config-3.8.0-34-generic
-rw-r--r-- 1 root root  1M Jan 30  2014 config-3.8.0-35-generic
-rw-r--r-- 1 root root  1M Feb  3  2014 config-3.8.0-36-generic
-rw-r--r-- 1 root root  1M Feb 19  2014 config-3.8.0-37-generic
-rw-r--r-- 1 root root  1M Mar 13  2014 config-3.8.0-38-generic
-rw-r--r-- 1 root root  1M May  2  2014 config-3.8.0-39-generic
-rw-r--r-- 1 root root  1M May 15  2014 config-3.8.0-41-generic
-rw-r--r-- 1 root root  1M Jul  4  2014 config-3.8.0-42-generic
-rw-r--r-- 1 root root  1M Jul 14  2014 config-3.8.0-44-generic
drwxr-xr-x 3 root root  1M Jun 23 06:36 grub
-rw-r--r-- 1 root root 19M Aug  6  2014 initrd.img-3.13.0-32-generic
-rw-r--r-- 1 root root 19M Aug 12  2014 initrd.img-3.13.0-33-generic
-rw-r--r-- 1 root root 19M Aug 14  2014 initrd.img-3.13.0-34-generic
-rw-r--r-- 1 root root 19M Sep  9  2014 initrd.img-3.13.0-35-generic
-rw-r--r-- 1 root root 19M Sep 24  2014 initrd.img-3.13.0-36-generic
-rw-r--r-- 1 root root 19M Oct  9  2014 initrd.img-3.13.0-37-generic
-rw-r--r-- 1 root root 19M Oct 30  2014 initrd.img-3.13.0-39-generic
-rw-r--r-- 1 root root 19M Dec  5  2014 initrd.img-3.13.0-40-generic
-rw-r--r-- 1 root root 19M Jan  1 16:29 initrd.img-3.13.0-43-generic
-rw-r--r-- 1 root root 19M Feb 13 11:36 initrd.img-3.13.0-45-generic
-rw-r--r-- 1 root root 19M Mar 12 09:08 initrd.img-3.13.0-46-generic
-rw-r--r-- 1 root root 19M Mar 25 10:11 initrd.img-3.13.0-48-generic
-rw-r--r-- 1 root root 19M Apr  9 15:33 initrd.img-3.13.0-49-generic
-rw-r--r-- 1 root root 19M May  2 06:40 initrd.img-3.13.0-51-generic
-rw-r--r-- 1 root root 19M May  7 11:33 initrd.img-3.13.0-52-generic
-rw-r--r-- 1 root root 19M May 21 20:42 initrd.img-3.13.0-53-generic
-rw-r--r-- 1 root root 19M Jun 10 13:40 initrd.img-3.13.0-54-generic
-rw-r--r-- 1 root root 19M Jun 23 06:36 initrd.img-3.13.0-55-generic
-rw-r--r-- 1 root root 16M Oct 18  2013 initrd.img-3.8.0-29-generic
-rw-r--r-- 1 root root 16M Oct 19  2013 initrd.img-3.8.0-31-generic
-rw-r--r-- 1 root root 16M Oct 25  2013 initrd.img-3.8.0-32-generic
-rw-r--r-- 1 root root 16M Dec  2  2013 initrd.img-3.8.0-33-generic
-rw-r--r-- 1 root root 16M Dec  3  2013 initrd.img-3.8.0-34-generic
-rw-r--r-- 1 root root 16M Jan 31  2014 initrd.img-3.8.0-35-generic
-rw-r--r-- 1 root root 16M Feb 19  2014 initrd.img-3.8.0-36-generic
-rw-r--r-- 1 root root 16M Mar 25  2014 initrd.img-3.8.0-37-generic
-rw-r--r-- 1 root root 16M Mar 31  2014 initrd.img-3.8.0-38-generic
-rw-r--r-- 1 root root 16M May  6  2014 initrd.img-3.8.0-39-generic
-rw-r--r-- 1 root root 16M May 26  2014 initrd.img-3.8.0-41-generic
-rw-r--r-- 1 root root 16M Jul  6  2014 initrd.img-3.8.0-42-generic
-rw-r--r-- 1 root root 16M Jul 22  2014 initrd.img-3.8.0-44-generic
drwx------ 2 root root  1M Oct 18  2013 lost+found
-rw-r--r-- 1 root root  1M Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root  1M Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  4M Jul 14  2014 System.map-3.13.0-32-generic
-rw------- 1 root root  4M Jul 30  2014 System.map-3.13.0-33-generic
-rw------- 1 root root  4M Aug 13  2014 System.map-3.13.0-34-generic
-rw------- 1 root root  4M Aug 18  2014 System.map-3.13.0-35-generic
-rw------- 1 root root  4M Sep  4  2014 System.map-3.13.0-36-generic
-rw------- 1 root root  4M Sep 24  2014 System.map-3.13.0-37-generic
-rw------- 1 root root  4M Oct 29  2014 System.map-3.13.0-39-generic
-rw------- 1 root root  4M Nov 14  2014 System.map-3.13.0-40-generic
-rw------- 1 root root  4M Dec  9  2014 System.map-3.13.0-43-generic
-rw------- 1 root root  4M Jan 15 14:46 System.map-3.13.0-45-generic
-rw------- 1 root root  4M Mar 10 15:50 System.map-3.13.0-46-generic
-rw------- 1 root root  4M Mar 12 14:56 System.map-3.13.0-48-generic
-rw------- 1 root root  4M Mar 25 11:58 System.map-3.13.0-49-generic
-rw------- 1 root root  4M Apr 15 17:10 System.map-3.13.0-51-generic
-rw------- 1 root root  4M May  5 13:33 System.map-3.13.0-52-generic
-rw------- 1 root root  4M May 20 12:59 System.map-3.13.0-53-generic
-rw------- 1 root root  4M May 27 06:15 System.map-3.13.0-54-generic
-rw------- 1 root root  4M Jun 18 05:19 System.map-3.13.0-55-generic
-rw------- 1 root root  4M Aug 14  2013 System.map-3.8.0-29-generic
-rw------- 1 root root  4M Sep 11  2013 System.map-3.8.0-31-generic
-rw------- 1 root root  4M Oct  2  2013 System.map-3.8.0-32-generic
-rw------- 1 root root  4M Oct 24  2013 System.map-3.8.0-33-generic
-rw------- 1 root root  4M Nov 13  2013 System.map-3.8.0-34-generic
-rw------- 1 root root  4M Jan 30  2014 System.map-3.8.0-35-generic
-rw------- 1 root root  4M Feb  3  2014 System.map-3.8.0-36-generic
-rw------- 1 root root  4M Feb 19  2014 System.map-3.8.0-37-generic
-rw------- 1 root root  4M Mar 13  2014 System.map-3.8.0-38-generic
-rw------- 1 root root  4M May  2  2014 System.map-3.8.0-39-generic
-rw------- 1 root root  4M May 15  2014 System.map-3.8.0-41-generic
-rw------- 1 root root  4M Jul  4  2014 System.map-3.8.0-42-generic
-rw------- 1 root root  4M Jul 14  2014 System.map-3.8.0-44-generic
-rw------- 1 root root  6M Jul 14  2014 vmlinuz-3.13.0-32-generic
-rw------- 1 root root  6M Jul 30  2014 vmlinuz-3.13.0-33-generic
-rw------- 1 root root  6M Aug 13  2014 vmlinuz-3.13.0-34-generic
-rw------- 1 root root  6M Aug 18  2014 vmlinuz-3.13.0-35-generic
-rw------- 1 root root  6M Sep  4  2014 vmlinuz-3.13.0-36-generic
-rw------- 1 root root  6M Sep 24  2014 vmlinuz-3.13.0-37-generic
-rw------- 1 root root  6M Oct 29  2014 vmlinuz-3.13.0-39-generic
-rw------- 1 root root  6M Nov 14  2014 vmlinuz-3.13.0-40-generic
-rw------- 1 root root  6M Dec  9  2014 vmlinuz-3.13.0-43-generic
-rw------- 1 root root  6M Jan 15 14:46 vmlinuz-3.13.0-45-generic
-rw------- 1 root root  6M Mar 10 15:50 vmlinuz-3.13.0-46-generic
-rw------- 1 root root  6M Mar 12 14:56 vmlinuz-3.13.0-48-generic
-rw------- 1 root root  6M Mar 25 11:58 vmlinuz-3.13.0-49-generic
-rw------- 1 root root  6M Apr 15 17:10 vmlinuz-3.13.0-51-generic
-rw------- 1 root root  6M May  5 13:33 vmlinuz-3.13.0-52-generic
-rw------- 1 root root  6M May 20 12:59 vmlinuz-3.13.0-53-generic
-rw------- 1 root root  6M May 27 06:15 vmlinuz-3.13.0-54-generic
-rw------- 1 root root  6M Jun 18 05:19 vmlinuz-3.13.0-55-generic
-rw-r--r-- 1 root root  6M Oct 18  2013 vmlinuz-3.8.0-29-generic
-rw------- 1 root root  6M Sep 11  2013 vmlinuz-3.8.0-31-generic
-rw------- 1 root root  6M Oct  2  2013 vmlinuz-3.8.0-32-generic
-rw------- 1 root root  6M Oct 24  2013 vmlinuz-3.8.0-33-generic
-rw------- 1 root root  6M Nov 13  2013 vmlinuz-3.8.0-34-generic
-rw------- 1 root root  6M Jan 30  2014 vmlinuz-3.8.0-35-generic
-rw------- 1 root root  6M Feb  3  2014 vmlinuz-3.8.0-36-generic
-rw------- 1 root root  6M Feb 19  2014 vmlinuz-3.8.0-37-generic
-rw------- 1 root root  6M Mar 13  2014 vmlinuz-3.8.0-38-generic
-rw------- 1 root root  6M May  2  2014 vmlinuz-3.8.0-39-generic
-rw------- 1 root root  6M May 15  2014 vmlinuz-3.8.0-41-generic
-rw------- 1 root root  6M Jul  4  2014 vmlinuz-3.8.0-42-generic
-rw------- 1 root root  6M Jul 14  2014 vmlinuz-3.8.0-44-generic
```

---

### Post by coffeecat on 2015-06-25
You have no fewer than 31 different kernels! 

Rather than use the package manager to uninstall old kernels I would go for TheFu's script since you have so many. 

By the way, you need to use the package manager (or apt) to purge old kernels. Simply deleting files in /boot isn't enough.

---

### Post by Bill Dubinski on 2015-06-25
Thanks to all, seems like I got this solved via Ubuntu tweek. Saved my last 10 kernels and will do same in future. 
Then checked for updates, rebotted and rebooted okay. 
We will see next kernel update. 

Thanks all.

---

