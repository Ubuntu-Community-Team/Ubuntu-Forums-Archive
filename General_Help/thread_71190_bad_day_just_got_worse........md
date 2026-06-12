---
title: "bad day just got worse......."
date: 2005-10-02
forum: General Help
---

### Post by MrCheese on 2005-10-02
Hi, have you ever typed "mkreiserfs /dev/hda1" and happily hit "y" to continue? I did, and waved goodbye to my XP system. Yeah, I know....don't congratulate me, I need it for some work stuff and my missus is a real luddite!
Does anyone know how to recover a reiser'ed drive which should be ntfs instead?
:(

---

### Post by nocturn on 2005-10-03
[QUOTE=MrCheese]Hi, have you ever typed "mkreiserfs /dev/hda1" and happily hit "y" to continue? I did, and waved goodbye to my XP system. Yeah, I know....don't congratulate me, I need it for some work stuff and my missus is a real luddite!
Does anyone know how to recover a reiser'ed drive which should be ntfs instead?
:([/QUOTE]

I'm sorry to say this, but basicly, your files on that partition are gone.
You can reformat the partition with NTFS, but you'll need to reinstall.

---

### Post by rcerreto on 2005-10-03
[QUOTE=MrCheese]Hi, have you ever typed "mkreiserfs /dev/hda1" and happily hit "y" to continue? I did, and waved goodbye to my XP system. Yeah, I know....don't congratulate me, I need it for some work stuff and my missus is a real luddite!
Does anyone know how to recover a reiser'ed drive which should be ntfs instead?
:([/QUOTE]
There are several products on the market which pretends to be able to recover lost data, even from a re-formatted drive. I'm not aware of any free or open sourced, though. Still, if you're really in trouble maybe it's worth the cost. Some of them are available in 'try-and-buy' so you might get the feeling whether they will do the job. Just have a look on Google.
Good luck! ;-)

---

### Post by az on 2005-10-03
[QUOTE=MrCheese]Hi, have you ever typed "mkreiserfs /dev/hda1" and happily hit "y" to continue? I did, and waved goodbye to my XP system. Yeah, I know....don't congratulate me, I need it for some work stuff and my missus is a real luddite!
Does anyone know how to recover a reiser'ed drive which should be ntfs instead?
:([/QUOTE]


You can spend a few hundred dollars and have the data recovered forensically.  It will take some time and your data recovery probably will be incomplete.

The reiserfs creation wrote all over your partition,  I really doubt any tools you can find over the internet will be able to recover anything, since they mostly deal with files deleted from an ntfs partition.  They do not take into account other filesystem structures.

You are screwed.

---

### Post by keninman on 2005-10-03
I use Restorer2000 Professional in my shop. If you can get the drive to spin up and you haven't written over the info then it should recover it. You will need another XP computer to install it on though. 
At $50 it is cheap and works well. I have even recovered deleted files and files from corrupt drives. It paid for itself the first time I used it on a customers drive.
[http://www.restorer2000.com]("http://www.restorer2000.com")

---

### Post by skoal on 2005-10-03
My suggestion?  First, get yourself another drive, old or purchase something cheap off eBay for around $5.  You only need something ~1-2 GB as a testbed system.

Install WinXP on it.  Try out a demo software program like: [http://www.runtime.org/gdb.htm](http://www.runtime.org/gdb.htm)

...GetBackData for NTFS.  Install that on your _second_ hdd under windows, and see if it can even recover that hda1 first.  Then, you can figure out where to proceed after that.  I believe from their docs you can just test to see if it's recoverable without destructively doing anything to it.  *Either way, don't mess with that partition on your drive now*.  You could possibly find something similiar to "GetBackData" you could burn on a bootable CD and do that instead of using a second hdd.  Either way, don't touch the first.
  
I use to use Ulitmate Boot CD for such occasions.  There may be some tools already on there to do the same.  _If_ you don't want to invest a small fortune and have a professional do this for you, I would suggest imaging that XP partition to a second hdd anyways (but you will need a second hdd at _least_ the same size as your XP partition on your original, not the ~1-2GB suggested above), leaving the original intact, and trying out various tools on the second to recover the NTFS partition.

Then, maybe try out good suggestions (like keninmans and others here) to proceed after that.

\\//_

---

### Post by Zotova on 2005-10-03
Well, I have no solution but could this be a blessing in disguise?

What programs do you need in xp for your work? There is a good chance there are linux alternatives which might even be compatible (open office, gaim etc)

Also what is it your missus doesn't like about Linux - or has she never tried it? Maybe you could get ubuntu profile set up so she'd never notice - give it xp style look so she feels at home and install the programs she likes then get her to give it a whirl... hopefully she'll like it and you won't get in trouble for deleting xp!

---

### Post by skoal on 2005-10-04
MrCheese, by the way, I ran across this the other day:[http://www.salvagentfs.com/1.0.html](http://www.salvagentfs.com/1.0.html)

Might be just the ticket! I would still image that NTFS partition to a second drive first and play with it there..

\\//_

---

### Post by skopas on 2005-10-04
Now is a good time to run Hiren's boot disk or a techie's boot disk.  They r dozen of revcovery progs on there.  U just never know.  Just an idea that's all, hope it can help.;)

---

