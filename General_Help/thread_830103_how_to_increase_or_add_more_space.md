---
title: "how to increase or add more space?"
date: 2008-06-15
forum: General Help
---

### Post by Ginoxy on 2008-06-15
hello, when i first install wubi i gave it 8G but now i need to increase it , how ?

---

### Post by prshah on 2008-06-15
> **Ginoxy said:**
> hello, when i first install wubi i gave it 8G but now i need to increase it , how ?

Take a look at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

See the section on "Resizing virtual disks using LVPM"

---

### Post by Ginoxy on 2008-06-15
ok what the difference between resize home or root ?

---

### Post by prshah on 2008-06-15
> **Ginoxy said:**
> ok what the difference between resize home or root ?

root ("/") is where all directories (including home) are attached. However, any directory can be physically present on any device.

For your purposes, a root partition of 10Gb is ample, if your "/home" partition is separate. Give your root partition a size of 10Gb, and the maximum available to "/home"

If you don't have separate "/" and "/home" partitions, then calculate the new size as this: 10Gb for root, and add to that how many ever Gb you need for your home partition.

---

### Post by Ginoxy on 2008-06-15
still i dont get it ! when i installed wubi at the first time it did not ask me for this i just choosed 8G but now i need to increase to 12 or 14G so is it root or home?

---

### Post by ago on 2008-06-16
home contains only user documents, if are out of space because of video files in your user folder then you want to increase the size home. home can be inside of the root device or on a separate volume.

usr contains most installed programs, so if you are out of space because you installed tons of programs you want to increase the size of usr. usr can be inside of the root device or on a separate volume.

root contains everything which is not explicitly setup on a different device. I.E. at the beginning root includes both home and usr.

---

### Post by prshah on 2008-06-16
> **Ginoxy said:**
> still i dont get it ! when i installed wubi at the first time it did not ask me for this i just choosed 8G but now i need to increase to 12 or 14G so is it root or home?

Increase in home. If you dont have home, then increase in root.

---

### Post by Ginoxy on 2008-06-16
This is what im talking about 

[ATTACH]74217[/ATTACH]

so is it possible to add the additional space from windows with out the program that you mentioned before? 

Thanks in advance

Oh by the way im using (H) drive for Wubi

---

### Post by Ginoxy on 2008-06-26
Reminder

---

### Post by prshah on 2008-06-27
> **Ginoxy said:**
> 
so is it possible to add the additional space from windows with out the program that you mentioned before? 



You cannot do this from Windows (Add space to your Wubi-Ubuntu install). And you need to resize root, if you have just selected a single 8Gb during installation.

Here's how I see it; you will need to use LVPM to copy/move all your data from your current (h:) wubi to a new (k: - 99% free space) wubi; give the new size as 22000Mb. LVPM will create a new Wubi disk file, copy your data from the current (h:) to the new (k:) drive, then give you instructions as to what changes to make in Windows to activate your new (expanded) wubi disk. Note that in Ubuntu, h: drive will probably be /dev/sdb2 and k: will be /dev/sdb3. You will not see h: and k: in Ubuntu; I use it here so that you are comfortable with convention.

CAUTION: I would advise you to be careful when using LVPM; if you are not careful and/or make error during partition selection you can wipe out your existing data on one or more partitions/disks.

Since you seem to be uncomfortable in this area, can you not seek the firsthand support of a knowledgeable friend?

---

### Post by Ginoxy on 2008-06-27
I believe that remove wubi and install it again would be much better ? what do you think?

---

### Post by prshah on 2008-06-27
> **Ginoxy said:**
> I believe that remove wubi and install it again would be much better ? what do you think?

Yes much better- if you don't care about any of your ubuntu data/settings.

---

