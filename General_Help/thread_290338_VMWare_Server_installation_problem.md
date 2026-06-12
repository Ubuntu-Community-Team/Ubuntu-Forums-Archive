---
title: "VMWare Server installation problem"
date: 2006-11-01
forum: General Help
---

### Post by jrohde on 2006-11-01
Hi

I have just installed Edgy 64bit, and I'm now trying to install VMWare Server, following the direction in [this]("http://www.howtoforge.com/ubuntu_vmware_server") page.

But I get this error: 

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number 990A0-YPJ4C-23110-xxxxx is invalid.

The serial number is copy/pasted from VMware's home page.

Have you heard abut this problem and do you know a solution/workaround?

Thanks,

Jakob

---

### Post by tzulberti on 2006-11-01
To enter the code, you must be using "sudo vmware" or "sudo vmware-confiig.pl". 

Try not to enter the code when you are configurating vmware, but once you could open it in the X.

---

### Post by jrohde on 2006-11-01
Hi tzulberti,

When I try to start VMWare using "sudo vmware", I get this:

/usr/lib/vmware/bin/vmware: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

So libX11.so.6 is still causing trouble. 

libX1.so.6 does exist:

ls -al /usr/lib/libX11* result in:

-rw-r--r-- 1 root root 1688244 2006-10-20 12:42 /usr/lib/libX11.a
lrwxrwxrwx 1 root root      15 2006-11-01 09:36 /usr/lib/libX11.so -> libX11.so.6.2.0
lrwxrwxrwx 1 root root      15 2006-11-01 09:50 /usr/lib/libX11.so.6 -> libX11.so.6.2.0
-rw-r--r-- 1 root root  909416 2006-10-20 12:42 /usr/lib/libX11.so.6.2.0


Jakob

---

