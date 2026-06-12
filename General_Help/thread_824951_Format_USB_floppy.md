---
title: "Format USB floppy"
date: 2008-06-10
forum: General Help
---

### Post by savsav on 2008-06-10
How do I format a floppy in an external USB floppy drive?

---

### Post by dudude on 2008-06-10
Download gparted from synaptic

Go to System->Administration->Partition Editor

You should be able to delete any partitions on the device.

---

### Post by savsav on 2008-06-10
So, there is no easy way to format a USB floppy in Linux, isn't there?

That's the feeling I'm getting after Googling this and reading about it online.

---

### Post by savsav on 2008-06-10
So, there is no easy way to format a USB floppy in Linux, isn't there?

That's the feeling I'm getting after Googling this and reading about it online.

---

### Post by fr3db3rt on 2008-06-18
> **savsav said:**
> So, there is no easy way to format a USB floppy in Linux, isn't there?

That's the feeling I'm getting after Googling this and reading about it online.
***mkdosfs /dev/sda***

or

***mkdosfs /dev/sda -I***

should do what you want.

If your floppy drive is not ***/dev/sda*** then find out with ***fdisk -l*** where your floppy drive belongs. You must have inserted any floppy disk in your floppy drive to do this.

Please let me (us) know if that works in Ubuntu, too!

Thanks,
fr3db3rt.

---

