---
title: "Please help"
date: 2007-06-28
forum: General Help
---

### Post by bomb-24 on 2007-06-28
I have a question. I have windows xp on a hp media center. It came equipped with a d drive made for a system restore. Can I delete that stuff in the d drive and have an extra drive with about 5 gigs of free space? I am running a dual boot with Ubuntu and XP and I would like to put Ubuntu on the d drive if I could. I made a set of restore cds for my xp so Is there any point in having that d drive? Please help me. Thank you in advance

---

### Post by AlexThomson_NZ on 2007-06-28
Hi bomb- Yep no prob there.

Rather than keep it as a small 5G drive though, just merge it in with another partition.

I like to divide my drive into 3 parts...
 - 15 Gigs for Linux
 - Small bit for swap space
 - The rest as a "data" partition

...keeping my important stuff on the data part, so I can play with the linux part all I want and if I stuff it up, I can blow it away, restore and stuff have all my important stuff untouched.

EDIT: I see you are dual booting so you should probably have 4 partitions (imho):
 - 15 Gigs for Linux (ext3)
 - Small bit of swap space
 - 15 Gigs for WIndows (ntfs)
 - The rest for Data (ntfs if you want to share it with the windows partition)

That's how I would do it- entirely up to you of course! :)

---

### Post by bomb-24 on 2007-06-28
is my d drive (that is a system recovery drive) a separate drive all together? or part of the c drive? See my problem is, this dual booting is running a little slow. not much but I would like it to be faster. So I would like to run linux off of the d drive if it is a separate drive. and ofcourse, I would have to try to figure out how to uninstall my current Ubuntu and delete all of the partitions so it is back to normal then install on that drive. And my other question, If I have a set of recovery cds, I dont really need that recovery drive do I? If you can help me with how to uninstall all of the and deleting all of the partitions so it is back to normal, that would be great. or even some tips. Thanks man. I appreciate it.

---

### Post by AlexThomson_NZ on 2007-06-28
The D drive will not be a seperate drive- it is just on the same physical disc as the c drive (just "partioned" so windows acts like it is 2 seperate drives).  How are you dual-booting XP and Ubuntu if Ubuntu is not installed?  You just running it from CD? (that is not really dual booting)...

Can confirm, if you have the recovery CDs, you do not need the 5Gig partition, and can safely get rid of it :)

---

### Post by AlexThomson_NZ on 2007-06-28
I gotta run now, but am sure someone here will help you (it's a pretty simple task for someone who has done this).  I'll check in with ya tomorrow...

---

