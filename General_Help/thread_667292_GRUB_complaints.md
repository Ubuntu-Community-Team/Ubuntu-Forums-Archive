---
title: "GRUB complaints"
date: 2008-01-14
forum: General Help
---

### Post by aitutaki on 2008-01-14
Hi all ,

I've installed Ubuntu Studio on an external hard drive, and I love it - it worked fine on the first pc i used. However, whenever I attempt to boot from the drive on the second PC, I get grub error 18. Is there anyway to create a /boot partition or otherwise get around the problem without having to reinstall and lose all my precious files?

The 2nd PCs specs:

plgpl-4 asus motherboard (recent, not an old board)
nvidia 7600GT
pent 4 3GHZ
audigy 2 sound card
1gb ram

Cheers for any help.

---

### Post by aitutaki on 2008-01-14
Anyone? 

That's a p4gpl-x motherboard, by the way. Typo.

Thanks for any help.

---

### Post by logos34 on 2008-01-14
Despite the 'error 18', I don't think this is a Bios limitation issue (you have a recent board).  

But that doesn't necessarily mean creating a separate /boot won't solve the problem.

Just one internal hard disk on each of the computers?

---

### Post by Tanker Bob on 2008-01-14
> **aitutaki said:**
> Anyone? 

That's a p4gpl-x motherboard, by the way. Typo.

Thanks for any help.
I recommend trying [Super Grub Disk](http://supergrub.forjamari.linex.org/). I had to use it several times to boot my system after setting up my RAID until I got fstab squared away. It has quite a few options, built-in help, and I found it very effective. It can even install or fix GRUB in the Master Boot Record if it somehow was erased, like if Windows overwrote the MBR.

Also, Googling on "GRUB Errors" will get you quite a bit of information from the net.

---

