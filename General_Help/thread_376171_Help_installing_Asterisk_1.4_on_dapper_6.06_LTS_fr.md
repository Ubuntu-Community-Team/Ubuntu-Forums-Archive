---
title: "Help installing Asterisk 1.4 on dapper 6.06 LTS from Source"
date: 2007-03-04
forum: General Help
---

### Post by vinooj on 2007-03-04
System Information
OS: Ubuntu 6.06 LTS 
CPU: AMD Dual core 2800
Kernel: 2.6.15-27-k7 with SMP

I'm having issues installing Asterisk1.4 from source via checkinstall. I was able to succesfully compile zaptel_1.4.0, libpri-1 .4.0, asterisk-1.4.1 using 'make linux26'

However trying to use 'Checkinstall" to install zaptel, I got the following error,

Unpacking zaptel (from .../zaptel_1.4.0-1_i386.deb) ...
dpkg: error processing /home/vinoo/tmp/zaptel-1.4.0/zaptel_1.4.0-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.15-27-k7/modules.alias', which is also in package linux-image-2.6.15-27-k7
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/vinoo/tmp/zaptel-1.4.0/zaptel_1.4.0-1_i386.deb

Looking at th error it looks like the checkinstall is trying to update modules.alias file to include zaptel shared libraries. Howver I wasn't sure whteher this will happen if I had done a 'make install'. If not, why is the 'checkinstall' trying to do this.

What should I do? 

Thanks in advance for the help.

-vinoo

---

