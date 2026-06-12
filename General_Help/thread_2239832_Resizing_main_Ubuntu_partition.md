---
title: "Resizing main Ubuntu partition"
date: 2014-08-16
forum: General Help
---

### Post by veddox on 2014-08-16
Hello everyone,

I would like to install Arch as a third system on my laptop, but before I mess up my current working system, I have a question. Right now, my hard drive has three partitions, one for Windows, one for data, and one for Ubuntu. The one with the most space to spare is the Ubuntu partition, so I would like to resize this and then use the left over space to create a new Arch partition. Is it possible just to boot up with a live CD, use GParted to do the resizing, and then go ahead with the installation? Or will that mess up/delete my Ubuntu install? Is there anything I need to watch out for?

Thanks in advance! :-)

---

### Post by em3raldxiii on 2014-08-16
Yes, your solution will work fine, but **you must back up all data that you are afraid to lose** any time you manipulate partitions on a physical disk.  It's standard procedure, but I've seen it happen in the past where a simple resize of a few GB results in corruption in other partitions on the disk.  Also note that you probably have a /swap partition - that one can remain the same for both Ubuntu and for Arch.

---

### Post by veddox on 2014-08-17
OK, thanks, resizing worked without a problem (and yes, I did backup before committing :-) ).

---

### Post by em3raldxiii on 2014-08-17
Awesome, I am glad it went well. :D

---

