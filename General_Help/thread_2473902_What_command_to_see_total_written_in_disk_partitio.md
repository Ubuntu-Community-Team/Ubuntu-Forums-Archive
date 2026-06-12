---
title: "What command to see total written in disk partition ?"
date: 2022-04-17
forum: General Help
---

### Post by aug7744 on 2022-04-17
Hello.
The disk is using 4 partitions.
How see total written for each partition (sdaX) since the OS was started ?
Stacer display only the total written for all partition in disk.
Thanks for reply.

---

### Post by yancek on 2022-04-18
smartctl should do the job.  Check the site below for some information on it.  Check various options available to get what you want.  It should be available on a default install.

[https://serverfault.com/questions/480726/how-to-measure-total-writes-performed-to-ssd-in-linux](https://serverfault.com/questions/480726/how-to-measure-total-writes-performed-to-ssd-in-linux)

---

### Post by aug7744 on 2022-04-18
@[**[COLOR=#000000]yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724")
Hello.
I not want the total written in all life of disk.
I have smartctl and not see any option to see that information.
Only the total written in partition since the OS was started.

---

### Post by #&amp;thj^% on 2022-04-18
> **aug7744 said:**
> @[**[COLOR=#000000]yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724")

Only the total written in partition since the OS was started.

As of yet  that's not possible you'll only see:
```

    Data Units Read (how much data was read over the lifetime of the disk)
    Data Units Written (how much data was read over the lifetime of the disk)
    Host Read Commands (how many read commands were issued to the disk over its lifetime)
    Host Write Commands (how many write commands were issued to the disk over its lifetime)
  
```

---

