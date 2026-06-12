---
title: "/root and /home"
date: 2007-05-23
forum: General Help
---

### Post by atlfalcons866 on 2007-05-23
i have a 160GB PATA hdd. how much gigs should i give the root and how many gigs should i give the /home?

---

### Post by GrueTamer on 2007-05-23
Well, you could possibly give 10-15 gigs to root and the rest to home, but that's just my personal suggestion.

---

### Post by hartz on 2007-05-25
I agree with the 10 to 15 GB suggestion.  I also give 2XRAM to a swap partition.  Then the rest goes to /home.

I use to like having an additional data partition, but I am more and more leaning to minimizing the number of real/extra data partitions in favor for dumping data into /home.

---

### Post by atlfalcons866 on 2007-06-02
i gave it 30GBs for the root that too much?

---

### Post by hartz on 2007-06-02
"Too Much" is a relative and difficult thing to quantify.

I'd say it is "too much" when you leave too little for /home, and 160 - 30 = 120, so that is still plenty for /home.

On the other hand, you're not likely to utilize the 30 GB in / any time soon, you will probably find that about 20 GB of that is wasted, and then you start creating directories like /mystuff in root and then you start leaving Ubuntu CD .iso files and digital camera photos etc in the this directory, and soon your partitioned file systems become a mess.

So in my opinion (Note: It is an Opinion) : 30 GB is too much.

---

### Post by jjacobs2 on 2007-06-02
You could use LVM volumes and do 10 GB for /.  If you need more in the future you can resize without losing data.

---

### Post by atlfalcons866 on 2007-06-06
what is lvm manager

---

### Post by hartz on 2007-06-08
Search is your friend.  See this thread: [http://ubuntuforums.org/showthread.php?t=150482](http://ubuntuforums.org/showthread.php?t=150482)

---

