---
title: "ddrescue and using offsets?"
date: 2016-12-14
forum: General Help
---

### Post by alex4478 on 2016-12-14
Hi,

I'm going through a personal data recovery nightmare and have decided to go down the route of installing Ubuntu, getting familiar enough with it to use ddrescue. I have read a lot about ddrescue, and have begun experimenting with some test disks. 

But it I have a question regarding offsetting.

As I understand it you can offset the start of the DD element from the source disk, but does that also offset the start of the cloned copy? If not how could you do that?

I'm asking because I'm hopeing to be able to have my source disk, (which has been formatted using fdisk to a system not recognised by osX) cloned missing the boot sector and then have the cloned data placed at the same offset of the backup drive. That drive would have a recognised partition and the newly cloned data would just "magically " be there. 

I'm sure I have it wrong. 

Thanks for any help.

---

### Post by alex4478 on 2016-12-15
I have continued to look for information on this and came across a site which suggests it can be done by the use of a -o flag.

> -o, --output-position=<pos>
   starting position in output file [ipos]

I may not have made sense in my fist post, I was tired at the time.

If I were to use a % instead of bytes/sectors measurement then I want to clone disk1 to 100%, using ddrescue to disk2. But, I want the offset of disk1 to start at 10% and the offset of disk2 to also be at 10%.

My thinking behind this is that disk1 has a very messed up boot sector, disk2 is fine and formatted as HFS+. So, would ddrescue take the data from after the boot sector and place it after the boot sector of disk2, therefore meaning that I could remove disk2 once the process has completed and connect it to my macOS and see the 'lost' data?

Many thanks for any responses.

---

### Post by sudodus on 2016-12-15
I suggest that you clone the whole drive with ddrescue, and afterwards identify and overwrite only the partition table with that of your backup. If it is a cloned backup with the same partition table it should work.

This means that a very small amount of data should be overwritten (and restored to what is correct). You can look at ddrescue as well as the original dd and their manuals to understand how to start and stop the overwriting at the correct positions.

-o-

You can create some small files and practice until you know how to read from the correct interval and write to the correct interval.

---

