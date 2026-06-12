---
title: "Running Music Library System on Ubuntu 12.04"
date: 2014-03-23
forum: General Help
---

### Post by rbmoler on 2014-03-23
I'm quite new to Ubuntu (12.04), but happy with it so far.  I'm migrating from XP.  On XP I have a very old specialized DOS data base called* "Music Library System."* (I installed it under MS-D0S in 1988.)  It holds all the cross-indexted files from some 3000 LPs, CDs, DVD/BluRay discs, LDs, and LPs of classical music.  It is rather specialized and I've been completely unsuccessful at moving the files to a modern database program including the one in LibreOffice.  I can run it in XP with no problem.  I'd like to run in it Ubuntu, probably in something like VM box using a suitable DOS like FreeDos.  Is that remotely possible?  If so I could use a little guidance.

I presently have a separate HD (E:\ under XP and media/data under Ubuntu) configured to be visible to both OPs and to share the same profiles with Firefox and Thunderbird along with a large quantity of other information.  It also contains the *Music Library System*, its executable file and all six of the separate databases that make up the searchable database system.  That is found in a directory *\Music.  *In XP I simply created a shortcut to the executable file  so whenever I need to update the data or search for a particular piece of music or video and/or its location in the CD/DVD/LD/LP storage locations I simply double click the icon on the XP Desktop.

Any guidance would be appreciated.

---

### Post by CharlesA on 2014-03-23
What database was it now?

---

### Post by Lars Noodén on 2014-03-23
There is also the possiblity that it would run under WINE.  If it does, then you would not need to worry about the VM and FreeDOS.  It's in the repository so it is easy to install and, if it does not work out, to remove.

---

### Post by Mark Phelps on 2014-03-23
Forget about Wine.  Checked there and Music Library System is not listed as a compatible app.

---

### Post by slooksterpsv on 2014-03-23
If it's a dos app what about DosBOX?

---

### Post by Lars Noodén on 2014-03-23
> **Mark Phelps said:**
> Forget about Wine.  Checked there and Music Library System is not listed as a compatible app.

If it's missing means that it hasn't been checked one way or another.  The few times I've had to use WINE it has been with older, relatively unkown apps and they worked though they were unlisted.  The ones to watch out for are the ones that are clearly listed and categorized under bronze or worse.

---

### Post by rbmoler on 2014-03-23
I did look at DosBox.  It was pretty clear that it is intended for gaming only.  If It didn't work I'd get no help.  I still may try it.

Here is more detailed information about the program:   

Source:   The Softwre Guild, Inc.. 13533 S.W. 63 Lane, Miami, Florida, 33183 Telephone 305-956-3114 (not in service)

Title:       Music Library System  Version 2.1

Program and Manual written by Douglas McFaul

The Copywrite notice is shown as 1986-1991, so my memory was probably faulty regarding when I installed it, but almost certainly on the first ordinary PC that I owned, the absolutely first being the original Sanyo.

The program in on a floppy (actually 2 different floppies, one being an ancient 5.25" floppy that I cannot play.)  I have the program and the most recent data base update on a CD as well

It's a program that is highly unlikely to be known by anyone at this point.  Very likely it was quite short lived, because  a couple of Windows based music cataloging programs came into existence a few years later.

It is certainly well beyond my skill to know whether or not it was adapted from some other DOS database program or was written de novo.  It has a fairly comprehensive data file and seven auxillary (smaller) databases that permit searching in a variety of ways.  The main database in less than 3MB, so the whole thng is not very large, but it is very efficient and easy to use even if you can't search in the nearly unlimited way that you can in a modern database.

I could upload the Music.exe file (to ?) if someone wanted to try running it in a DOS emulator.

---

### Post by tgalati4 on 2014-03-23
Is there any way to export the database while running in DOS to any other recognizable format?  Then you would at least have a chance to write a script to parse it into XML and then import it into rhythmbox or some other linux music manager.

---

### Post by rbmoler on 2014-03-24
It's a simple program.  You can print out the data in a number of different configurations, but there is no export function.  The entire music.exe file is only 78 kB.  It was designed to operate with two floppy discs.  It operates in a very simple manner using an entry form that is just a tabbed list with entries separated by spaces.  Probably anyone with a bit of skill with databases could figure out how to read the data and get it into a modern database.

Slooksterpsy has offered to try running it under DosBox.  I just need to know how to send it to him using the private message system.  I can't locate a way to attach a file.

---

### Post by CharlesA on 2014-03-24
You cannot attach files to private messages.

---

### Post by slooksterpsv on 2014-03-24
It works under dosbox, but there's no way to export any of the data to another format in the program. There may be a way to convert the output files to different format. I would say there's better applications out there for this program where you can even pull the data from the internet and sync it to a database.

EDIT: Also to remove copyright infringement I've deleted the file and any files it created.

[ATTACH=CONFIG]251431[/ATTACH][ATTACH=CONFIG]251430[/ATTACH]

---

### Post by tgalati4 on 2014-03-24
If you don't mind us making fun of your musical taste, attach the database file.  Perhaps a hex editor or some simple scripting can pull the data apart into something that is useful. Otherwise, your legacy music list program is the reason dosbox exists.

---

### Post by rbmoler on 2014-03-24
Thanks to slooksterpsv for helping out.
I'm way too old to be at all bothered by jests regarding my 65 year long (I didn't start until I was 15 so add 15:D)  devotion to classical music.  Well I like jazz too and I have a good bit of Benny Goodman, and the full 6 CD album if Keith Jarrett at the Blue Note.  Too far off topic, sorry.

   I'll upload the music.dat file to box and provide the link here for anyone who wants to take a crack at it.

There were better programs available long ago, but I didn't relish haveing to reenter a thousand or more files.  Now it's approaching 3000.

---

### Post by rbmoler on 2014-03-24
Here is the link to Box where I uploaded the Music.dat file.  There are actually 7 more files of the form IXx where x = 1-7.  They provide different ways of searching through the .dat file.

[https://app.box.com/s/qpip18adxtpltp2w9av3](https://app.box.com/s/qpip18adxtpltp2w9av3)

---

### Post by tgalati4 on 2014-03-25
I only see the executable file (MUSIC.EXE) at that link.  No data files.

---

### Post by freebird54 on 2014-03-25
> **tgalati4 said:**
> I only see the executable file (MUSIC.EXE) at that link.  No data files.

Apparently it was written in what looks to me like an early version of Borland's Turbo Pascal.  The storage method is likely to be 'discoverable' - and may even use fixed length records (ie: 512 bytes for sector-base scanning) and the .IX# files will be indexes that can be rebuilt from an REBUILD command.  I'd be happy to have a look if the data file itself appears - I have a lot of old 'C' and assembler 'data massage' and 'conversion' routines lying around from an earlier age :)

Yeah - I know I'm showing my age too :) - even if I'm mostly rock!

---

### Post by TheFu on 2014-03-25
Has any consideration been given to just pointing a new management system at the files and letting the automatic processes discover the content?  Plex is really good at this, provided the different types of files are segmented into different directories
* music
* tv
* movies
* home movies
If this is commercial stuff, then most of the content will be recognized if named reasonably.

BTW, I used to write programs using borland tools and the old file-based DBs early in my career - paradox, DB2, DB3, DBIV.  The amount of bloat in code these days is unbelievable in comparison.

---

### Post by rbmoler on 2014-03-25
The database is dominately classical CDs.  The next biggest category is DVDs of operas.  LDs and LPs are also present.  I've converted all of my VHS tapes (also operas) to DVD (for my own use, of course.)  There is no specific way to segregate the different formats.  I used "Location" to handle that by prefixing every entry by the name of the format (CD, DVD [includes blurays] LD and LP.)  They are stored by format; composer last name (main composer for discs with works from several composers); title (for example Symphony No 6 or Aida) and Category- an arbitrary 3 digit number that represents the type of work (415 = string trio, 705 = dymphony.)

I didn't quite understand how BOX did sharing.  I uploaded the .dat file and assumed the old link would work.  Here's the correct one.

[https://app.box.com/s/e4pwpu93lpzkp9wmeivv](https://app.box.com/s/e4pwpu93lpzkp9wmeivv)

---

### Post by TheFu on 2014-03-25
If you are happy with the current solution, keep using it knowing that the collection will be lost by your heirs or estate. Went through that last year when Mom died.  She kept amazing paper records though she had software that was current and maintained too.  The paper was her records - NOT the software - and she didn't do a good job of keeping things in order or even in the same boxes. Nobody wants to go through all that paper - think it was all shredded.

So - if you want to move to a newer system ...

* If CDDB has the music, they can be automatically added to modern DBs. There are other music DBs online too that might work.
* For TV and Movies, if they are in IMDB, theTVDB or TheMovieDB, they can be automatically added to modern DBs.

It all comes down to filenames and directory names matching the expected formats for whatever tool you use for videos.  Music generally needs ID3-tags.

Things that aren't in those DBs will need to be manually entered, somehow. CSV is a common way. 
I looked at the file - seems like a very simple format, if you know the data and can figure out how many lines are used for each record. A 10 line perl, python, ruby, what-ever script can parse it into CSV for use by any spreadsheet or import into another system.

---

### Post by tgalati4 on 2014-03-25
Now share at least one index file so we can see the structure of the data.  Paging through a binary file with *hexedit* is no fun.

For real CD's, I agree, just put them in a music manager and let the CDDB fill in the meta-data.

Describe how you will use the database going forward.  Do you want to set up a media server and play the tracks directly?  Is the database simply used for a library indexing system so you can find them on the shelf?  

How do you use the music database on a day-to-day basis?

Looking at the data, it does appear to be a Turbo Pascal, fixed-length, flat, database.  So I am showing my age as well.  I now have Barber's *Adagio for Strings* playing in my head.

---

### Post by freebird54 on 2014-03-25
> **rbmoler said:**
> The database is dominately classical CDs.  The next biggest category is DVDs of operas.  LDs and LPs are also present.  I've converted all of my VHS tapes (also operas) to DVD (for my own use, of course.)  There is no specific way to segregate the different formats.  I used "Location" to handle that by prefixing every entry by the name of the format (CD, DVD [includes blurays] LD and LP.)  They are stored by format; composer last name (main composer for discs with works from several composers); title (for example Symphony No 6 or Aida) and Category- an arbitrary 3 digit number that represents the type of work (415 = string trio, 705 = dymphony.)

I didn't quite understand how BOX did sharing.  I uploaded the .dat file and assumed the old link would work.  Here's the correct one.

[https://app.box.com/s/e4pwpu93lpzkp9wmeivv](https://app.box.com/s/e4pwpu93lpzkp9wmeivv)

I am pretty sure I can extract the files to put in whatever format you wish - but it would be much easier if I could see whatever the program looks like while running...  Could you post the REBUILD utility, or the set of .IX# files?  It might give me some direct information about field names, and sizes, that I can't easily deduce from the .DAT file...

Thanks!

---

### Post by rbmoler on 2014-03-25
The database had a simple purpose.  I had been keeping my LPs on a deep shelf filed by composer.  By the time I had a couple hundred, it started to get messy because I could have a Beethoven piano sonota on three different LPs only on one of which Beethoven was the first composer.  I couldn't keep in my head all those separate locations.  I needed a way to find a particular performance, hence the *Music Library System *which is just what it says it is, a good way to catalog (and file) the albums so that, for example, I can easily locate one of the six versions of Barber's Adagio including the original, which is the Adagio movement in his string quartet.  I'm going to have it running amok in my head for the next several hours.  The CDs are in purpose designed and built drawers cabinets, each drawer holding about 90 singles.

I'm still adding to my collection sporadically - particularly operas.  I agree, the collection will be dispersed when I die.  None of my kids are passionate about classical music.  I am not a casual listener either.  I go to a lot of concerts in the Northern VA area.  The music and video go through my Oppo DVD/Blueray player to a 67inch screen and a Sony 200W/ch 7.1 channel receiver to a pair of Phase Tech floor standing speakers.  There are a few surround sound CD and videos also.

So the database has no purpose other than making it easy for me to keep the collection stored in an orderly manner and the music relatively easy to put my finger on.

I'll upload one of the IX# files and provide the link.

IX1 has been uploaded to Box.  The link is:     [https://app.box.com/s/bzqnhp2xybzkwgaji24d](https://app.box.com/s/bzqnhp2xybzkwgaji24d)

BTW:  The author of the program is, apparently, alive and well in the Miami area.  He and his wife ran the *Software Guild, Inc.  *It has not been shut down but is listed as inactive.

---

### Post by freebird54 on 2014-03-25
> **rbmoler said:**
> 
I'll upload one of the IX# files and provide the link.

IX1 has been uploaded to Box.  The link is:     [https://app.box.com/s/bzqnhp2xybzkwgaji24d](https://app.box.com/s/bzqnhp2xybzkwgaji24d)


Apparently it needs all of the defined index files, or the REBUILD program to create them, before it will run.  Perhaps you could pop either up for that purpose?

Being that you use the program for a reference only, have you thought what form you would most like to have it in?  It is, of course, possible to run it the way it is in DOSbox... or you run it in a spreadsheet - or any number of alternate database programs once the data is out and portable.  If your choice is DOSbox - it should be possible to make it accessible directly from the desktop...  :)  Of course - then I wouldn't have the fun of extracting the data...  Your choice.

---

### Post by tgalati4 on 2014-03-25
One possible use case is to use *dosbox* to run the existing database.  Then add any new albums to *rhythmbox* or some other music database.  Then you would have to search through two databases to find what you want.  An alternative is to manually add items to a new database any time you perform a comparative--listening to all 6 versions of Barber's *Adagio for Strings* for instance.  That way you incrementally add items to the new database and you will have a current listing of all the tracks that you have listened to recently.

When you die, please send me a PM, because I would like to buy your collection.  You might need to write a script to do that, because it is difficult to send a PM when you are dead.  But the collection is impressive!

Send an email to the author and ask him to port it to linux.  There is a pascal compiler for linux call free pascal (fpc).  I'm not sure of the differences from Turbo Pascal, but no harm in trying to compile.  Ask the author if he would be willing to release the code under an open license.

---

### Post by freebird54 on 2014-03-25
The more I think about it, the more I suspect you might be better off just running it in dosbox - one click from the desktop to running...

If you don't yet know how... after dosbox is installed and run the first time, it creates a 'hidden' directory for itself in your home directory. This is called **.dosbox** (note the **.** - that's what makes it 'hidden' when you don't tell it to show! (use of **CTRL-H** will toggle the hidden into view or not)).  First, you copy all of your MUSIC.* files into **.dosbox**.  In there is a file called *doscfg-0.74.conf*.  If you add these lines:
```

mount c ~/.dosbox
c:
music
exit

```
at the very bottom (after AUTOEXEC) and save, the next time you start DOSbox with a click on the side panel, it should autostart right into the MUSIC program, with all files present... and exit cleanly when you leave!

Enjoy - or let me at the running program for extraction!  :)

---

### Post by rbmoler on 2014-03-26
I'll upload the entire thing on BOX and put the link here.

I have dosbox on my desktop already and attempted to use it to access the Music directory on the common data disk** media/data**\music\music.exe.  No luck with that.  If that's possible I'd prefer to run the program that way so for a while at least its available if I boot Win XP.  

I really don't see much point in using some other DB program.  I have such a program on XP and while it would find the data on-line, It didn't make the lookup as useful as Music does.  Most of those programs are designed for popular/rock/etc music.  They get hung up with performers and singers rather than Composers which is the top item in Music Library.

My local classical music station is interested in the collection.  I'll definitely leave instruction to my executor (My oldest daughter) to contact tgalati4 if the station declines to accept it under the terms of my will.

I need java to upload the folder Music otherwise I'd have to have 9 links, UGH.  Be back later (I hope) with just one link

---

### Post by freebird54 on 2014-03-26
Probably the best bet... I still have things accessible in a similar manner instead of on a 'real' platform - and not just because I wrote the alternatives :) (sometimes simpler is better)

You could still modify the doscfg file as suggested, though - to make it easy to access quickly (which is part of the point, right?) Perhaps like this:

```

mount c /media/data/music
c:
music
exit

```
should do it.  Enjoy - and if this is the 'final fix', please mark this thread SOLVED with the Thread Tools at the top right of the page..

---

### Post by rbmoler on 2014-03-26
I had actually tried that already.  I tried again opening dosbox and got the prompt Z:\

When I copied the line 
[B]mount c /media/data/music
[/B]
I get the message that the directory doesn't exist.  It further says that it really has to be in the home/robert directory.  (example dos/progs)
So that's my sticking point.  Apparently media/data doesn't exist as far as dos box is concerned.  Just to be sure there's not something missing:
  I've set up media/data so that it mounts on bootup.  My Firefox and Thunderbird profiles are there so that both OSs access the same profiles.  Does that make any difference?

Here's the link to the folder *Music* which has the complete data base (9 files)

[https://app.box.com/s/f2rn6knth69k54zkzy2p](https://app.box.com/s/f2rn6knth69k54zkzy2p)

---

### Post by freebird54 on 2014-03-26
> **rbmoler said:**
> I had actually tried that already.  I tried again opening dosbox and got the prompt Z:\

When I copied the line 
[B]mount c /media/data/music
[/B]
I get the message that the directory doesn't exist.  It further says that it really has to be in the home/robert directory.  (example dos/progs)
So that's my sticking point.  Apparently media/data doesn't exist as far as dos box is concerned.  Just to be sure there's not something missing:
  I've set up media/data so that it mounts on bootup.  My Firefox and Thunderbird profiles are there so that both OSs access the same profiles.  Does that make any difference?

Here's the link to the folder *Music* which has the complete data base (9 files)

[https://app.box.com/s/f2rn6knth69k54zkzy2p](https://app.box.com/s/f2rn6knth69k54zkzy2p)

OK - that should not happen - I just tried the whole program here - and it is willing to work anywhere I put it... such as 
```

mount c /mnt/data2/music

```

OR

```

mount c /media/Expansion_/music

```

so the location did not bite you :)  I would expect that a typo - or not EXACTLY matching the name of your external drive (including especially the CaSe of that name) might be the source of your dfficulty :)

I could still try to extract the data for you - but you will have a hard time matching its capabilities without a custom rewrite  - and you are used to it now anyway!  Hope this helps...

---

### Post by rbmoler on 2014-03-26
I'm a little frustrated here.  When I open media/data/ in my home folder and then open the folder /Music/ (with the initial uppercas M) is that name going to be the correct one for opening it as c in dosbox?  I was very careful to change the label on my E drive under XP to be all lower case letters.  Ubuntu does indeed see the Music folder as having an uppercase initial M and shows the drive as media/data all lowercase.

I've played with this for the past hour.  I made absolutely sure that everything is lowercase.  Home folder shows the external drive as media/data (all lower case)  If I open it and brouse to music (all lower case.)  I see the music.exe file and all the other files   I even copied and pasted the names into the dosbox mount command, but I always get the" directory does not exist" response.  Maybe I really do have to unmount that drive before I can mount it again under dosbox.

I even opened XP and looked at the disk label and directory name to verify that I had it right.  Still no luck.  Something more is involved.

---

### Post by freebird54 on 2014-03-26
> **rbmoler said:**
> I'm a little frustrated here.  When I open media/data/ in my home folder and then open the folder /Music/ (with the initial uppercas M) is that name going to be the correct one for opening it as c in dosbox?  I was very careful to change the label on my E drive under XP to be all lower case letters.  Ubuntu does indeed see the Music folder as having an uppercase initial M and shows the drive as media/data all lowercase.

Now what! he said.

There you go - whatever EXACTLY it would look like in your Ubuntu terminal, is what you need in that mount statement.  so if your terminal says:
```
/media/data/Music
```
then you need a mount command of:
```
mount c /media/data/Music
```

Different systems treat upper and lower case in different ways:
Windows/DOS - doesn't care, or preserve the case you use - you say music, and it says MUSIC
Linux/Unix/Mac - DOES care, and preserves case - You say MuSiC - and you can't access the file any other way
AmigaDOS - doesn't care, but DOES preserve the Case you use - you say MuSiC and music or MUSIC will access it.
Newer Windows - finally allows a longer filename, and preserves case, but does NOT care - as always :)

The preference for lower case you notice in the Linux world is really spelled laziness - can't be bothered to hit the <SHIFT> key :)  However, it does make for safer passwords - and prettier listings done the Linux way.  The consequence, though, is the insistence on precision.  You will notice in my previous examples that I needed to put a Capital on **Expansion_**, as well as the trailing underline, or it would NOT have worked on my system.

Give it a try...

---

### Post by rbmoler on 2014-03-27
Unfortunately that doesn't work.  I still get the same message that the folder/directory doesn't exist.  I know (assuming I can believe my own eyes and didn't deceive myself) that I have the spelling and cases right.

I suspect it has something to do with the fact that the drive is already mounted as media/dat.  Perhaps someone with an external drive could verify that.

I can't unmount media/data without going into terminal mode and using the umount command and I haven't quite gotten the syntax of that figured out yet.

Oh, good grief!  I was doing something wrong and I don't know what it is.  Would an extra space between "c" and "/media/data/music cause it to fail?  Maybe I'm getting senile at this young age!

In any case I just opened it and ran the program, so by gum you guys were right and I just needed to follow your advice.

Problem solved.  Sorry I wasted a lot of your time.

---

### Post by freebird54 on 2014-03-27
No problem at this end!  It takes every one a while to realize just HOW literal computers can be :)

We will know that computers have come of age (!) when they understand the DWIM command, and execute it perfectly....


**D**o  **W**hat **I**  **M**ean  :)

Have a good one - and have good listen too!

---

### Post by tgalati4 on 2014-03-27
Now I just need to figure out how to get your local station to change its play format to smooth jazz.  They would then be much less interested in a classical music collection--regardless of how well-organized it is.

Music trivia:  How many movies have used Barber's Adagio for Strings (or snippets of it)

1.  Platoon, dramatic evacuation scene

Answer:  (no peeking!)

[http://en.wikipedia.org/wiki/Adagio_for_Strings](http://en.wikipedia.org/wiki/Adagio_for_Strings)

---

### Post by louise2 on 2014-04-24
My apologies for dropping in as a newbie onto a Solved thread, but I hope I can be forgiven.

We found this thread as part of an increasingly desperate search for anyone who could help us migrate data out of another music library in the Software Guild format.  This one is a catalog of opera scores, sheet music, and recordings, and contains nearly 6000 entries.  It's part of the estate of an opera aficionado, and his heirs would be really, really happy not to have to scrap the entire thing.

We're able to run the program itself (it runs in DOSBOX with some coaxing, and will run without an emulator on any 32-bit Windows system, even Windows 7).  We currently have it on an old XP laptop.

I was able to track down instructions for exporting the database into a slightly less archaic software, called Organize Your Collection, which I was also able to track down.  If we can do that export, we might be able to step it up to something current.  But . . . to do that, we need the original software that is used to create the Music Library databases.  Specifically, we need an executable, GUILD.EXE.  It might be on the floppies that the OP mentioned.  It was probably part of the collection of old software that was thrown out when the original owner died.  *headdesk*  We also tried tracking down the Doug McFaul who wrote the original program, and learned that he committed suicide in 2005.

I'm fairly computer-savvy, but I haven't yet learned enough to write extraction scripts.  So I have two possible hopes here:

- [**[COLOR=#000000]rbmoler[/COLOR]**]("http://ubuntuforums.org/member.php?u=1886837"), would you be willing to help a total stranger online, by checking for the GUILD.EXE file on the original software you have?  If you have it, and I'm able to migrate this database, I'll have a solution to share.

- [**[COLOR=#000000]freebird54[/COLOR]**]("http://ubuntuforums.org/member.php?u=228502"), would you be interested in an extraction project involving another one of these databases?

Mods, if I should have started this inquiry as a new thread, let me know and I'll do so.  Thank you!

*crosses fingers*

---

