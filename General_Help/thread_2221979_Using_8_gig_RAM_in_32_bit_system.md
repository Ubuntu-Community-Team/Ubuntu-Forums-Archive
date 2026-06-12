---
title: "Using 8 gig RAM in 32 bit system?"
date: 2014-05-04
forum: General Help
---

### Post by Autodave on 2014-05-04
I kinda remember seeing on here somewhere that there is a program to allow the 32 bit system to recognize and use more that the normal max of 3.5 gig.  Anyone know what that program is?

---

### Post by whitesmith on 2014-05-04
Theoretically the maximum RAM usable by any 32-bit system is 2**32 (4294967296 B = 4194304 KB = 4096 MB = 4 GB). Some of that is used by on-board cards, so the effective maximum tends to approach 3 GB from above. I don't know of any way to game those limitations. Back in the day when DOS programs were limited to 640 KB, an outfit named Phar-Lap came up with a trick using extended (expanded?) memory to lift the barrier in a manner of speaking, but that was a totally different situation.  Perhaps a hardware guy is lurking who knows something I don't. Cheers!

---

### Post by kc1di on 2014-05-04
any Ubuntu release after I believe it was 10.04 comes with a PAE kernel and will address more than 4 gigs already. only thing that would prevent that is if your processor is not PAE enabled.  But most of them in the last 10 years or so are. so you should not have any problems using 8 gigs of ram.

---

### Post by oldfred on 2014-05-04
But why 32 bit? Any system that supports 8GB of RAM should run 64 bit.

       Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)
[URL="https://help.ubuntu.com/community/PAE"]
https://help.ubuntu.com/community/PAE[/URL]


 Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by Impavidus on 2014-05-04
Apart from Xubuntu Precise 32 bit and maybe Lucid server edition (maybe forgetting one) all supported 'buntus come with PAE kernel nowadays. PAE allows the system to use up to 64GiB, but individual applications are still limited to 4GiB, so not very useful unless running load of small programs. You can better use 64 bit when going over 3GiB memory.

---

