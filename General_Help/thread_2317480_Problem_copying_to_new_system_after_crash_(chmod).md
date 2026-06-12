---
title: "Problem copying to new system after crash (chmod)"
date: 2016-03-16
forum: General Help
---

### Post by stepnjump1 on 2016-03-16
Hi guys,

I have a situation.
I removed compiz the other day and that crashed my system.
So I used a live CD, moved all my data to an external hard drive using cp -avr command in the hope I was going to keep all my permissions.

I kept the same username and group when I reinstalled but the easy move that I had anticipated is not working.

My archives are showing 600 instead of 644 and my directories 700 instead of 755

There are so many layers of directories that I was wondering if there might be anything I could easily do to make the move onto their new home partition other than having to run a script?

Thank you very much in advance,

Step

---

### Post by howefield on 2016-03-16
Thread moved to the "*General Help*" forum.

---

### Post by bab1 on 2016-03-16
> **stepnjump1 said:**
> Hi guys,

I have a situation.
I removed compiz the other day and that crashed my system.
So I used a live CD, moved all my data to an external hard drive using cp -avr command in the hope I was going to keep all my permissions.

I kept the same username and group when I reinstalled but the easy move that I had anticipated is not working.

My archives are showing 600 instead of 644 and my directories 700 instead of 755

There are so many layers of directories that I was wondering if there might be anything I could easily do to make the move onto their new home partition other than having to run a script?

Thank you very much in advance,

Step

From the top level directory you can use this chmod command to change the permissions back on the complete directory tree```

sudo chmod -R ug=rwX,o=rX </path/to/directory>
```...where </path/to/directory> is your path to the top level directory of the data.

---

### Post by stepnjump1 on 2016-03-17
Thank you very much BAB1. This is going to be very helpful.

---

