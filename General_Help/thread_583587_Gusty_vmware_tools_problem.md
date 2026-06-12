---
title: "Gusty vmware tools problem"
date: 2007-10-20
forum: General Help
---

### Post by Tex-Twil on 2007-10-20
Hi,
I'm trying to install vmware tools on a guest Gusty distribution. I have a problem with the **vmware-config-tools.pl** phase. It says that the headers of my kernel are different from the kernel I'm running.

> Unable to make a vmhgfs module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmhgfs.o': -1 File exists
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.


I did install the headers 

> 
sudo aptitude install linux-headers-$(uname -r)


any ideas ?


thanks.

---

### Post by biovore on 2007-10-23
It dosn't work anymore because the newer linux kernels arn't correctly support by vmware.  There is a patch you have to apply to the vmware install in order for it to work right.

See:
[http://communities.vmware.com/message/645058](http://communities.vmware.com/message/645058)
There are a bunch of home brew solutions. 

Also make sure your using the newest version of vmware.

---

### Post by Tex-Twil on 2007-10-30
Hi,
I read some thread on the forum but it seems like there is a patch for the host OS. I'm running Gusty in a **client** and I can't compile vmware tools in the client.

Thanks

---

