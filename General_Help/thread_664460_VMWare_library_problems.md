---
title: "VMWare library problems"
date: 2008-01-11
forum: General Help
---

### Post by Malakim on 2008-01-11
Hi all!

I'm having some issues getting VMWare Workstation running on Kubuntu 7.10. Maybe someone here can point me in the right direction. My problem is as follows:
```

When running vmware-config.pl I get the message:
The following libraries could not be found on your system:
libX11.so.6
libXtst.so.6
libXext.so.6
libXrender.so.1
libz.so.1
You will need to install these manually before you can run VMware Workstation.

```

However, when I go look in /usr/lib all of those libraries are there.

The VMWare kernel modules all build without any problems.

This is on an Athlon64 machine running 64-bit Kubuntu.

Thanks!

Regards,
Markus Svensson

---

### Post by Malakim on 2008-01-11
I got a response from someone over at the VMWare forums who claims that I need the 32-bit libraries as well.

Is it possible to use 32-bit librareis on a 64-bit install of Kubuntu? If it's possible, how do I do it?

Regards,
Markus Svensson

---

### Post by narraal on 2008-06-21
Have a look at Cappy's post here

[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

It works oh so nice :)

Hopefully his post can be moved into the FAQ's of the Ubuntu forum.

---

