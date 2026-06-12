---
title: "Where did my drives go?"
date: 2007-12-23
forum: General Help
---

### Post by smithit on 2007-12-23
I had 2 drives before, they were C: (220 GB) and D: (9 GB).

I have decided to use Ubuntu because I was not satisfied with Windows Vista, so I reformatted both my drives then installed Ubuntu. Everything went smooth but when I go to "Computer" I don't see my two drives anymore! 

Can anyone please help?

---

### Post by LaRoza on 2007-12-23
> **smithit said:**
> I had 2 drives before, they were C: (220 GB) and D: (9 GB).

I have decided to use Ubuntu because I was not satisfied with Windows Vista, so I reformatted both my drives then installed Ubuntu. Everything went smooth but when I go to "Computer" I don't see my two drives anymore! 

Can anyone please help?

C: and D: are most likely partitions, and when you installed, you repartitioned and formated the hard disk.

Did you intend to dual boot?

The total space available should be the same, minus the swap space.

(If you chose to use the entire drive, you will have two partitions, on large one and one small one)

---

### Post by CCNA_student on 2007-12-23
Those are partitions on the same hard drive right? If so you probably formatted them. How did you tell Ubuntu to format the partitions when you were installing?

      Sin Cere,

      CCNA

---

### Post by smithit on 2007-12-23
No, I reformatted it (I used to the Windows Vista installation disk to reformat which deletes all data on hard drives including Windows Vista OS)

then I booted up and installed Ubuntu. Everything works fine but I am wondering where my hard drives went?

---

### Post by fedex1993 on 2007-12-23
There is not such thing inside of linux as D: C:. One linux there is one Big partition called ext3 and probley / which means that the main partition where everything is saved. There is also a swap partition which is like i dont know yet but still trying to find that out. If you inteded to do a dual boot than i would look up a guide on te forums

---

### Post by smithit on 2007-12-23
> **CCNA_student said:**
> Those are partitions on the same hard drive right? If so you probably formatted them. How did you tell Ubuntu to format the partitions when you were installing?

      Sin Cere,

      CCNA

I don't know, I just chose the already-ticked one

---

### Post by LaRoza on 2007-12-23
> **smithit said:**
> No, I reformatted it (I used to the Windows Vista installation disk to reformat which deletes all data on hard drives including Windows Vista OS)

then I booted up and installed Ubuntu. Everything works fine but I am wondering where my hard drives went?

You have one hard disk, according to the information given.

The C: and D: drives in Windows were partitions, not actual drives. 

When you installed Ubuntu, you will have 2 partitions, but only one can be used for data, the other is a swap partitions, like the Windows page file.

Right Click Computer->Filesystem and see the size, it should be almost the size of the drive you have. (Minus the swap partition)

---

### Post by smithit on 2007-12-23
> **LaRoza said:**
> You have one hard disk, according to the information given.

The C: and D: drives in Windows were partitions, not actual drives. 

When you installed Ubuntu, you will have 2 partitions, but only one can be used for data, the other is a swap partitions, like the Windows page file.

Right Click Computer->Filesystem and see the size, it should be almost the size of the drive you have. (Minus the swap partition)

Okay, I did that and it seems to be about the size of C: partition

But what about my 9 GB D: partition?

---

### Post by LaRoza on 2007-12-23
> **smithit said:**
> Okay, I did that and it seems to be about the size of C: partition

But what about my 9 GB D: partition?

That was the recovery partition (unless you created it).

---

### Post by zetetic on 2007-12-23
> **smithit said:**
> I had 2 drives before, they were C: (220 GB) and 
D: (9 GB).

I have decided to use Ubuntu because I was not satisfied with Windows Vista, so I reformatted both my drives then installed Ubuntu. Everything went smooth but when I go to "Computer" I don't see my two drives anymore! 

Can anyone please help?

In Linux a partition is just a file. So C: and D: are just files. Look in /dev.

This is very basic knowledge. Before installing Linux, you should have read, among other things, some documents about Linux file system structure and disk partitioning!

zetetic

---

### Post by LaRoza on 2007-12-23
> **zetetic said:**
> In Linux a partition is just a file. So C: and D: are just files. Look in /dev.

This is very basic knowledge. Before installing Linux, you should have read, among other things, some documents about Linux file system structure and disk partitioning!


No, C: and D: don't exist anymore. The post chose to use the entire disk, so they were both wiped.

It isn't basic knowledge for one who is new to Linux, and there is nothing wrong with not doing a lot of research before moving.

---

### Post by smithit on 2007-12-23
Okay, thanks for the help guys :)

---

### Post by LaRoza on 2007-12-24
> **smithit said:**
> Okay, thanks for the help guys :)

No problem. You'll get used to the Linux way of doing things in no time.

(Mark this thread as solved, Thread Tools->Solved)

---

