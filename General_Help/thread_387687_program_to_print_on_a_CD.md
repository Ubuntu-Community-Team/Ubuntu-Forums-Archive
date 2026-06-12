---
title: "program to print on a CD"
date: 2007-03-18
forum: General Help
---

### Post by lyceum on 2007-03-18
Back when I was an avid Windows user, I bought an Epson Stylus Photo R200. It is a great printer. It has easily loaded up onto Dapper, Edgy and now Feisty. The thing I love the most about this printer is that it can print right onto a CD. I only have one problem now. I cannot get Epson's program to run on Ubuntu. There is a list of products, but none are FOSS. Is there a FOSS program that I can use to make CD labels and print them on my CD's  (no sticker)? 

Thank you.

---

### Post by koshari on 2007-03-18
use gimp to design the disk , it has a script that masks the cd/dvd shape, then export it to the turboprint print template which is an open office template, this works with canons, so it would just be a question of if the r200 had drivers that would allow to printing to the cd tray as in the canon.

---

### Post by ubuntu27 on 2007-03-18
> **lyceum said:**
> Back when I was an avid Windows user, I bought an Epson Stylus Photo R200. It is a great printer. It has easily loaded up onto Dapper, Edgy and now Feisty. The thing I love the most about this printer is that it can print right onto a CD. I only have one problem now. I cannot get Epson's program to run on Ubuntu. There is a list of products, but none are FOSS. Is there a FOSS program that I can use to make CD labels and print them on my CD's  (no sticker)? 

Thank you.

My HP printer doesn't have a "print to CD directly" properties. 
SO I didn't know that kind of printer existed, how useful must be.

I recommend you to try out [http://glabels.sourceforge.net/]("http://glabels.sourceforge.net/")glabels.
It's in the universe repository.

```
sudo aptitude install glabels
```


As the name suggest glabels let's you create labels. Too bad it dosn't have directly print to CD option, but, something is something. 

Stickers are not bad you know ;)

---

### Post by lyceum on 2007-03-18
Thank you, both of you. I know how to make the CDs, I just don't know how to get them onto the the CD in Ubuntu :( I really don't like the stickers, as they cost twice as much and the paper makes it look cheap. I pass out my own Ubuntu CDs, rather than wait for shipit. I felt a bit odd about doing everything on Ubuntu except for burning the ink onto the CDs. ah well. Thanks anyway.

---

### Post by ubuntu27 on 2007-03-18
> **lyceum said:**
> Thank you, both of you. I know how to make the CDs, I just don't know how to get them onto the the CD in Ubuntu :( I really don't like the stickers, as they cost twice as much and the paper makes it look cheap. I pass out my own Ubuntu CDs, rather than wait for shipit. I felt a bit odd about doing everything on Ubuntu except for burning the ink onto the CDs. ah well. Thanks anyway.

Wait, I think I found something.

cd-circleprint:

[http://sourceforge.net/projects/cd-circle-print/](http://sourceforge.net/projects/cd-circle-print/)

The Author says: "When I started burning CDs with linux there were some programs to print covers for cd boxes but I didn't find anything for printing nice circular labels for the CD itself.
So I started this little perlscript to print on my cd-labels."

---

### Post by boujemong on 2007-03-18
check out this post, i looked for weeks before finding a working solution to the r220 cd print problem.

this works on my edgy machine with an r220.

[http://ubuntuforums.org/showthread.php?t=180580&page=2](http://ubuntuforums.org/showthread.php?t=180580&page=2)

---

### Post by ubuntu27 on 2007-03-19
> **boujemong said:**
> check out this post, i looked for weeks before finding a working solution to the r220 cd print problem.

this works on my edgy machine with an r220.

[http://ubuntuforums.org/showthread.php?t=180580&page=2](http://ubuntuforums.org/showthread.php?t=180580&page=2)

Thank you Boujemong :)

Hope that thread will be useful to lyceum :)

---

### Post by lyceum on 2007-03-19
> **boujemong said:**
> check out this post, i looked for weeks before finding a working solution to the r220 cd print problem.

this works on my edgy machine with an r220.

[http://ubuntuforums.org/showthread.php?t=180580&page=2](http://ubuntuforums.org/showthread.php?t=180580&page=2)

Exactly what I was looking for, can't wait to try it :D Thanks!

:guitar:

---

