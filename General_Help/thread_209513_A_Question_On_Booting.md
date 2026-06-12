---
title: "A Question On Booting"
date: 2006-07-05
forum: General Help
---

### Post by _bRAD_ on 2006-07-05
I'd like to boot my ubuntu system (v5.04) using a CD only.  No hard drive (well, it would have one, but it wouldn't be connected or active).  I've got ubuntu installed to the computer's hard drive right now, all the bells and whistles and whatnot.  But what I'd like is a list of the files that would be required to make a bootable CD.

The reason I want to do this is that this Linux box is going to be a hardware firewall between my phone company and my two other computers.  But if I have it boot from CD, then any would-be script kiddie that gets in can't change anything, thus making it secure.  Very secure.

So if anyone can help me out and provide a list of the files/directories that would be required to make a bootable CD for ubuntu with NOTHING more than needed (just the kernel, for example, I shouldn't need a desktop, should I?), I'd be very greatful.  Thank you, in advance.

- bRAD

---

### Post by Mike_N on 2006-07-05
So yer trying to make a Firewall/Router eh? Try Smoothwall or m00nwall... Mike

---

### Post by _bRAD_ on 2006-07-05
I'll look into those, thank you.  But I'd kind of like to stick with ubuntu if I can, but if not, I guess I'll have to use something else, huh?  Oh well.

And yes, I'm making a firewall. ;)

- bRAD

---

### Post by lamego on 2006-07-05
Thats a very dumb idea for several reasons:
1 - Having a read-only filesystem to boot from does not make your system safer, the configuration systems must be writeable for the system to work.
2 - The firewall is not just about protection but also aboud auditing, meaning you should keep the most possible detail abouting incoming connections for the case you have a security violation attempt. If you want a read-only system which will not keep logs then you are doomed.
3 - If you don't care about 1 and 2  and need a temporary firewall you can just use a plain Ubuntu Live CD .

---

