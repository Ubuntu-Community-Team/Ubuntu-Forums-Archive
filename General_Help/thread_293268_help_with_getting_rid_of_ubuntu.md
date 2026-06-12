---
title: "help with getting rid of ubuntu"
date: 2006-11-04
forum: General Help
---

### Post by jdogg225 on 2006-11-04
Well, I am running ubuntu on my computer, no partitions, no dual booting. How do I get rid of it and format my hard drive completely? I am selling my computer so I need everything wiped.

](*,) I have done countless searches on these forums and google.

---

### Post by jdogg225 on 2006-11-05
Well, I am running ubuntu on my computer, no partitions, no dual booting. How do I get rid of it and format my hard drive completely? I am selling my computer so I need everything wiped.

](*,) I have done countless searches on these forums and google.

---

### Post by K.Mandla on 2006-11-05
Try [Killdisk]("http://www.killdisk.com"). It completely blanks the entire surface of your drive. Great for erasing machines before passing them on. ;)

---

### Post by Dullin on 2006-11-05
You can also try Dban the most notorious cd for this kind of thing. Watch out though, leaving it in the cd drive and rebooting starts the process. **Not to be taken lightly!**
[http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

---

### Post by jocko on 2006-11-05
You could boot a ubuntu live cd and delete the partitions with gparted.

---

### Post by towsonu2003 on 2006-11-05
> **jocko said:**
> You could boot a ubuntu live cd and delete the partitions with gparted.

just repartitioning and / or formatting may leave some recoverable data. just my 2 dollars :P

---

### Post by jdogg225 on 2006-11-05
> **K.Mandla said:**
> Try [Killdisk]("http://www.killdisk.com"). It completely blanks the entire surface of your drive. Great for erasing machines before passing them on. ;)

Thanks, its working so far as I see, but it will take some time. :)

---

### Post by ckonrad on 2006-11-05
> **jdogg225 said:**
> Well, I am running ubuntu on my computer, no partitions, no dual booting. How do I get rid of it and format my hard drive completely? I am selling my computer so I need everything wiped.

](*,) I have done countless searches on these forums and google.

you can do that very simply, all you have to do is put in a live linux cd and when it boots to your desktop open up a terminal and type this below as root

shred -vfz -n 7 /dev/hda

the number 7 above is the number of times that the data on your system will be written over with garbage data, you can replace that number with any number you want the larger the number the longer it will take and if you hardrive is big it will take long, you can just use 1 if you want a quick erase but if you have sensitive data on your system a person could still get some of that data using various methods, the department of defense erases there drives 35 times, so if you want to do it that say type 35 above instead of 7.

-corey

---

