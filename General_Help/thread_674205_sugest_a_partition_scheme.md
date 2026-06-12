---
title: "sugest a partition scheme"
date: 2008-01-21
forum: General Help
---

### Post by markp1989 on 2008-01-21
i currently have an 80gb sata drive partitioned like this
10gb windows
8gb /
1gb swap
reat /home

i have just brought a 160gb hard disk,that im am planing to add along side this  drive, what would be the best partitioning scheme for this, i will have about 240 gb total storage

i need windows, just for printing, and am planing to keep the windows partition the same, i dont mind re installing ubuntu if it is needed,

i would like to leave around 20gb unpartitioned for experimenting with new distros etc 

i just want to know what the best partitioning scheme should be

thanks for any advice given

---

### Post by logos34 on 2008-01-21
Personally, I'd just partition it as one big ext3 (leaving a little empty space at beginning or end for testing linux distros).  

here's one link worth a glance:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by markp1989 on 2008-01-21
ok, that makes sense, il prob do that, just set up a mount point and add it to my fstab,  il prob set it as /media/data or somthing like that, i have a while to decide what im going to do, cause im waiting for it to get here

---

### Post by markp1989 on 2008-01-27
Thanks, i did as you sugested, and it works fine, one question i would like to askl, i have created folders on the new drive called "Music" "Videos" "Pictures" and "Disk Images" 

how would i replace the folders in my home folder with system links to these folders? 

i would like /home/mark/Music to link to /media/data/Music 

how would i go about doing this?

---

### Post by cheahk on 2008-01-27
> **markp1989 said:**
> 

i would like /home/mark/Music to link to /media/data/Music 



```
ln -s /media/data/Music /home/mark/Music 
```

-K

---

### Post by markp1989 on 2008-01-27
> **cheahk said:**
> ```
ln -s /media/data/Music /home/mark/Music 
```

-K

 thankyou, worked perfectly

---

