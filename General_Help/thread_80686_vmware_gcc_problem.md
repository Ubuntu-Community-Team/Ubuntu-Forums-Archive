---
title: "vmware gcc problem"
date: 2005-10-22
forum: General Help
---

### Post by Dajazzz on 2005-10-22
Hi.

I'm trying to install VMware but i get this problem. How can I install gcc 3.4.5?
when I type sudo apt-get install gcc-3.4 I get 
gcc-3.4 is already the newest version

This is the error that I get at the end of the istallation of VMware.

Trying to find a suitable vmmon module for your running kernel.

None of the pre-build vmmon modules for VMware Workstaion is suitable for your  running kernel. Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on you system)? YES

Using compiler "/usr/bin/gcc". Use environment variable CC to override

Your kernel was build with "gcc" version "3.4.5", while you are trying to use "/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware workstation cannot work in such configuration. Please either recompile your kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl with CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please visit our Web site at "http://www.vmware.com

Exectution aborted. 

Hope that someone can help me!

THX

---

### Post by trilo on 2005-10-22
Version 3.4 will do fine, actually it may very well be 3.4.5

That isn't the problem, the problem is what that message tells you the problem is. You're trying to use gcc 4, when you need to use 3.4.

---

### Post by Dajazzz on 2005-10-22
[QUOTE=trilo]Version 3.4 will do fine, actually it may very well be 3.4.5

That isn't the problem, the problem is what that message tells you the problem is. You're trying to use gcc 4, when you need to use 3.4.[/QUOTE]
:?
and how can I use version 3.4.5 / 3.4 ?

Thx

---

### Post by trilo on 2005-10-22
well, the message says, "Using compiler "/usr/bin/gcc". Use environment variable CC to override"

i've only just joined this forum, but isn't there a search function?

EDIT: ok, i searched for: vmware install gcc

and got this:

[http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware+install+gcc](http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware+install+gcc)

seems pretty easy

---

### Post by Dajazzz on 2005-10-22
[QUOTE=trilo]well, the message says, "Using compiler "/usr/bin/gcc". Use environment variable CC to override"

i've only just joined this forum, but isn't there a search function?

EDIT: ok, i searched for: vmware install gcc

and got this:

[http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware+install+gcc](http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware+install+gcc)

seems pretty easy[/QUOTE]
OKE thanks TRILO

I am already further...
The only thing I did not have was the # export CC=/usr/bin/gcc-3.4 line


THX!

---

### Post by Dajazzz on 2005-10-22
after the ./runme.pl my system freezes...

---

### Post by orzechowskid on 2005-10-22
what version of vmware are you using?  I just installed Workstation 5.5, and all I had to do was set CC=/usr/bin/gcc-3.4 , and download the source for my current kernel and point vmware-install.pl to that directory.  Run fine for me.

Did that runme.pl come from one of the semi-official patch tarballs?  Like I said, if you're using 5.5 then you might not need it.

---

### Post by Samuel on 2005-10-22
i got a freeze when i ran the patch too, rebooted and tried again (with the # export CC=/usr/bin/gcc-3.4 line) and all went well.

---

### Post by Dajazzz on 2005-10-23
[QUOTE=Samuel]i got a freeze when i ran the patch too, rebooted and tried again (with the # export CC=/usr/bin/gcc-3.4 line) and all went well.[/QUOTE]
Oke that worked, after a reboot.
thx guys!

---

