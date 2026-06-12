---
title: "The Formatting Of External Hard Disk Drives For Backups."
date: 2013-01-19
forum: General Help
---

### Post by BlinkinCat on 2013-01-19
Hi all,

Up until now my backups have been hair raising to say the least - namely via flash drives and an external HD for my reasonably large video collection. The external HD is a Seagate with packaging nominating only Windows and partitioned in NTFS. There are five folders generally referring to Seagate with such names as setup.exe etc. The manual backup has worked quite well, my only needing one folder (Videos) joining the five Seagate folders.

I am now considering purchasing another external HD for backups, potentially via luckybackup or grsync. I anticipate that I will again be purchasing a Seagate Drive, that being the brand favoured by our local supplier. My questions therefore are -

Should I repartition the new Drive ? and if so in ext 4 ?
I assume repartitioning would erase all of the Seagate files and folders.

I apologize if these questions seem pretty basic, but after investing in a new HD I don't want to mess anything up. Any tips will be welcome.

Cheers - :)

---

### Post by Bucky Ball on 2013-01-19
Yes, reformatting the drive will erase everything.

---

### Post by BlinkinCat on 2013-01-19
> **Bucky Ball said:**
> Yes, reformatting the drive will erase everything.

Am I correct in assumimg this will be OK and choice could be ext 4 ?

Thanks for your lightning response by the way Bucky Ball - :p

---

### Post by Bucky Ball on 2013-01-19
Yes, you could create one large EXT4 partition_* if you are only intending to use this with Linux.*_ Remember, Windows will not recognise EXT* partitions. If you are intending to share between the two, use NTFS. 

Once your partition(s) are created, you can then create folders in there if you like. I would probably make one large extended partition and then create logical drives (partitions) in there. This would prevent the limitation of only being allowed four primary partitions on one physical drive, in case you ever want to go there. You can create as many logical partitions inside an extended as your hardware can handle (theoretically limitless number).

---

### Post by BlinkinCat on 2013-01-19
Thanks Bucky,

Yes I have only one Linux distribution.

I anticipate getting a 1 TB drive - perhaps I could divide that into one large partition for backups with two or perhaps three others - I can have a good think about it.

Thank you very much again Bucky, your input is much appreciated - I may leave the thread open for a little while but anticipate I will shortly mark as "Solved"

Cheers - :p

---

### Post by Bucky Ball on 2013-01-19
A pleasure. And as I say, an extended partition with logicals in there might be the safest. In future you might have call for a fifth partition and then you are stymied. 

But if you're confident you are never going to need more than four partitions on that drive, then primary partitions it is, go for it! Either/or.

Good luck with it. ;)

---

### Post by BlinkinCat on 2013-01-19
Hi again,

I just new it, I have another question - making the large extended partition, would I firstly create one sole ext 4 partition over the complete drive, and then use GParted to divide it up ? Creating "extended partitions" has always confused me.

---

### Post by Bucky Ball on 2013-01-19
Nope. You just create an extended partition, size it to use the entire drive, and you're away. Extended partitions are like containers for logical partitions, if that makes any sense. You can then create as many logical drives as you like in there. Extendeds are like empty space, but no limitation on the logicals you can shove in there (which overcomes the four primary partition limit to one physical drive).

Your machine will then see the logical drives as separate mini-drives if you like, inside the extended (but the extended doesn't actually show in a file manager as anything as it is, as I say, a container, not an actual 'partition'. It is a partitions to hold partitions!

Basically, the logicals are exactly the same as and behave the same as partitions.

Hope that helps ... ;)

---

### Post by BlinkinCat on 2013-01-19
> **Bucky Ball said:**
> 

Hope that helps ... ;)

Believe it or not Bucky it helps a lot - I just don't understand at what stage I will partition as ext 4 ? Bucky I promise I will go away if you could answer that question.

Many thanks for your responses - :p

Edit : - Am I missing a major point - perhaps I should be FORMATTING entire disk as ext 4 ?

---

### Post by Bashing-om on 2013-01-19
BlinkinCat; Hey !

This is the guide I prefer for a new hard drive:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Works great, not to hard to fill in the details - the guide is explicit for single partition but the hints for more partitions are good enough.
[INDENT]hth 

[/INDENT]

---

### Post by BlinkinCat on 2013-01-19
> **Bashing-om said:**
> BlinkinCat; Hey !

This is the guide I prefer for a new hard drive:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Works great, not to hard to fill in the details - the guide is explicit for single partition but the hints for more partitions are good enough.[INDENT]hth 

[/INDENT]

Thanks very much for your input Bashing-om  - :)

---

### Post by rawlins02 on 2013-01-19
> **BlinkinCat said:**
> Believe it or not Bucky it helps a lot - I just don't understand at what stage I will partition as ext 4 ? Bucky I promise I will go away if you could answer that question.

Many thanks for your responses - :p

Edit : - Am I missing a major point - perhaps I should be FORMATTING entire disk as ext 4 ?

You will format the drive soon after inserting the LiveCD and starting GParted. You should look over parts of the GParted tutorial:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

CAUTION: Be sure all data on disk has been backed up on another medium, as reformatting will erase all contents.

Yes you may format entire disk as ext4. GParted will allow you to set up primary or logical partitions in several formats. Suggest you look over the tutorial and post other questions as needed.

---

### Post by BlinkinCat on 2013-01-19
> **BlinkinCat said:**
> 
Edit : - Am I missing a major point - perhaps I should be FORMATTING entire disk as ext 4 ?

Must immediately duck out and purchase "Linux For Dummies" - I need it.

Will now mark as solved - ):P

Edit : - just ducked back to thank rawlins02 for his referral to what looks like a great tutorial.
Many apologies to Bucky Ball also.

---

### Post by Bucky Ball on 2013-01-19
You format the logical drives inside the extended partition as EXT4. The extended partition is not formatted as anything as it is a container only.

---

### Post by BlinkinCat on 2013-01-19
> **Bucky Ball said:**
> You format the logical drives inside the extended partition as EXT4. The extended partition is not formatted as anything as it is a container only.

Many thanks Bucky Ball - I have got it at last - :p

---

### Post by Bucky Ball on 2013-01-20
;)

---

