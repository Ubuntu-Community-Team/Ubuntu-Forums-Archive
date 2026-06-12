---
title: "Captive-NTFS"
date: 2005-07-03
forum: General Help
---

### Post by fizgig on 2005-07-03
So I want to get write support going in Ubuntu for my ntfs partition.  I installed the captive-ntfs package and then tried to run /usr/share/lufs/prepmod

It does some stuff but then says:

[b]Failed to prepare lufs.ko module for your Linux kernel 2.6.10-5-686.
Detected Linux kernel sources "/lib/modules/2.6.10-5-686/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-5-686/build
                /usr/src/kernel-headers-2.6.10-5-686
                /usr/src/linux-2.6.10-5-686
                /usr/src/linux-2.6.10
                /usr/src/linux
                /usr/src/kernel-source-2.6.10-5-686
[/b]
I'm not sure what to do next.  I have /usr/src/linux pointing at linux-source-2.6.10 but I am currently running 2.6.10-5-686.  I also have linux-headers-2.6.10-5-686 in there as well.  I'm not an expert at this and I'm not sure what to do.  Any tips?

---

### Post by mad_alfred on 2005-07-04
I'd select the NTFS write support during kernel compiling

you can follow this guide [kernel compiling](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compiling)

i wouldn't suggest write support for ntfs partition, i'd rather create a FAT32 partition which you can create with partition-magic ( which is very easy to use under windows of course lol) and then transfer all the files you want to share with windows/linux in it.

that's what i did and works perfectly. :D

there is a guide on how to create a fat32 partition and mount it on boot [here](http://ubuntuguide.org/#mountunmountfat)

partition magic can be found [here](http://www.soft32.com/download_151.html)

 
cheers,chris  :)

---

### Post by fizgig on 2005-07-04
I appreciate it but kernel ntfs support is very limited and can be dangerous.  Captive appears to be perfect (once installed correctly).

---

### Post by Prog on 2005-07-05
So is there no way to mount a writable ntfs drive on boot?

Also, is captive-ntfs supposed to be in synaptic?  Because it's not for me, and I've already done that extra repositories thing in the Ubuntu guide. D:

---

### Post by fizgig on 2005-07-05
I aliened it from the rpm package on the captive site.

I know of no other method to mount an NTFS partition as writable safely.

---

