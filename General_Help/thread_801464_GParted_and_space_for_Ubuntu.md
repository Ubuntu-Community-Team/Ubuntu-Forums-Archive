---
title: "GParted and space for Ubuntu"
date: 2008-05-20
forum: General Help
---

### Post by Amnesia180 on 2008-05-20
Hi All,

I have just downloaded GParted and i want to put unallocated space onto my sda2 folder.

How do I go about doing this?

I have included a copy of what my partitions look like this far... can you suggest any other way of cleaning up?

[IMG]http://www.dan-taylor.co.uk/images/Screenshot.png[/IMG]

Thanks,
Amnesia

---

### Post by Amnesia180 on 2008-05-21
bump?

---

### Post by forestpixie on 2008-05-21
You need to resize the extended partition so that it doesn't include the unallocated space, then you should be able to move the unallocated space after sda2 and resize sda2 to include it.

You can try using the partition editor in the buntu livecd or use a gparted or partedmagic livecd. In those cases download the appropriate ios and burn as an image, then you can boot with it.
[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by housam on 2008-05-21
If you downloaded the newer version of Gparted , then the following steps should work without troubles. :

- resize ubuntu partition to occupy the all the unallocated space.
- grab the front end of that partition to leave an unallocated space from that side.
- grab the front end of the extended partition to leave the unallocated space out of it .
- resize the sda2 to have this unallocated space within it.

[COLOR="Red"]WARNING : THIS PROCESS WILL TAKE A VERY LONG TIME .[/COLOR]

Another solution : 
- Using Gparted , Delete the extended partition.
- create a smaller one leaving an unallocated space  just behind sda2.
- add this unallocated space to sda2 by grabing the aft end.
- repartition the extended partition to root ( / ) and swap.
- reinstall ubuntu.
-

---

### Post by Amnesia180 on 2008-05-21
Thanks for your input,

So, are you saying I have to use the live CD instead of the g parted that I got from the ubuntu terminal?

I am not infront of my linux until later on so I will give it a go then.

Edit: When you say "Grab" do you mean, literally grab the images?
And how do I chose where to leave the unallocated space?

---

### Post by housam on 2008-05-21
> **Amnesia180 said:**
> 

Edit: When you say "Grab" do you mean, literally grab the images?
And how do I chose where to leave the unallocated space?

Yes. the edge of the partitions.
By choosing front end / aft end of the partition edges.

---

### Post by forestpixie on 2008-05-21
You have to use a livecd of some sort as you can't work on mounted partitions - hence the key symbol.

---

