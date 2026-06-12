---
title: "How to install Kali Linux tools or at least create a live USB in Ubuntu"
date: 2014-12-20
forum: General Help
---

### Post by YQ002lc2 on 2014-12-20
I'm looking for and not finding a way to integrate Kali Linux Tools into Ubuntu 14.04?

If I can't integrate the tools, can someone guide me through the process of creating a Kali Linux live USB?

I've tried to install a VM of Kali Linux on VirtualBox, but I always get errors.

---

### Post by C.S.Cameron on 2014-12-20
What happens when you follow the info on the Kali pages:

[http://docs.kali.org/category/installation](http://docs.kali.org/category/installation)

---

### Post by oldos2er on 2014-12-21
> **YQ002lc2 said:**
> I'm looking for and not finding a way to integrate Kali Linux Tools into Ubuntu 14.04?


There's a git repository [here]("http://git.kali.org/gitweb/"), that would probably be the easiest way. Some of the tools might have versions in the Ubuntu repositories too.

---

### Post by YQ002lc2 on 2014-12-22
Thank you for your reply, C.S.Cameron.   

All the options give some kind of error. I've tried to install it as a virtual machine and I've tried to make a USB live disk without success on two computers. 

I used gparted to create two partitions. 
I then used unetbootin to install the live image to the root partition. 
I made the persistence.conf file in the second partition. 
I made sure these files had the correct chmod attributes. 
I booted from the USB and got errors in both the default boot option and the boot with encrypted persistence. 

The default option gives a segfault with "...Server terminated with error (1) Closing log file" 
The boot with encrypted persistence gives 
cat: can't open '/sys/block/*/removable': No such file or directory 
Eventually, it shows 
Unable to find a medium containing a live file system
modprobe: chdir(3.14-kali1-486): no such file or directory
Please let me know any procedure you used. The information on kali.org wasn't much help for me. 


Thank you, oldos2er. Perhaps you can help?
I tried:
$git clone git://git.kali.org/packages/cowpatty.git
$cd ~/cowpatty

What do I do from there? I'm not familiar with git and the information from google wasn't much help.

---

