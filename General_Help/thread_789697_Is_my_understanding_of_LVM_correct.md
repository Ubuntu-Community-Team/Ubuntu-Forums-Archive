---
title: "Is my understanding of LVM correct?"
date: 2008-05-10
forum: General Help
---

### Post by Jordanwb on 2008-05-10
I was installing 8.04 Server onto this old computer (using Alternate installer) and when I got to the screen about partitioning I saw two options:

Set up LVM (something like that)
Set up Encrypted LVM

So I was wondering "What's LVM?" so I went to Wikipedia, searched LVM, clicked on the one regarding to linux and I started reading; but I don't understand all of it. So what I'd like is to confirm my understanding of LVM:

LVM is like RAID in that it allows you to span data across multiple hard drives, or mirror the contents of one drive onto another without the need of a RAID controller.

Thanks.

BTW: You'll probably see me asking a lot of questions about Linux/Ubuntu because I like to understand and learn about what I'm using.

---

### Post by Monicker on 2008-05-10
LVM does not offer redundancy as does RAID.  Its a way of splitting and combining drives and partitions that allows you to more easily add/move/reduce storage capacity.

So that if you had a volume group which was mounted as /home that was getting full for example, you could throw in another drive, and extend the size of that volume group to gain extra space.

---

### Post by tamoneya on 2008-05-10
it allows you to easily get the benefits of RAID 0 and/or RAID 1(mirroring and striping).  YOu cannot however do RAID5 parity.

---

### Post by Jordanwb on 2008-05-10
> **Monicker said:**
> that allows you to more easily add/move/reduce storage capacity.

Why would I want less storage capacity? :confused:

> **tamoneya said:**
> it allows you to easily get the benefits of RAID 0 and/or RAID 1(mirroring and striping).  YOu cannot however do RAID5 parity.

It seems that my understanding of LVM is correct.

---

### Post by Monicker on 2008-05-10
> **Jordanwb said:**
> Why would I want less storage capacity? :confused:

.

There could be instances where you want to take space from one volume group and give it to another which needs it more.  Reduce one volume group, extend the other.

---

### Post by Jordanwb on 2008-05-10
Ahh yes I didn't think of that. But my understanding of LVM is correct to an extent?

---

### Post by Monicker on 2008-05-10
> **Jordanwb said:**
> Ahh yes I didn't think of that. But my understanding of LVM is correct to an extent?

Yes, I didn't think it had raid like capabilities, but after digging around some I see that in fact that is true.  I've only dealt with LVMs a little;  Fedora and RHEL use LVMs by default during an install.

---

### Post by Jordanwb on 2008-05-10
All right cool. Thanks.

---

### Post by _sAm_ on 2008-05-10
And you can also add LVM on top of sw RAID.

---

### Post by Jordanwb on 2008-05-11
In my computer I have two Maxtor hard drives (both 40 GB) I set up Ubuntu Server with LVM and currently one hard drive is in the Logical volumn. How do I add the other?

---

