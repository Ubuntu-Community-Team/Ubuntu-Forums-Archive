---
title: "Move unallocated space into logical partition"
date: 2013-02-15
forum: General Help
---

### Post by nate7 on 2013-02-15
Hi, I really want more space in my home partition of ubuntu, but i don't know how to do that. I already have 10gb of unallocated space which i've freed. But i just want to know how do i extend the home partition by using up the unallocated space. 

Thanks. 

Screenshot: [http://i.imgur.com/bORP2u4.png](http://i.imgur.com/bORP2u4.png)
Screenshot from within ubuntu (not on live cd): [http://i.imgur.com/2lR2CSN.png](http://i.imgur.com/2lR2CSN.png)

EDIT: Sorry this should be in Installation & Upgrades

---

### Post by nate7 on 2013-02-15
I've read around places, and i think i need to boot from the live CD, use gparted on there, and click the resize on sda7, correct?

---

### Post by Mark Phelps on 2013-02-15
> **nate7 said:**
> I've read around places, and i think i need to boot from the live CD, use gparted on there, and click the resize on sda7, correct?

NO -- presuming that what you really want to do is move the 10GB of Unallocated space (adjacent to sda2) into one of your Linux partitions.

What you will have to do is expand the partition you want to take up the space -- but you can only do that when the unallocated space is adjacent to the partition itself.

In this case, you would have to do the following:
1) Expand sda4 to absorb the unallocated space
2) Move sda5 to the left
3) Move sda6 to the left
4) Expand sda7 to absorb the unallocated space

You WOULD have to do this from a CD or USB because you can't mess with partitions that are in use.

---

### Post by Bashing-om on 2013-02-15
nate7; Hi !

Not yet - >"and click the resize on sda7, correct?" In your partition configuration, it is a bit more complex. Your sda7 (home) is a logical partition inside of the extended partition.

In the operation you are contemplating the extended partition will have to be enlarged prior to enlarging the sda7 partition .

Never having done this myself I do not know what will result in arbitrarily enlarging the extended partition in relation the those logical partitions. While waiting for wiser heads to advise; read up on GParted:
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)
in the page's search box enter the search term "gparted" -with out the quotes-.

[INDENT]a learning process

[/INDENT]

---

### Post by nate7 on 2013-02-15
@Mark

So would i do this? [http://i.imgur.com/bG40T4v.png](http://i.imgur.com/bG40T4v.png)

I think its everything you said

---

### Post by Impavidus on 2013-02-15
Seems OK. I usually do this one step at a time instead of scheduling all at once, but this should work. Not that I often change partitions.

Do you have backups of your files? If there's a power failure while changing partitions you can loose data.

---

