---
title: "un rm?"
date: 2007-08-07
forum: General Help
---

### Post by chr1831 on 2007-08-07
can i un rm -r a folder? i kinda did it on the wrong folder :(

-Chris

---

### Post by yabbadabbadont on 2007-08-07
Not really.  You, like many before you (including me), will likely never do that again.  ;)

---

### Post by ChasHutch on 2007-08-07
I learned the same lesson...  the hard way!

---

### Post by chr1831 on 2007-08-07
dang it!!!, i need my file back...., i just lost my 22page thesis..., due in 3more weeks......., lovely.... atleast i didn't do it the day b4..., and now i know backup in 2 DIFFERENT dirs in 2 DIFFERNT locations and not in the same dir....

-Chris
 `-Royaly Screwed
    `-Wants his thesis back....

---

### Post by lisati on 2007-08-07
> **chr1831 said:**
> dang it!!!, i need my file back...., i just lost my 22page thesis..., due in 3more weeks......., lovely.... atleast i didn't do it the day b4..., and now i know backup in 2 DIFFERENT dirs in 2 DIFFERNT locations and not in the same dir....

-Chris
 `-Royaly Screwed
    `-Wants his thesis back....

Ouch! Having accidentally deleted the wrong thing myself, I know what you mean!
Short of going to a backup, it looks like your memory and typing fingers will be getting a LOT of exercise.

Good luck!

---

### Post by yabbadabbadont on 2007-08-07
Well, you might try one of these:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

(the last one doesn't seem to be responding for me currently)

By the way, when making a "backup", at least put it onto a different drive.  Better yet, at least two different pieces of external media (CD, DVD, Tape, ...)  Like I said before, you'll never make this mistake again...  :(

---

### Post by ertrules22 on 2007-08-07
That sucks!
I feel for you!
(Although I have never deleted a file that I needed in ubuntu, oh well!)
Hope you can get your thesis rewritten!
:popcorn:

---

### Post by bodhi.zazen on 2007-08-07
See if this helps :

[https://answers.launchpad.net/ubuntu/+question/2178](https://answers.launchpad.net/ubuntu/+question/2178)

---

### Post by apetresc on 2007-08-07
You posted this thread about an hour ago, so it is probably too late now :( But for future reference if this happens again (but I bet it won't :)), the FIRST THING you should do is unmount the partition and remount it read-only. You can use the line: ```
mount -o remount,ro /home
```(This assumes, of course, that /home is a separate partition, which is always a good idea, especially in cases like these).
This works because "rm" does not actually overwrite the data on the hard drive, merely removes the last reference to the data, basically giving permission to the kernel to use that space for other things. The faster you unmount the filesystem, the less time the kernel has to get around to actually using that space.

Once that's done, you can use some of the various tools, like the ones bodhi posted, to get a lower-level look at the filesystem and recover what you can.

More details can be found here, for example: [http://www.antipope.org/charlie/linux/shopper/152.html](http://www.antipope.org/charlie/linux/shopper/152.html)

Good luck!

---

### Post by Nekiruhs on 2007-08-07
To prevent this from happening again:
```
echo "alias rm='rm -i'" >> ~/.bashrc && source .bashrc
```
Makes RM always go interactively.

---

### Post by chr1831 on 2007-08-07
is there a live cd with these tools?, i don't want to turn the computer back on :)

-Chris

---

### Post by apetresc on 2007-08-07
> **chr1831 said:**
> is there a live cd with these tools?, i don't want to turn the computer back on :)

-Chris

Yes :D It's called "Knoppix STD" (that stands for "Security Tools Distribution", not the other thing ;))

It's a version of Knoppix that has been loaded with a lot of security and forensics tools. It has everything necessary to do some quite advanced forensics and recovery. The only complaint one could have against it is that some of the tools aren't exactly intuitive to use. But you can find documentation for them. Otherwise, it is the *perfect* tool for the job!

It can be downloaded here: [http://s-t-d.org/](http://s-t-d.org/)

---

