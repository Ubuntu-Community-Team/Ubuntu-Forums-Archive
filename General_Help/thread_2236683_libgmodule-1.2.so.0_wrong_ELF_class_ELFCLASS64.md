---
title: "libgmodule-1.2.so.0: wrong ELF class: ELFCLASS64"
date: 2014-07-28
forum: General Help
---

### Post by stefano91 on 2014-07-28
Hi everybody!

I was trying to install Cn3D a NCBI tool ([http://www.ncbi.nlm.nih.gov/Structure/CN3D/cn3dunix-4.1.shtml](http://www.ncbi.nlm.nih.gov/Structure/CN3D/cn3dunix-4.1.shtml)). Unfortunately when I launch it I get the following:

```

stefano@stefano-TravelMate:~/Cn3D-4.1$ ./Cn3D 
./Cn3D: error while loading shared libraries: libgmodule-1.2.so.0: wrong ELF class: ELFCLASS64

```

Before getting this I had trouble with another shared libray, the libgtk1.2 that I hardy solved.
But I cannot find this one in any other thread or in the web. How could I solve this?

Thanks!

---

### Post by steeldriver on 2014-07-28
It looks like you are trying to run it on a 64-bit platform, whereas the webpage you linked says it is only supports i386

You *may *be able to make it work by installing i386 versions of the relevant packages - the details of how will depend what version of Ubuntu you are running. Or you may want to look at installing a 32-bit system (perhaps as a VM) for this application.

---

### Post by stefano91 on 2014-07-28
ok! That's it! I did not noticed that! 
I think at this point another easy way could be to download the win version and run it with wine.
I'll put solved! 
Thank you!

---

