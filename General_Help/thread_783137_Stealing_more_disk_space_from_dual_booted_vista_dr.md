---
title: "Stealing more disk space from dual booted vista drive"
date: 2008-05-05
forum: General Help
---

### Post by dazzlindonna on 2008-05-05
I'm a recent convert to Ubuntu (totally loving it).  I installed 8.04 as a dual boot with Vista.  Everything is working well.  No problems.  Life is good.  However, I initially only allocated 40 gigs of space to Ubuntu, leaving 200 gigs of free space for Vista.  (I thought I'd play with ubuntu and then return to Vista - oh how wrong I was).  And although I've got it set up so that Ubuntu can read and write to the Vista drive, I still think it might be better to steal a large chunk of Vista's free 200 gigs and give it directly to Ubuntu.

So, how would I go about doing this, I wonder?  I mean, I know how to use Vista's Disk Manager to shrink its partition, thereby creating a new partition to use.  But my question is this...how do I then get Ubuntu to see and use this new partition - or add it to its existing one?  Possible?  Not possible?

Thanks!

---

### Post by game_plan on 2008-05-05
Did you make primary or logical partitions? 

If they are primary or extended partitions then your best bet would be a program like partition magic since it can resize the partitions preserving the data.

If its a logical partition then you can use the fdisk command to expand your partition.

---

### Post by fahadsadah on 2008-05-05
After shrinking the Vista partition, please boot the computer up from the Hardy CD.
Then go to System->Administration->Partition Editor. You will be able to resize your Ubuntu partition.
I know you can resize the Vista partition from the LiveCD too, but that isn't guaranteed to work

---

### Post by retrow on 2008-05-05
If you need to use space from Vista partition just to store files, you can do that just by browsing to the partition which holds Windows and reading/writing files on the NTFS side. For the purposes of Ubuntu based applications and supporting files, 40GB is more than enough.

---

### Post by dazzlindonna on 2008-05-05
Thanks everyone for the quick answers.  Much appreciated.

---

### Post by ilrudie on 2008-05-05
Another option that is more complicated but might produce a nicer result would be to use the "stolen" disk space that vista is giving up to make a /home partition for ubuntu.  This is where your users would now live giving you 40 gigs for OS/Programs/Logs/etc and whatever you take from Vista for music/movies/documents and personal configuration.  This is a nice solution because if you mess up your Ubuntu install you can reinstall all the OS files without damaging your user accounts.  You will have to reinstall all the extra programs but your personal files will be saved.  If you are interested in this just post back to the thread and I can help you with it.

---

### Post by FuturePilot on 2008-05-05
You could use the Gparted Live CD and shrink the Vista partition and then expand the Ubuntu partition to take up the free space. Though I must warn that moving a partition to the left can take **hours** :shock:

---

### Post by dazzlindonna on 2008-05-05
That is a beautiful idea, ilrudie, but I've already done it one of the other ways above.  I'll definitely keep that in mind for the next go-round though.  Great tip.

---

### Post by ilrudie on 2008-05-05
No problem.  Glad to help.

---

