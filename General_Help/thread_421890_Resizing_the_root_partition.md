---
title: "Resizing the root partition?"
date: 2007-04-24
forum: General Help
---

### Post by Olmen on 2007-04-24
Hi.

I recently installed Ubuntu on this machine and I'm in love. So much in fact that I'd like to remove the previous vista install altogether. The current setup is 10gb ext, 512 mb swap and  70 ntfs.

I'd like to avoid clean installing Ubuntu from scratch because I've already made a lot of changes and installed a lot of apps... What i'd like to do is to format the ntfs partition and then resize my the root ext partition so that it takes up the whole disk (minus the swap of course). Also, it'd perhaps be good to make the swap partition a bit larger (read somehere that it should be about 1.5 times the RAM) What's the safest way to do that?

Could this be done by using the partitioning tool Ubuntu offers on the liveCD or is there a better / safer / smarter way to approach this? Or is it even possible :P?

Any advice would be greatly appreciated!

---

### Post by lakersforce on 2007-04-24
I know this is not what you want to hear, but I think the best sollution would be a clean install.

And perhaps you should set up an extra partition for back-up purposes, so you can keep some of your most important data whenever you need to do a clean install.

---

### Post by tarpon_bill on 2007-04-24
Yep on the new install being the best way. It is quite complicated, and often not successful, to resize root partitions. It never seems to work for me, it does work for other partitions, sometimes. Best to do a good job with sizing partitions at the beginning.

---

### Post by dcstar on 2007-04-24
> **Olmen said:**
> 
.......
Also, it'd perhaps be good to make the swap partition a bit larger (read somehere that it should be about 1.5 times the RAM) What's the safest way to do that?


Do not take much (if any) notice about how big Swap partitions should or shouldn't be. These things were written many years ago when most systems had little (compared to these days) RAM and relied on Virtual Memory far (far) more heavily.

If you have over 512MB of RAM, and don't run large resource intensive apps simultaneously, then you can have minimal Swap.

Any sort of "1.5 times RAM" thinking is just outdated dogma that serves more to confuse people rather than provide any useful service to them these days.

---

### Post by GuitarRocker2562 on 2007-04-24
idk if it will work right, but could you just convert the ntfs to a home partition and like do something so ubuntu sees it as /home ?

---

### Post by Azakus on 2007-04-24
You can try the Gparted Live CD (I've used it and it works very well).
You can nondestructively resize your partitions with a very easy GUI.
You have to use a live cd because you can't change a mounted partition
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Olmen on 2007-04-24
> **Azakus said:**
> You can try the Gparted Live CD (I've used it and it works very well).
You can nondestructively resize your partitions with a very easy GUI.
You have to use a live cd because you can't change a mounted partition
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Thanks for the tip. I tried Gparted and it worked like a charm!

---

