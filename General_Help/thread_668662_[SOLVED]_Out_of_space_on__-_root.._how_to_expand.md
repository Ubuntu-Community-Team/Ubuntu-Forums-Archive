---
title: "[SOLVED] Out of space on / - root.. how to expand?"
date: 2008-01-15
forum: General Help
---

### Post by neptune on 2008-01-15
Hi,

Just realized that I'm completely out of space on root partition. I can't even run apt-get.

My root is formatted as ext3 4.6gb on /sda2

I have about 100gb of unallocated, empty space on this drive (and more space on second drive).

Is there any way to increase the root partition size without losing data or having to re-format/re-install??

I should have noticed this sooner but now I'm totally out of space.. 4kb left :(

Thanks!

---

### Post by AndyCooll on 2008-01-15
> **neptune said:**
> Hi,

Just realized that I'm completely out of space on root partition. I can't even run apt-get.

My root is formatted as ext3 4.6gb on /sda2

I have about 100gb of unallocated, empty space on this drive (and more space on second drive).

Is there any way to increase the root partition size without losing data or having to re-format/re-install??

I should have noticed this sooner but now I'm totally out of space.. 4kb left :(

Thanks!

You can do this by downloading the GParted Live CD. 

You may well be able to use the Ubuntu Live CD too (and then installing GParted). Since you are using the Live CD it will mean the root drive isn't mounted and hence can be resized.

Obviously, you should backup important stuff first.

:cool:

---

### Post by voteforpedro36 on 2008-01-15
I think (you may not want to try without somebody else agreeing, I could be wrong), you could install GParted. Use it to expand the current drive, and it won't damage anything else.

---

### Post by bodhi.zazen on 2008-01-15
> **AndyCooll said:**
> You can do this by downloading the GParted Live CD. 

You may well be able to use the Ubuntu Live CD too (and then installing GParted). Since you are using the Live CD it will mean the root drive isn't mounted and hence can be resized.

Obviously, you should backup important stuff first.

:cool:

Gparted is already included in the Ubuntu desktop CD. Now the gparted live CD is a nice tool, but it is not necessary to download and burn a new CD.

> **voteforpedro36 said:**
> I think (you may not want to try without somebody else agreeing, I could be wrong), you could install GParted. Use it to expand the current drive, and it won't damage anything else.

No, this will not work. You can not resize a mounted partition, thus to resize root ( / ) you need to boot a live CD.

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by voteforpedro36 on 2008-01-15
> **bodhi.zazen said:**
> Gparted is already included in the Ubuntu desktop CD. Now the gparted live CD is a nice tool, but it is not necessary to download and burn a new CD.



No, this will not work. You can not resize a mounted partition, thus to resize root ( / ) you need to boot a live CD.

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

This kind sir is correct.

---

### Post by neptune on 2008-01-15
Wow.. thanks for the quick replies folks!

Here's how my partitions look right now:
[IMG]http://neptune.page9.ca/Screenshot--dev-sda - GParted.png[/IMG]

Can I move the entire sda3 (extended) partition? I tried this but I was only able to expand it, not move it.

I'd have to shrink sda6 and move sda5, and then I think sda3 would be movable/shrinkable, right?

Then I could expand sda2 (root)?

I have the Ubuntu Live DVD as well as Knoppix Live CD; does Knoppix have a partition editor?

Thanks!

---

### Post by smartboyathome on 2008-01-15
Install GParted while the livecd is running from Getdeb.net (it is a newer version than what is on the livecd) and then you can move the extended partition to after the unallocated space and then you can expand your partition to include the unallocated space.

---

### Post by neptune on 2008-01-15
> **smartboyathome said:**
> Install GParted while the livecd is running from Getdeb.net (it is a newer version than what is on the livecd) and then you can move the extended partition to after the unallocated space and then you can expand your partition to include the unallocated space.
getdeb.net doesn't have any versions of gparted.

---

