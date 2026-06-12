---
title: "grub error 22 !!HELP!! PLEASE"
date: 2007-11-19
forum: General Help
---

### Post by Jason Weiss on 2007-11-19
Hi ppl, 

I just tried to delete one of my partitions of ubuntu, ( i had two partitions with 2 versions of ubuntu on them ie 1 on each)

I used gparted to delete on of the portions, now grub is angry with me and will not boot. 

it says: 
"Grub loading....
Error 22"
:confused:
Please help I just want to boot again

---

### Post by Thyme on 2007-11-19
Are you sure that you're trying to boot from the partition that you didn't delete? As far as I know, the "Error 22" is when the partition doesn't exist or grub can't find it.

You can also edit and play around with the grub entry and change the "/root" part to other partitions to see what the outcome is. "e" is to edit and "b" to boot the entry.

---

