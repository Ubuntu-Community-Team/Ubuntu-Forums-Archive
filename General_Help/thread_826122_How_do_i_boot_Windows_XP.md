---
title: "How do i boot Windows XP?"
date: 2008-06-11
forum: General Help
---

### Post by citricsquid on 2008-06-11
So i just formatted my HDD so i could do a fresh install of XP and Ubuntu.

I got through XP install and was running perfectly, exactly how i liked it, then i grabbed my ubuntu disk and went through the ubuntu setup.

I found a post when i was running XP about have to get my wusb54gs working with linux, which is how i am connected now.

Anyway, my question;
How do i get back to XP? I have programs i need to use that only run on XP....

It's definitely still installed, i can see the partition showing in Ubuntu file manager thingy, all the stuff i added is there.

So yeah, when i boot GRUB only shows Ubuntu, no XP :(

---

### Post by logos34 on 2008-06-11
gksudo gedit /boot/grub/menu.lst

copy the sample windows stanza near the top to the very bottom and take out the hash (#) marks.  It will show up on grub menu when you reboot

---

### Post by citricsquid on 2008-06-11
So i copied the example and did;

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

Right? Wrong?
I really don't want to go ahead with it incase it's wrong...
I think i need to put in the partition info for Windows?

Is sda2 btw.

---

### Post by logos34 on 2008-06-11
> **citricsquid said:**
> 
Is sda2 btw.

in that case, then

> root (hd0,**1**)

---

### Post by citricsquid on 2008-06-11
I'm really not very good at this, can you give me a "step by step" or the complete code?

title Windows XP
root (hd0,1)
makeactive
chainloader +1

Doesn't work, i know why; I need to specify the location of XP right?
How? :)

---

### Post by logos34 on 2008-06-11
boot from the ubuntu live cd and run 

sudo fdisk -l

post it.

You say XP is the second partition, sda2.  so (hd0,1) should work (that's the bios address/location)

---

