---
title: "Problem with new Partition"
date: 2006-10-24
forum: General Help
---

### Post by IOwnUrMom on 2006-10-24
So...

I made 4 partitions from my 40 GB disk...

A 20 GB NTFS
A 1 GB SWAP
And 2x 5 GB Ext3 Part.

Their Order:

|------------------------------||---------||-----------||----|
Windows                         Empty Ext3  Ubuntu       Swap
Now, I installed Ubuntu on one partition and I decided i needed more space, so I downloaded GParted and ran the live Disk. Then I deleted the empty partition and I resized the Ubuntu partition to the left. (I probobly should have moved it then expanded it to the right... oh well :( ). So, I go and start loading ubuntu from GRUB and it goes through and Stops in "Checking File Systems" and it freaks out and tells me all about the partition I deleted... And it won't load... I have important stuff there, so I need it back alive....


Any help?

Nick
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by IOwnUrMom on 2006-10-24
Can anyone help me?

Ahhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by IOwnUrMom on 2006-10-25
Help??

---

### Post by CatKiller on 2006-10-25
> **IOwnUrMom said:**
> Then I **deleted the empty partition** and I resized the Ubuntu partition to the left.

That's the bit that's messed you up. GRUB is trying to boot from the third partition on the disc, which is now your swap partition. Have a look around for instructions to reconfigure GRUB - I've not done it, so I can't tell you exactly how.

Good luck!

---

