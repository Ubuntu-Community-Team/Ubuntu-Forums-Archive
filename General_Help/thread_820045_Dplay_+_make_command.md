---
title: "Dplay + make command"
date: 2008-06-05
forum: General Help
---

### Post by miickEe on 2008-06-05
Hey

I'm following this tutorial here
[http://www.linux-sottises.net/en_themasq.php](http://www.linux-sottises.net/en_themasq.php)

Regarding DirectPlay and installing the ip_masq module. I am having troubles in using the make command, since most of the rest depends on it.

I've untar'd the tarball, then placed it in /usr/local/src and tried to run the "make" command. I don't know what it takes as arguments but all I know is that it wont work for me.

```

miickee@miickee-gutsy:/usr/local/src/ip_masq_dplay-0.3.00$ make
Configure the kernel before compiling the module
make: *** [all] Error 1

```

And instead of having the file ip_masq_dplay.o I have ip_masq_dplay.c. It wants me to put the ip_masq_dlay.o file in /lib/modules/2.6.22-14-generic/ipv4 folder, but there is no ipv4 folder.
```


miickee@miickee-gutsy:/lib/modules/2.6.22-14-generic$ ls -l -a -h
total 1.8M
drwxr-xr-x  7 root root 4.0K 2008-06-01 14:52 .
drwxr-xr-x  3 root root 4.0K 2007-10-16 09:20 ..
lrwxrwxrwx  1 root root   40 2008-06-01 12:08 build -> /usr/src/linux-headers-2.6.22-14-generic
drwxr-xr-x  2 root root 4.0K 2008-06-01 14:36 initrd
drwxr-xr-x 10 root root 4.0K 2007-10-16 09:20 kernel
drwxr-xr-x  2 root root 4.0K 2008-06-01 14:47 madwifi
-rw-r--r--  1 root root 357K 2008-06-01 14:52 modules.alias
-rw-r--r--  1 root root   69 2008-06-01 14:52 modules.ccwmap
-rw-r--r--  1 root root 390K 2008-06-01 14:52 modules.dep
-rw-r--r--  1 root root  813 2008-06-01 14:52 modules.ieee1394map
-rw-r--r--  1 root root  527 2008-06-01 14:52 modules.inputmap
-rw-r--r--  1 root root  18K 2008-06-01 14:52 modules.isapnpmap
-rw-r--r--  1 root root   74 2008-06-01 14:52 modules.ofmap
-rw-r--r--  1 root root 267K 2008-06-01 14:52 modules.pcimap
-rw-r--r--  1 root root 1.4K 2008-06-01 14:52 modules.seriomap
-rw-r--r--  1 root root 167K 2008-06-01 14:52 modules.symbols
-rw-r--r--  1 root root 470K 2008-06-01 14:52 modules.usbmap
drwxr-xr-x 10 root root 4.0K 2008-06-01 14:36 ubuntu
drwxr-xr-x  2 root root  380 2008-06-06 03:43 volatile
miickee@miickee-gutsy:/lib/modules/2.6.22-14-generic$ 


```
I need DirectPlay so I can play older games over the net/lan. Anyone who can help with this method, or has another method, I'll appreciate it a lot.

Thanks in advance

miickee

---

