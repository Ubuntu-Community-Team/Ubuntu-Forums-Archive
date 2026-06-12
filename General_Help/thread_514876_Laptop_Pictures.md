---
title: "Laptop Pictures"
date: 2007-08-01
forum: General Help
---

### Post by richd4567 on 2007-08-01
Hi There 

Fist time I've used Linux, Ubuntu or a  forum, please forgive my ignorance.

I installed a copy of Ubuntu 5.04 on an old laptop that was gathering dust so we could use it to download pictures to when on holiday.  This worked after a fashion and although is was extremely slow it did the job.

Problem is I can't get the pictures back off it, it no longer recognizes USB and I've tried all the solutions I can find for this to no avail.

I now realize from reading the forums the machine is too weak for the OS I''ve used.  Its a Packard Bell easy-one with 60mb of Ram, 6 GB HDD and a 500mhz processor.

Any help would be greatly appreciated.

Best regards

Rich

---

### Post by ddrichardson on 2007-08-01
Use a minimal live cd distro that supports USB to get them off - try [Damn Small Linux]("http://damnsmalllinux.org/").

---

### Post by notwen on 2007-08-01
Yes, I'd recommend DSL for your laptop, it should run pretty good on your laptop's specs.  As far as getting the pictures off I'd recommend possibly emailing them to yourself(perhaps a gmail account) and then opening up said email account on another PC.  Good luck. =]

---

### Post by richd4567 on 2007-08-01
Thank you ddrichardson and notwen for your prompt replies, will try your ideas tonight

---

### Post by richd4567 on 2007-08-01
Hi Guys

I've managed to boot from DSL CD, I've never seen this old caravan step move so fast!  Once i get the pictures off will be using this.  

How do I acess the HDD and the USB in DSL?  I' had a good look round the DSL wiki and can't find what I need.

When i boot into Ubuntu the pictures are still there.

Thanks for the help

---

### Post by ddrichardson on 2007-08-01
I imagine they'll be /dev/sda1 or 2 you'll need to manually mount them, eg 1st ide drive (ext2):

```
sudo mount /dev/hda1 /mnt/hdd
```

Remember to create the /mnt/hdd directory first.

---

### Post by richd4567 on 2007-08-02
Thank you ddrichardson, all 400 2mb  pictures recovered!

I may even be able to make use of this old laptop with DSL.

Best regards

Rich

---

### Post by ddrichardson on 2007-08-02
Cheers. DSL is pretty good. I have it running on an old Pentium 133, believe it or not.

---

