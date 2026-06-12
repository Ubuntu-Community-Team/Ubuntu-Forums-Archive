---
title: "VMWare on Ubuntu - Failed to connect to peer process."
date: 2007-07-01
forum: General Help
---

### Post by 19thHole on 2007-07-01
Thanks in advance for any help, I've been trying (off & on) for over a week to solve this myself.  I'm sure it's something stupid easy, but I can't figure it out.  I apologize for the longish post down there, but I'm trying to supply all the info I can.
 
Issue:
    Can't power on VWWare guest.

Setup
 - Dell Precision M65 - 2.4Ghz Core Duo 64 bit CPU; 4Gb Ram; 100Gb HDD, NVidia GPU 
 - Ubuntu "fiesty fawn" 7.04 Desktop, 64 bit AMD and Intel computers ([http://www.ubuntu.com/getubuntu/download);](http://www.ubuntu.com/getubuntu/download);) installed using default options.
 - VMWare Eval ([http://www.vmware.com/download/ws/eval.html);](http://www.vmware.com/download/ws/eval.html);) installed using default options.

I get this error when I try to "power on this virtual machine":
    Unable to change virtual machine power state: Failed to connect to peer process.

I've tried googling, this post seems to be the jist of what's out there:
   [http://peterdedecker.net/blog/index.php/2005/11/25/vmware_troubles](http://peterdedecker.net/blog/index.php/2005/11/25/vmware_troubles))

I've tried sudo chmod o+x vmware-vmx, but instead of the results listed in the post:
   (-rwsr-s--x 1 root vmware 4183128 Jan 23 21:17 vmware-vmx)
I get
   (-r-sr-xr-x  1 root root 5598084 2007-06-25 13:18 vmware-vmx).  
If I don't do it as sudo I get operation not permitted.

I checked the var dir: 11 Gb free.

I don't know how to run vmware-config as root.  I tried entering sudo vmware in the terminal, and while I get different VMWare behavior (doesn't remember where the .vmx file is), once I open it again and try to "power on", I get the same error.

I'm not stupid, but I am a noob, so don't worry about talking down.  I would love nothing more than to learn that this is just some silly PIBCAK error.

Thanks,
Kevin

---

### Post by nardo on 2007-07-09
I had the same problem, the solution it's to install the 32-bits libraries.
the anwser it's in
[http://ubuntuforums.org/showthread.php?p=2990990](http://ubuntuforums.org/showthread.php?p=2990990)

---

