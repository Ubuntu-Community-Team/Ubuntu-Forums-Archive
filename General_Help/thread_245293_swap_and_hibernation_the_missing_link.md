---
title: "swap and hibernation: the missing link?"
date: 2006-08-27
forum: General Help
---

### Post by roger64 on 2006-08-27
There must be somewhere in a plain Dapper standard installation a line of command within some /etc config file which designate the swap partition to use in hibernation mode.

I would like to know where. Rationale: I have my root partition on a primary partition and my swap on a logic volume in an extended partition. If  I modify within /etc/fstab the name of the swap partition (ex: sda6 becoming sda8), hibernation is not working anymore. 

Now, I avoid this by taking care of keeping the same swap number. I think it would be more comfortable to know how it works and tell Ubuntu which swap to use. 

Any tip where I could find this missing link? 
Thanks for help. It's not menu.lst from Grub (I don't use suspend2) :-k

---

### Post by roger64 on 2006-08-29
well, 
nobody knows about this?
:(

---

