---
title: "Recovering lost data"
date: 2008-04-14
forum: General Help
---

### Post by helixed on 2008-04-14
A friend of mine recently had his windows partition crash.  Instead of recovering the data, he tried running the dell setup again, in the hope of being able to access the files.  The dell setup reformatted the hard drive.  I was wondering if anybody knows how I could recover these files.  I would really appreciate a GUI, but I could do some simple CLI stuff.

Thanks for the help,

Helixed

---

### Post by Rhubarb on 2008-04-14
There's a few ways to do this.

*Do not boot into windows.  Leave your computer off.
Take your hard drive to a data recovery specialist (the most expensive at ~US$300, but the best way to get your data recovered) - especially if you're not too confident doing this yourself.

*The other way is to boot up from a different large hard disk (bigger than the windows one) into Ubuntu.  Make sure the windows drive is not mounted.
Grab a the package called testdisk:
```
sudo aptitude install testdisk
```
In that package is a good CLI program called photorec.
You need to know the device that represents you windows hard disk.  For this I'll assume sdb1.
Then run the program:
```
photorec /dev/sdb1
```
This program will let you choose what files it can search for (jpg, png, exe, mov, mp3, doc, ogg, txt, and many others), and will prompt you where it wants you to dump the recovered files to (just make a directory in home named "recover" or something).
It takes about 20 to 30 or so minutes to scan through a 60GB drive, and it does recover most files fine.
photorec can take a while to learn how to use, but it isn't super hard to learn.

*Other possibilities you could take:
There are windows programs that you could use that may work - programs that can look through ntfs or fat32 partitions.  - You'd still need a 2nd hard drive that lets you dump the extracted files onto.

If the data is important or if you're not confident about using photorec / other programs, I strongly suggest you take it to a data recovery place.

---

### Post by harrybazeegar on 2008-04-14
Now I know why I love this forum :D

---

### Post by nickfish on 2008-04-14
thanks man 
your post  saved my life 
my wife was ready to  kill me because i formated her win partition\\:D/  
with her favorite photos inside

---

### Post by helixed on 2008-04-14
Thanks for the replies.   The only problem with this solution is the computer in question is a laptop, so I don’t really have any way of putting in a larger hard drive.  Is there some way I could do this with a live cd and an external hard drive,  or could I image the hard drive somehow and do it from another computer?

Thanks a lot,

helixed

---

### Post by tamoneya on 2008-04-14
using the ubuntu liveCD and an external USB drive will work for this situation.  Just make sure that no matter what you dont do anything to the original drive.  Even writting a text file could over write old data on the drive.

---

### Post by helixed on 2008-04-26
Okay, I thought I'd post a replay on how I finally managed to get this to work.  The photorec utility didn't seem to work quite right for me.  I couldn't figure out how to get it to work.  I booted from a live CD called MiniPe XT.  I ran one of the utilities off of this CD.  My main problem was finding some place to put the files.  Instead of messnng with trying to mount a hard drive on a windows live CD, I just networked a couple computers and transferred the files.  Anyway, I know it's not the cleanest solution, but it worked and I didn't have to buy any extra hardware. 

Helixed

---

