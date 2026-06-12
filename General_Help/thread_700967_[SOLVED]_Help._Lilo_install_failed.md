---
title: "[SOLVED] Help. Lilo install failed"
date: 2008-02-18
forum: General Help
---

### Post by Akovia on 2008-02-18
Hi,
I installed lilo and made a newb syntax error trying to run liloconfig. I finally figured that out and have the configuration running now but of course there is always some kind of problem.

Here is the warning I get:

 WARNING!                                                                     
 &#9474;                                                                              
 &#9474; Your /etc/fstab configuration file gives device                             
 &#9474; UUID=f1e0249a-1442-4143-817b-429358c9f872 as the root filesystem device.  
 &#9474; This doesn't look to me like an "ordinary" block device. Either your     
 &#9474; fstab is broken and you should fix it, or you are using hardware (such as   
 &#9474; a RAID array) which this simple configuration program does not handle.  
 &#9474;                                                                            
 &#9474; You should either repair the situation or hand-roll your own                
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig     
 &#9474; again to retry the configuration process. Documentation for LILO can be     
 &#9474; found in /usr/share/doc/lilo/.                                       


I had grub before and wondered if there was any safe way to stop the lilo install and revert back, or figure out how to continue here.

Thanks,
Akovia


Thanks,
Akovia

---

### Post by bodhi.zazen on 2008-02-18
installing lilo onto Ubuntu is not so easy.

Try these links :

[http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)

Hermanzone : [http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

---

### Post by Akovia on 2008-02-19
You are a god amongst men. The second link guided me to be able to install lilo while keeping Grub as my boot manager. Thanks for the quick and accurate response.

Akovia

---

### Post by bodhi.zazen on 2008-02-19
LOL, but we really should thank Herman for writing / maintaining the link I gave you ;)

---

