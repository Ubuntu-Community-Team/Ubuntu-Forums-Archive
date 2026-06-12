---
title: "Help regarding linux-headers"
date: 2013-09-03
forum: General Help
---

### Post by Ashiq_Irphan on 2013-09-03
I`m trying to compile some code, as per the instructions I need to have the linux headers on my machine, so I ran this code

```
vm001@vm001-VirtualBox:~$ uname -r
3.2.0-29-generic-pae
vm001@vm001-VirtualBox:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for vm001: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-29-generic-pae is already the newest version.
linux-headers-3.2.0-29-generic-pae set to manually installed.
The following packages were automatically installed and are no longer required:
  ruby1.8 ruby libruby1.8 libreadline5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 455 not upgraded.
```


I hope this means all my headers are already available, Isn`t it ?

As the next step I tried to compile the code

```
vm001@vm001-VirtualBox:~/Downloads/aodv-uu-0.9.6$ make
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o main.o main.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o list.o list.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o debug.o debug.c
debug.c: In function ‘print_rt_table’:
debug.c:349:13: warning: variable ‘written’ set but not used [-Wunused-but-set-variable]
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o timer_queue.o timer_queue.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_socket.o aodv_socket.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_hello.o aodv_hello.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_neighbor.o aodv_neighbor.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_timeout.o aodv_timeout.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o routing_table.o routing_table.c
routing_table.c: In function ‘rt_table_insert’:
routing_table.c:92:17: warning: variable ‘nm’ set but not used [-Wunused-but-set-variable]
routing_table.c: In function ‘rt_table_update’:
routing_table.c:196:17: warning: variable ‘nm’ set but not used [-Wunused-but-set-variable]
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o seek_list.o seek_list.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_rreq.o aodv_rreq.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_rrep.o aodv_rrep.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_rerr.o aodv_rerr.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o nl.o nl.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o locality.o locality.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -o aodvd main.o list.o debug.o timer_queue.o aodv_socket.o aodv_hello.o aodv_neighbor.o aodv_timeout.o routing_table.o seek_list.o aodv_rreq.o aodv_rrep.o aodv_rerr.o nl.o locality.o 
make -C /home/vm001/Downloads/aodv-uu-0.9.6/lnx KERNEL_DIR=/lib/modules/3.2.0-29-generic-pae/build KCC=gcc XDEFS=-DDEBUG
make[1]: Entering directory `/home/vm001/Downloads/aodv-uu-0.9.6/lnx'
gcc -Wall -Wno-strict-aliasing -O2 -D__KERNEL__ -DMODULE -nostdinc -DMODVERSIONS -include /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h -I /usr/lib/gcc/i686-linux-gnu/4.6/include -I/lib/modules/3.2.0-29-generic-pae/build/include -DDEBUG -c -o kaodv-mod.o kaodv-mod.c
***cc1: fatal error: /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h: No such file or directory***
compilation terminated.
make[1]: *** [kaodv-mod.o] Error 1
make[1]: Leaving directory `/home/vm001/Downloads/aodv-uu-0.9.6/lnx'
make: *** [kaodv] Error 2
```

Ignoring the warnings, leaves me with just one error (the one that I have highlighted above).
I`m not able to fix it, pls help me.

Thanks in advance.

P.S: If you want to know what code I`m trying to compile pls look at this link [http://sourceforge.net/projects/aodvuu/](http://sourceforge.net/projects/aodvuu/)

---

### Post by rai_shu2 on 2013-09-03
To run make from Debian/Ubuntu, you still need the "build-essential" package. So, make sure you have that installed.

---

### Post by Ashiq_Irphan on 2013-09-03
> **rai_shu2 said:**
> To run make from Debian/Ubuntu, you still need the "build-essential" package. So, make sure you have that installed.

I have installed the "build-essential" package but still got the same error

```
vm001@vm001-VirtualBox:~/Downloads/aodv-uu-0.9.6$ make
make -C /home/vm001/Downloads/aodv-uu-0.9.6/lnx KERNEL_DIR=/lib/modules/3.2.0-29-generic-pae/build KCC=gcc XDEFS=-DDEBUG
grep: /lib/modules/3.2.0-29-generic-pae/build/Makefile: No such file or directory
make[1]: Entering directory `/home/vm001/Downloads/aodv-uu-0.9.6/lnx'
gcc -Wall -Wno-strict-aliasing -O2 -D__KERNEL__ -DMODULE -nostdinc -DMODVERSIONS -include /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h -I /usr/lib/gcc/i686-linux-gnu/4.6/include -I/lib/modules/3.2.0-29-generic-pae/build/include -DDEBUG -c -o kaodv-mod.o kaodv-mod.c
cc1: fatal error: /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h: No such file or directory
compilation terminated.
make[1]: *** [kaodv-mod.o] Error 1
make[1]: Leaving directory `/home/vm001/Downloads/aodv-uu-0.9.6/lnx'
make: *** [kaodv] Error 2
```

---

### Post by rai_shu2 on 2013-09-03
I guess you need the source code for the kernel.

```
sudo apt-get source linux-image-$(uname -r)
```

---

### Post by Ashiq_Irphan on 2013-09-04
Thanks for your interest in helping me [[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1844973")@rai_shu2.

I`m going to try it now and I`ll get back to you with the results

---

### Post by Ashiq_Irphan on 2013-09-04
> **rai_shu2 said:**
> I guess you need the source code for the kernel.

```
sudo apt-get source linux-image-$(uname -r)
```

Tried what you said but still there is no change. Same error and no change

```
vm001@vm001-VirtualBox:~/Downloads/aodv-uu-0.9.6$ make
make -C /home/vm001/Downloads/aodv-uu-0.9.6/lnx KERNEL_DIR=/lib/modules/3.2.0-29-generic-pae/build KCC=gcc XDEFS=-DDEBUG
make[1]: Entering directory `/home/vm001/Downloads/aodv-uu-0.9.6/lnx'
gcc -Wall -Wno-strict-aliasing -O2 -D__KERNEL__ -DMODULE -nostdinc -DMODVERSIONS -include /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h -I /usr/lib/gcc/i686-linux-gnu/4.6/include -I/lib/modules/3.2.0-29-generic-pae/build/include -DDEBUG -c -o kaodv-mod.o kaodv-mod.c
cc1: fatal error: /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h: No such file or directory
compilation terminated.
make[1]: *** [kaodv-mod.o] Error 1
make[1]: Leaving directory `/home/vm001/Downloads/aodv-uu-0.9.6/lnx'
make: *** [kaodv] Error 2
```

Pls help me, I`m so desperate and I need to get it working.....

---

### Post by Ashiq_Irphan on 2013-09-04
I tried the following..

I ran a search on the file ***modversions.h*** Copied the file to the location.

```
vm001@vm001-VirtualBox:/aodv-uu-0.9.6$ sudo find / -name modversions.h
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/modversions.h
vm001@vm001-VirtualBox:/usr/src/linux-headers-3.2.0-29-generic-pae/include/config$ sudo cp modversions.h /lib/modules/3.2.0-29-generic-pae/build/include/linux/
```

Now a getting new errors.

```
vm001@vm001-VirtualBox:/aodv-uu-0.9.6$ make
make -C /aodv-uu-0.9.6/lnx KERNEL_DIR=/lib/modules/3.2.0-29-generic-pae/build KCC=gcc XDEFS=-DDEBUG
make[1]: Entering directory `/aodv-uu-0.9.6/lnx'
gcc -Wall -Wno-strict-aliasing -O2 -D__KERNEL__ -DMODULE -nostdinc -DMODVERSIONS -include /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h -I /usr/lib/gcc/i686-linux-gnu/4.6/include -I/lib/modules/3.2.0-29-generic-pae/build/include -DDEBUG -c -o kaodv-mod.o kaodv-mod.c
In file included from /lib/modules/3.2.0-29-generic-pae/build/include/linux/list.h:4:0,
                 from /lib/modules/3.2.0-29-generic-pae/build/include/linux/module.h:9,
                 from kaodv-mod.c:29:
/lib/modules/3.2.0-29-generic-pae/build/include/linux/types.h:4:23: fatal error: asm/types.h: No such file or directory
compilation terminated.
make[1]: *** [kaodv-mod.o] Error 1
make[1]: Leaving directory `/aodv-uu-0.9.6/lnx'
make: *** [kaodv] Error 2
```

Need some help to get this fixed.

---

### Post by steeldriver on 2013-09-04
I think your fundamental problem is that the source code is from 2010 and is explicitly configured to build on a 2.x kernel - you're basically going to have to re-write the lnx/Makefile to reflect new locations of various header files - you've found the new location of modversions.h but all the arch-dependent types.h files are now in /usr/src/linux-headers-$(uname -r)/arch for example. I don't know of a 'quick fix' - sorry.

---

### Post by Ashiq_Irphan on 2013-09-04
> **steeldriver said:**
> I think your fundamental problem is that the source code is from 2010 and is explicitly configured to build on a 2.x kernel - you're basically going to have to re-write the lnx/Makefile to reflect new locations of various header files - you've found the new location of modversions.h but all the arch-dependent types.h files are now in /usr/src/linux-headers-$(uname -r)/arch for example. I don't know of a 'quick fix' - sorry.

I`m going to try it now. I shall get back to you when I have an update.

I really appreciate the help.

---

### Post by rai_shu2 on 2013-09-04
That's just line 12 of Makefile, right?

```
KERNEL_DIR=/lib/modules/$(KERNEL)/build
```

So, change that to:

```
KERNEL_DIR=/usr/src/linux-headers-$(KERNEL)
```

---

### Post by Ashiq_Irphan on 2013-09-06
I`m still trying to fix this issue, 
The publisher of the code has recommended using a Red Hat system, so I was surprised if there is any major difference between the Red Hat Linux system and our dear Ubuntu system ???

---

### Post by rai_shu2 on 2013-09-06
The publisher requires the 2.4 or 2.6 kernel. I suspect they wrote those documents before Ubuntu even existed. Obviously, any kernel made within the past 10 years should handle this code no problem (assuming we can update it to work with a 3.x kernel).

---

### Post by Ashiq_Irphan on 2013-09-09
Thanks everybody for their support.

Since the "readme" file on the code suggested using a Red Hat Enterprise Linux system, I tried the code on a fedora machine too. Same errors, I know it would happen, but still wanted to give it a try.

I also posted the errors on the fedora forum and no luck fixing it....

So finally decided to program it myself.

I have posted few of my doubts regarding eclipse on a different [thread]("http://ubuntuforums.org/showthread.php?t=2173409"), If you guys can share your thoughts on it, that would be great.

***Thanks a lot.***

---

