---
title: "Deleting files on /boot"
date: 2013-12-05
forum: General Help
---

### Post by desesperado on 2013-12-05
Hi all. I have a question to the *buntu masters. Presently in my Xubuntu 13.10 installation i have the following kernels```
~$ dpkg-query -l | grep linux-image
ii  linux-image-3.11.5-031105-generic    3.11.5-031105.201310132235          i386         Linux kernel image for version 3.11.5 on 32 bit x86 SMP
ii  linux-image-3.12.0-031200-generic    3.12.0-031200.201311031935          i386         Linux kernel image for version 3.12.0 on 32 bit x86
```and the contents of my **/boot** folder is the following:```
~$ ls -lh /boot
total 233M
-rw-r--r-- 1 root root 978K Oct 14 03:50 abi-3.11.5-031105-generic
-rw-r--r-- 1 root root 985K Nov  4 00:53 abi-3.12.0-031200-generic
[COLOR=#ff0000]-rw-r--r-- 1 root root 834K Oct  9  2012 abi-3.5.0-17-generic
-rw-r--r-- 1 root root 837K Jan  8  2013 abi-3.5.0-22-generic
-rw-r--r-- 1 root root 837K Jan 24  2013 abi-3.5.0-23-generic
-rw-r--r-- 1 root root 839K Feb  7  2013 abi-3.5.0-24-generic
-rw-r--r-- 1 root root 839K Feb 25  2013 abi-3.5.0-25-generic
-rw-r--r-- 1 root root 839K Mar  8  2013 abi-3.5.0-26-generic
-rw-r--r-- 1 root root 841K Mar 25  2013 abi-3.5.0-27-generic
-rw-r--r-- 1 root root 904K Apr 17  2013 abi-3.8.0-19-generic[/COLOR]
-rw-r--r-- 1 root root 164K Oct 14 03:50 config-3.11.5-031105-generic
-rw-r--r-- 1 root root 163K Nov  4 00:53 config-3.12.0-031200-generic
[COLOR=#ff0000]-rw-r--r-- 1 root root 151K Oct  9  2012 config-3.5.0-17-generic
-rw-r--r-- 1 root root 151K Jan  8  2013 config-3.5.0-22-generic
-rw-r--r-- 1 root root 151K Jan 24  2013 config-3.5.0-23-generic
-rw-r--r-- 1 root root 151K Feb  7  2013 config-3.5.0-24-generic
-rw-r--r-- 1 root root 151K Feb 25  2013 config-3.5.0-25-generic
-rw-r--r-- 1 root root 151K Mar  8  2013 config-3.5.0-26-generic
-rw-r--r-- 1 root root 152K Mar 25  2013 config-3.5.0-27-generic
-rw-r--r-- 1 root root 158K Apr 17  2013 config-3.8.0-19-generic[/COLOR]
drwxr-xr-x 5 root root 4.0K Dec  5 00:36 grub
-rw-r--r-- 1 root root  16M Nov 13 21:42 initrd.img-3.11.5-031105-generic
-rw-r--r-- 1 root root  17M Dec  4 23:28 initrd.img-3.12.0-031200-generic
[COLOR=#ff0000]-rw-r--r-- 1 root root  15M Jan 25  2013 initrd.img-3.5.0-17-generic
-rw-r--r-- 1 root root  15M Jan 25  2013 initrd.img-3.5.0-22-generic
-rw-r--r-- 1 root root  15M Jan 31  2013 initrd.img-3.5.0-23-generic
-rw-r--r-- 1 root root  15M Feb 19  2013 initrd.img-3.5.0-24-generic
-rw-r--r-- 1 root root  15M Feb 26  2013 initrd.img-3.5.0-25-generic
-rw-r--r-- 1 root root  15M Mar 28  2013 initrd.img-3.5.0-26-generic
-rw-r--r-- 1 root root  15M Apr 30  2013 initrd.img-3.5.0-27-generic
-rw-r--r-- 1 root root  16M Apr 30  2013 initrd.img-3.8.0-19-generic[/COLOR]
-rw-r--r-- 1 root root 173K Jun 17 10:52 memtest86+.bin
-rw-r--r-- 1 root root 175K Jun 17 10:52 memtest86+_multiboot.bin
-rw------- 1 root root 2.6M Oct 14 03:50 System.map-3.11.5-031105-generic
-rw------- 1 root root 2.7M Nov  4 00:53 System.map-3.12.0-031200-generic
[COLOR=#ff0000]-rw------- 1 root root 2.3M Oct  9  2012 System.map-3.5.0-17-generic
-rw------- 1 root root 2.3M Jan  8  2013 System.map-3.5.0-22-generic
-rw------- 1 root root 2.3M Jan 24  2013 System.map-3.5.0-23-generic
-rw------- 1 root root 2.3M Feb  7  2013 System.map-3.5.0-24-generic
-rw------- 1 root root 2.3M Feb 25  2013 System.map-3.5.0-25-generic
-rw------- 1 root root 2.3M Mar  8  2013 System.map-3.5.0-26-generic
-rw------- 1 root root 2.3M Mar 25  2013 System.map-3.5.0-27-generic
-rw------- 1 root root 2.4M Apr 17  2013 System.map-3.8.0-19-generic[/COLOR]
-rw------- 1 root root 5.5M Oct 14 03:50 vmlinuz-3.11.5-031105-generic
-rw------- 1 root root 5.6M Nov  4 00:53 vmlinuz-3.12.0-031200-generic
[COLOR=#ff0000]-rw-r--r-- 1 root root 5.0M Oct 17  2012 vmlinuz-3.5.0-17-generic
-rw------- 1 root root 5.0M Jan  8  2013 vmlinuz-3.5.0-22-generic
-rw------- 1 root root 5.0M Jan 24  2013 vmlinuz-3.5.0-23-generic
-rw------- 1 root root 5.0M Feb  7  2013 vmlinuz-3.5.0-24-generic
-rw------- 1 root root 5.0M Feb 25  2013 vmlinuz-3.5.0-25-generic
-rw------- 1 root root 5.0M Mar  8  2013 vmlinuz-3.5.0-26-generic
-rw------- 1 root root 5.0M Mar 25  2013 vmlinuz-3.5.0-27-generic
-rw------- 1 root root 5.2M Apr 17  2013 vmlinuz-3.8.0-19-generic[/COLOR]
```So my question is: can I safely remove all those files that relate to previous versions of kernels from **/boot**&#8203;, which I think are the ones I highlighted in red, leaving just the ones that relate to the existent kernels in my computer?

Thanks in advance for helping.

---

### Post by plucky on 2013-12-05
You should be able to use ```
sudo apt-get autoremove
``` to reduce the number of kernels.

It will keep the current and previous kernel,just in case you need to boot into an earlier kernel.

This was introduced in an earlier release (13.04?).

On earlier releases.I always used Synaptic Package Manager to remove kernels and headers.


Good Luck

---

### Post by slickymaster on 2013-12-05
I would advise you on using Synaptic, also.

---

### Post by The Cog on 2013-12-05
I have also been through an exercise of removing old kernels from /boot like that. I checked with aptitude rather than dpkg though I imagine the results would be the same, then manually deleted all the ones that it didn't think were installed, just as you are suggesting. No harm came of doing so. 

And actually, because the default install options create a 500M /boot partition, if you don't clear out in time eventually an upgrade fails partway through because the partition is full. Then it can take hours to clean up the mess - it refuses to either upgrade or downgrade because of broken dependencies. I'm not that familiar with the dependency management, and I think that reinstalling can be the quickest solution when that happens.

---

### Post by desesperado on 2013-12-05
Firstly let me thank you for your answers and helpful advices.

> **plucky said:**
> You should be able to use ```
sudo apt-get autoremove
``` to reduce the number of kernels.
It will keep the current and previous kernel,just in case you need to boot into an earlier kernel.
This was introduced in an earlier release (13.04?).
On earlier releases.I always used Synaptic Package Manager to remove kernels and headers.
Good Luck

I removed the previous/old kernels using```
sudo apt-get purge linux-imagexxxxxx
```and that left all those files in my **/boot** folder, hence why I'm questioning if they're safe for deletion since the kernels that they relate to are no longer in the computer.

> **The Cog said:**
> I have also been through an exercise of removing old kernels from /boot like that. I checked with aptitude rather than dpkg though I imagine the results would be the same, then manually deleted all the ones that it didn't think were installed, just as you are suggesting. No harm came of doing so. 

And actually, because the default install options create a 500M /boot partition, if you don't clear out in time eventually an upgrade fails partway through because the partition is full. Then it can take hours to clean up the mess - it refuses to either upgrade or downgrade because of broken dependencies. I'm not that familiar with the dependency management, and I think that reinstalling can be the quickest solution when that happens.

I'm no expert by all means, just a curios and eager to learn user, but it strikes me as logical that no harm would come of removing them since they were installed by kernels that I already purged from the computer. Is this assumption I'm making correct?

---

### Post by philinux on 2013-12-05
I use this (step 5 is the main bit) now and again to remove all but the latest kernel. I make sure I'm happy with any new kernel. Usually a few days in use.

I always use the dry run in step 5 before doing a purge,

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by desesperado on 2013-12-05
> **philinux said:**
> I use this (step 5 is the main bit) now and again to remove all but the latest kernel. I make sure I'm happy with any new kernel. Usually a few days in use.

I always use the dry run in step 5 before doing a purge,

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Thanks for you input philinux. I've tried already the dry run you suggested but that doesn't seems to delete the files I mentioned which leaves me pretty much with my initial doubt.

---

### Post by philinux on 2013-12-05
Post the output of the dry run for us. Don't forget the code tags.

---

### Post by plucky on 2013-12-05
Have you tried the ```
sudo apt-get autoremove
``` command,as that will also remove any dependencies that are no longer required?

> I'm no expert by all means, just a curios and eager to learn user, but it strikes me as logical that no harm would come of removing them since they were installed by kernels that I already purged from the computer. Is this assumption I'm making correct? 

I see no problem with removing them now as you have already removed the kernel images.They might still be there as the linux-headers are still installed.

See what the "autoremove" command tells you.

Good Luck

---

### Post by The Cog on 2013-12-05
> **desesperado said:**
> I'm no expert by all means, just a curios and eager to learn user, but it strikes me as logical that no harm would come of removing them since they were installed by kernels that I already purged from the computer. Is this assumption I'm making correct?
Yes, I think you are correct. 
I don't really understand how it came to have all those kernels and initrd files left in /boot when aptitude said they weren't installed, but these were quite old machines (many years out of date) and I think the handling of /boot has improved since then. But even if you remove everything except the kernel that it's currently configured to boot, no harm happens.

---

### Post by desesperado on 2013-12-05
> **philinux said:**
> Post the output of the dry run for us. Don't forget the code tags.

Here it is philinux```
~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libc6-dev linux-headers-3.11.5-031105 linux-headers-3.11.5-031105-generic
  linux-image-3.11.5-031105-generic linux-libc-dev
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Remv libc6-dev [2.17-93ubuntu4]
Remv linux-headers-3.11.5-031105-generic [3.11.5-031105.201310132235]
Remv linux-headers-3.11.5-031105 [3.11.5-031105.201310132235]
Remv linux-image-3.11.5-031105-generic [3.11.5-031105.201310132235]
Remv linux-libc-dev [3.11.0-14.21]
```As you can see the files I mentioned on my first post won't be deleted.

---

### Post by philinux on 2013-12-05
I would use synaptic to remove all those old kernels then. Odd though.

Is this package installed

```
apt-cache policy linux-generic
```

---

### Post by desesperado on 2013-12-05
> **plucky said:**
> Have you tried the ```
sudo apt-get autoremove
``` command,as that will also remove any dependencies that are no longer required?

I see no problem with removing them now as you have already removed the kernel images.They might still be there as the linux-headers are still installed.

See what the "autoremove" command tells you.

Good Luck

Yes, I've tried it but it doesn't remove anything.

I've checked, and there are no more linux-headers still installed besides the ones related to linux-image-3.11.5-031105-generic and  linux-image-3.12.0-031200-generic.

---

### Post by desesperado on 2013-12-05
> **The Cog said:**
> Yes, I think you are correct. 
I don't really understand how it came to have all those kernels and initrd files left in /boot when aptitude said they weren't installed, but these were quite old machines (many years out of date) and I think the handling of /boot has improved since then. But even if you remove everything except the kernel that it's currently configured to boot, no harm happens.

That makes two of us wondering on that.

Anyway The Cog, thanks for your answers. I'll go ahead and delete them as I see the logical in your arguments.

---

### Post by desesperado on 2013-12-05
> **philinux said:**
> I would use synaptic to remove all those old kernels then. Odd though.

Is this package installed

```
apt-cache policy linux-generic
```

Yes it is, philinux.

I'm going to delete those files as The Cog said and since everybody concurs on the fact that no harm will come of it I'm going to mark this thread as solved.

Once again I thank you all guys for your help and advices.

---

### Post by philinux on 2013-12-05
> **desesperado said:**
> Yes it is, philinux.

I'm going to delete those files as The Cog said and since everybody concurs on the fact that no harm will come of it I'm going to mark this thread as solved.

Once again I thank you all guys for your help and advices.

After you've done that just run this.

```
sudo update-grub
```

---

