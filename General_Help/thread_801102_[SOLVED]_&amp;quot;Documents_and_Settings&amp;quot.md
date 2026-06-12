---
title: "[SOLVED] &amp;quot;Documents and Settings&amp;quot; missing - Sorry for the double post"
date: 2008-05-20
forum: General Help
---

### Post by Darvon on 2008-05-20
Hi! 

Yeah, i've posted this one in the absolute beginner talk already, but it is possible that tis is a wubi specific problem. (here's the post [http://ubuntuforums.org/showthread.php?t=730028](http://ubuntuforums.org/showthread.php?t=730028) )

I have WinXP an I've installed Ubuntu 8.04 with wubi. I have only one Partition( C:) so there are two systems on it.
The problem is: in my /host/Documents and Settings folder, there should be the folder from Windows, named after my Windows Username. But it isn't. There's "All Users" and "Default User" and so on, but my folder is missing. So I can't acces my documents, any firefox or other files. Everything else is there and I can access it.
With the Live CD the files are accessable, but not in that directory, it's in a "100 GB Medium" folder.
First I thought, the Win Username is a problem for Ubuntu (with "á" characters and a space), but changing that didn't work.
My Linux expert roommate tried something like mounting the drive manually (I'm a noob so I didn't get that completely) but this didn't work neither.

Suggestions so far are to copy everything to another folder in Windows, but then many programs wouldn't run well, and I still want to use my Windows. I neither have the disk space to double all the files.
Another one is to play around with partitioning, perhaps thats what I'll try next (if I feel like doing it and also have the time)

Perheps the wubi experts here can tell me something new :)

Thank You
Darvon

---

### Post by ago on 2008-05-20
Does your user name contain any special/accented chars? If so see [https://bugs.launchpad.net/wubi/+bug/136682](https://bugs.launchpad.net/wubi/+bug/136682)

---

### Post by Darvon on 2008-05-20
Ok, I want to thank you for the help, this was the Problem, this was really fast :)
Yeah, it was with the characters, and after getting that debdiff stuff, it was possible to download that lupin stuff and yeah... it worked.

BUT: As you see, I did not fix this, I asked for help, my roommate, who is programmer and knows linux quite well, he was doing it. And he needed half an hour!!! I have absolutely no clue how I could have done this alone, and how someone can call that "user friendly"!!! Okay, it's a bug, and it will be fixed. And sorry for you on the forum, I know you didn't do this mess, and you help whrever you can, and you report these things that they get fixed.
But it's still unbelievably annoying!

But still: Problem solved (you need the bug link from ago, with most of the comments, and this one [http://www.ntfs-3g.org/support.html#locale](http://www.ntfs-3g.org/support.html#locale) )

I hope I'll have a better time with ubuntu from now

Darvon

---

### Post by ago on 2008-05-20
> **Darvon said:**
> I know you didn't do this mess
Yes I did. I wrote wubi... And the bug has already been fixed (by Tormod). It only needs to be released and if you have already installed via Wubi, you will get that fix automatically via routine upgrades once it is released. So I wouldn't think it is too unfriendly.

---

