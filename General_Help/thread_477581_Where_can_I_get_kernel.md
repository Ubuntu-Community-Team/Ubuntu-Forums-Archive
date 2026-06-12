---
title: "Where can I get kernel?"
date: 2007-06-18
forum: General Help
---

### Post by anaconda on 2007-06-18
I accidentally deleted the contents of "/boot" folder from my  Ubuntu Dapper (6.06)

So ofcourse it wont boot anymore.

Where can I get  initrd.img-2.6.15-27-386   and vmlinuz-2.6.15-27-386 (that is the version I had) and is that all that I need?  

I have a working grub, which boots to my feisty-partition.

---

### Post by srg84 on 2007-06-18
In synaptic search: "linux image" and in which have you installed already, right click reinstall.

It should create all the files again

---

### Post by aidanr on 2007-06-18
srg84, not much good if it won't boot, the vmlinuz file is in this package
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.50_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.50_i386.deb)

you can extract it and copy it over, the initrd i don't now though, maybe chroot and mkinitrd

---

### Post by srg84 on 2007-06-18
this package is in synaptic and can be reinstalled by that way.

---

### Post by anaconda on 2007-06-18
> **aidanr said:**
> srg84, not much good if it won't boot, the vmlinuz file is in this package
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.50_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.50_i386.deb)

you can extract it and copy it over, the initrd i don't now though, maybe chroot and mkinitrd

Thanks!
I downloaded it and extracted the vmlinuz-file. 

The initrd is more difficult, since I cant find mkinitrd-command in ubuntu? found info about mkinitrd with google, but it doesn't seem to be available in the repositories either?

any other way to create initrd?

And srg84 thanks for the help, but I cant use synaptic, because I cant boot to that system before I get this problem solved.  hmm..  execpt maybe I could boot with Dapper liveCD and copy its initrd to my dapper partition.... worth a try!  hope I can find the Dapper CD.

---

### Post by anaconda on 2007-06-18
Got it working.

copied the contents of /boot  folder from the liveCD and then booted the machine and installed a new kernel (using synaptic) 

Thanks!

---

