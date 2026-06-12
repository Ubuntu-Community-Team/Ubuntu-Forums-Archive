---
title: "error with updating staroffice"
date: 2007-12-20
forum: General Help
---

### Post by buildid on 2007-12-20
when i start the ./setup file ill get this error on my system :

root@buildid-desktop:/home/buildid/temp/120184-12# ./setup

Searching for the staroffice installation ...

read: 26: Illegal option -n

[: 28: ==: unexpected operator
root@buildid-desktop:/home/buildid/temp/120184-12# 

anybody have any idear this is my system or not ?

thank you

This is an legal version of staroffice , with an license ...

---

### Post by alfaro on 2008-03-06
I got the same problem, could u finally fixed it?

---

### Post by RMOP on 2008-03-24
Identical problem here as well. Any progress on your end?

---

### Post by Noobdaemon on 2008-03-31
Same problem here, I will try finding out some more information and when i fix it I will get back to you guys... I have just installed the legal star office, and so im pretty pissed of....

---

### Post by Noobdaemon on 2008-03-31
I found some sort of a solution here, but I am still having problems because it cannot find the correct files, does this work on your machines?

sudo alien -i --scripts /directory where you saved the files/120184-12/RMPS/8.rpm

PLease get back to me with the results.

---

### Post by malevolentjelly on 2008-04-11
I used this solution, which is a tad blunt:

```
sudo bash
alien -i --scripts ~/Desktop/120184-12/RPMS/*.rpm
```

Worked with flying colors, albeit pretty slowly. If you're attempting this, I suggest relaxing and grabbing yourself a snack.

:popcorn:

If you're having trouble with this- I don't mean to be presumptuous- but make sure you have alien installed:

```
sudo apt-get install alien
```

Thanks for the inspiration, y'alls. :)

FYI, I am running Xubuntu 8.04; not that it should make any difference.

---

### Post by malevolentjelly on 2008-04-11
Dupe?

---

### Post by Noobdaemon on 2008-04-13
This code worked:
alien -i --scripts ~/Desktop/120184-12/RPMS/*.rpm

Thanks a lot everyone

---

### Post by Noobdaemon on 2008-04-18
Thank you all for the effort :) After installing alien, and executing the alien command it worked perfectly!!! Thanks again and all enjoy star office :popcorn:

---

### Post by Noobdaemon on 2008-04-29
Ok now there is a new release of star office, well at least a new update... and the old methods wont work anymore... tried everything that we have tried before... but it says it cant find some file... ill try re-download it, but o dont think it will work... stupid updates:lolflag:

---

