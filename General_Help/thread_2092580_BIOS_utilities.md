---
title: "BIOS utilities?"
date: 2012-12-08
forum: General Help
---

### Post by mrmezaiii on 2012-12-08
This is sort of a hardware question, but I didn't really think of another place for it on an Ubuntu Forum. 

I use a laptop, how can I flash my BIOS from within the Ubuntu 12.10 OS?

It's a Toshiba machine using an American Megatrends BIOS version (1.20)

---

### Post by offgridguy on 2012-12-08
> **mrmezaiii said:**
> This is sort of a hardware question, but I didn't really think of another place for it on an Ubuntu Forum. 

I use a laptop, how can I flash my BIOS from within the Ubuntu 12.10 OS?

It's a Toshiba machine using an American Megatrends BIOS version (1.20)
The BIOS as i know it, is accessed prior to and seperate from any OS.

---

### Post by Mark Phelps on 2012-12-08
You need to check the website for your motherboard.  Sometimes they offer ISOs that you can burn to CD and boot from those.  Also, some motherboards have an option to boot using a special key sequence using a USB stick and you can flash from that.

---

### Post by grahammechanical on 2012-12-08
My motherboard maker supplied with the motherboard a CD with various utilities that run under a Microsoft operating system, including a utility for flashing the BIOS. But nothing for using under the Linux OS and certainly nothing specific to Ubuntu.

I do have a method for flashing the BIOS from the BIOS setup program and  using a DOS utility on a floppy disc. May be something similar is available for you.

Manufacturers do not support Linux to the extent that we would like. 

Regards.

---

### Post by Cheesemill on 2012-12-08
You can't do it from Ubuntu but there is another way. Nearly all motherboard manufacturers still provide a DOS flashing application and the BIOS images for download.

I just use [Unetbootin]("apt://unetbootin") to create a FreeDOS bootable USB stick and then copy the downloaded files onto it. Just boot from the USB and run the flashing command, there should be specific documentation with the downloads.

---

