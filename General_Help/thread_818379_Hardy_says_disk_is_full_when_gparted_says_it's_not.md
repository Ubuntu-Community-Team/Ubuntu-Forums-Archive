---
title: "Hardy says disk is full when gparted says it's not"
date: 2008-06-04
forum: General Help
---

### Post by TorchlightJay on 2008-06-04
Hello,
  So I am using Hardy Heron and I am trying to copy a file to one of my partitions but it keeps telling me that the disk is full. I opened gparted and got a different story. It appears I have 3 gigs left. The file i am trying to transfer is only 43 megs? Anyone know what can cause this?

---

### Post by leito666 on 2008-06-04
Can you paste the result of this:

```
df -h
```

---

### Post by TorchlightJay on 2008-06-04
Here is what it says about that particular partition

/dev/sda*             75G   71G  6.8M 100% /home/blah/mountpoint

---

### Post by philinux on 2008-06-04
Have a look at the file system tab with system monitor.

---

### Post by rraj.be on 2008-06-04
I think that there was something hiden inside like some system files.

And another questionis whether you are using a swap file or swap partition.

this may be due to your swap

---

### Post by TorchlightJay on 2008-06-04
I am using a swap partition.

---

### Post by rraj.be on 2008-06-04
Then just try to fix it manually by checking each drives.

Files ystem management in ubuntu is extremly powerfull that it makes error very very seldom

Hence check each directory size and add them and check whether something is hiden or not.

Some back up or temporary files may be there unknow to this.

To view hidden files select

```
View -> show hidden files
```

---

### Post by plucky on 2008-06-04
> /dev/sda* 75G 71G 6.8M 100% /home/blah/mountpoint


Don't forget approx 5% of the partition is reserved for root because of journalling.

It is not good to run a partition so full as it can cause fragmentation.

Either enlarge the partition or backup some files and make some space or it could cause other problems.


Good Luck

---

### Post by TorchlightJay on 2008-06-04
Is there a tool within ubuntu to take care of this problem or am I manually going to have to search for the hidden files in this partition? If there is a tool, great. If not, c'est la vie.

---

### Post by .nedberg on 2008-06-04
> **plucky said:**
> Don't forget approx 5% of the partition is reserved for root because of journalling.

It is not good to run a partition so full as it can cause fragmentation.

Either enlarge the partition or backup some files and make some space or it could cause other problems.


Good Luck

I would also think this is the reason!

---

### Post by rraj.be on 2008-06-05
I think there is no need for any extra packages.

[Actually i dont know whether its there or not.]


But enabling show hidden files itself shows you every thing that you need in that.

---

