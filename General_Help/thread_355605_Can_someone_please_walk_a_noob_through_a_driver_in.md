---
title: "Can someone please walk a noob through a driver install?"
date: 2007-02-07
forum: General Help
---

### Post by KhanFire on 2007-02-07
Hi everyone! I just installed ubuntu on my laptop and am ready to begin the learning curve.  I am trying to install a driver for my cat-5 -> USB adapter and I'm having a real hard time understanding what the instructions want me to do.  Perhaps someone can decode what it is asking me to do?

Here is what the readme file said:

> USBKR-100 on linux is as follows:

  step 1: compile:
	   gcc -DMODULE -D__KERNEL__ -c rtl8150.c -I/usr/src/linux-2.4.0/include/
           *linux-2.4.0 will change according to the kernel version
           
  step 2: insert the driver as module:
           insmod rtl8150.o        
           (run 'lsmod' to see if the module is inserted)

  step 3: bind your card to an IP address:

           /sbin/ifconfig eth0 ${IPADDR} netmask ${NETMASK} broadcast ${BROADCAST} 
           (run 'netstat -i' to see if there is a interface 'eth0')

  step 4: add your card to IP routing table and add gateway:
	   /sbin/route add default gw ${GATEWAY} dev eth0


*make sure that your kernel is version 2.4.0 or next version.
 Otherwise, you have to	upgrade your kernel.
 ([http://www.kernel.org/pub/linux/kernel/v2.4](http://www.kernel.org/pub/linux/kernel/v2.4)) 


---

### Post by llamakc on 2007-02-07
Those instructions are for the 2.4 kernel, you're running a 2.6 most likely.

Before trying to compile a module, have you tried the device natively?

---

### Post by KhanFire on 2007-02-07
Yes I am running a 2.6, this is however the only release of the driver I have found.  I have tried to use the device but I am still unable to use it to connect to the internet.

---

### Post by llamakc on 2007-02-07
The 2.4 module source will not compile on 2.6. You'll need to track down source for 2.6 or find somebody that has already solved the problem.

What's the device's model number?

---

### Post by llamakc on 2007-02-07
Why not just load the module that ships with 2.6?

`sudo insmod rtl8150`

`lsmod | grep rtl8150`


It's loaded, correct? You shouldn't need to compile that source at all.

---

