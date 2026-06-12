---
title: "Hunter clone for linux? (Collection Manager)"
date: 2006-09-24
forum: General Help
---

### Post by futz on 2006-09-24
I have some pretty enormous collections of pictures (pr0n) that I use csv's to organize. I used to do it with Hunter 2.1 on windoze. I'm looking for something like Hunter for linux.

Hunter will kinda run under Wine, but it crashes often and I haven't got it to do anything useful yet.

I grabbed Tellico, but it seems useless for my purposes. Crashes all the time too.

Anyone know of a good collection manager? Or have you succeeded in getting Hunter to behave properly under Wine?

I wish I had more free time and better programming skills. There's about a dozen programs (probably more) that linux really needs and they either don't exist, or the existing ones are unfinished bug-filled junk. This is one of them, tho it's a tiny niche program, so it'll probably never get developed.

---

### Post by henriquemaia on 2006-09-25
F-Spot Photo Manager.

---

### Post by orb9220 on 2006-09-25
Gwenview
Picasa
GQview
F-Spot

all should be in synaptic

---

### Post by futz on 2006-09-25
Sorry guys. None of those is a collection manager. Those are all viewers. Not what I'm looking for at all. (And for viewing I prefer gThumb.)

Here's a link to Hunter if you want to see what it does. It's a powerful tool, and I've seen nothing else like it. 

[http://hunter.broquard-ebooks.com/](http://hunter.broquard-ebooks.com/)

There's a chance I may still get it to behave in Wine. My problems are probably caused by filename syntax differences between linux and windows.

---

### Post by orb9220 on 2006-09-25
> Anyone know of a good collection manager?

I guess I don't understand what that means since the have options to have Albums,catgories,exif info,etc... which is used to organized picture collections which mine is at about 26K of images. And have them all  organized for searching and sorting.

If you are stuck using cvs than I quess you are stuck with cvs. Since that is the first pic program I have heard of that uses it.

and another one I thought of with alot of plugins is [http://www.digikam.org/about.html](http://www.digikam.org/about.html)

---

### Post by futz on 2006-09-25
> **orb9220 said:**
> I guess I don't understand what that means
I guess not :mrgreen: 

> to organized picture collections which mine is at about 26K of images.
I have probably 40 to 60 gigs of stuff to organize at present.

> If you are stuck using cvs than I quess you are stuck with cvs. Since that is the first pic program I have heard of that uses it.
Ok, let me explain this clearer:
1. It's CSV, not CVS. Csv stands for Comma Separated Volume. Collectors build csv files for collections of files, whether they be pics or whatever type. The csv files contain filenames, crc value and filesize and the sub-directory it should be stored in for each file in the collection. Hunter takes the csv file and searches thru your files and finds any file that matches the data in the csv and puts it in the proper collection. Then it generates a csv file of what you're missing. You can take that and generate a filter for Agent or other good newsreader and use it to find the files you're missing.

2. Hunter is not a "pic" program. It is not a picture manager or viewer. It is a collection manager.

> and another one I thought of with alot of plugins is [http://www.digikam.org/about.html](http://www.digikam.org/about.html)
Another viewer

---

### Post by henriquemaia on 2006-09-25
Sorry, I misunderstood what you wanted. You can try [Tellico]("http://www.periapsis.org/tellico/"), which is a is a [KDE]("http://www.kde.org/") application for organizing your collections (description from its own site).

On the features, it's stated:

Imports Bibtex, RIS, CSV, and many other formats

Maybe this helps.

---

### Post by futz on 2006-09-25
As I said in my first message, Tellico just doesn't work. I've spent the time with it, and I've gotten nowhere. It imports a csv and then... does nothing... and then it crashes. WTF! Found it to be totally useless. It's aimed more at book collections anyway.

---

### Post by henriquemaia on 2006-09-25
What about a solution using apache/php/mysql? There quite a few options around. I have tried once to build my collection of movies and some are really great.

---

### Post by henriquemaia on 2006-09-25
Have you tried this?

[http://www.gcstar.org/index.en.php](http://www.gcstar.org/index.en.php)

---

### Post by futz on 2006-09-25
> **henriquemaia]What about a solution using apache/php/mysql? There quite a few options around. I have tried once to build my collection of movies and some are really great.[/quote]
[QUOTE=henriquemaia said:**
> Have you tried this?
[http://www.gcstar.org/index.en.php](http://www.gcstar.org/index.en.php)
Ummm... No. Neither is what I'm looking for. Gcstar is the same kind of thing as Tellico and just isn't what I'm looking for. 

Tellico and gcstar are just little special purpose databases. Hunter is not the same thing at all.

Hunter is a file hunter, verifier, renamer and sorter. When you've Hunted a collection, you KNOW with 99.9% certainty that you have the correct files (verified with crc matching) with the correct names, and how many of them you have. You've got them automatically sorted into individual directories. You know exactly which ones you're missing or if you have the complete set. And you've got missing file csv reports that you can use to filter for the missing files.

You don't have to type any of this info in. It's all contained in the csv files, generated by other, even crazier, collectors. :mrgreen:  You can generate your own csv's with it if you want to.

Like I said, Hunter is pretty unique. I haven't yet seen anything else that does what it does. I'm pretty sure I could knock one together with Python or C or Perl or even Ruby, but for that I need free time to polish my rusty programming chops. Maybe work will slow down next month...

---

### Post by CaveRat on 2006-09-26
> **futz said:**
> Sorry guys. None of those is a collection manager. Those are all viewers. Not what I'm looking for at all. (And for viewing I prefer gThumb.)

Here's a link to Hunter if you want to see what it does. It's a powerful tool, and I've seen nothing else like it. 

[http://hunter.broquard-ebooks.com/](http://hunter.broquard-ebooks.com/)

There's a chance I may still get it to behave in Wine. My problems are probably caused by filename syntax differences between linux and windows.

Just a thought. Have you tried sending the author an email asking how to either get it to work in Wine, if he/she knows a Linux Guru who has got it to work, or if he/she knows of a good Linux alternate hidden out there somewhere? It might be worth a shot.

---

### Post by mar9tin on 2006-10-15
Well Vince would certainly know if it will.  He's a computer science prof.  I don't see why it wouldn't, but perhaps futz should hunt and verify by crc alone and not the default which is crc and filename.  However, I've been told by a Linux user that he is using The!Checker with Wine.  The!Checker is a similar program and is here:  [http://ourworld.compuserve.com/homepages/vhorch/piccheck.htm](http://ourworld.compuserve.com/homepages/vhorch/piccheck.htm)

May have to bypass reg: wine PICCHECK.exe "/iniloc"

Good luck!

Martin

---

### Post by haruki on 2007-06-03
futz, I happened upon this thread during my own search for something like hunter for linux.

I am curious, as it's been seven some months since the last post on this, did you ever find a program that works for you, or start work on your own?

I've searched on off for a while with no luck of my own.

Does anyone else have any recommendations or pointers?

Thanks!

---

### Post by haruki on 2007-06-05
Quick update, as suggested in this tread I emailed Vic Broquard (the mainter of Hunter) to ask if he knew of a Hunter-like project for linux or if he had any recommendations in regards to Hunter on linux in general and he said that no, he didn't, and that he knew nothing about linux. So, that's that.

There must be somebody who collects pictures on linux who has a solution though, and I'm guessing it's a cool clever little script they've writtend for themselves too.

---

### Post by futz on 2007-06-08
> **haruki said:**
> futz, I happened upon this thread during my own search for something like hunter for linux.

I am curious, as it's been seven some months since the last post on this, did you ever find a program that works for you, or start work on your own?

I've searched on off for a while with no luck of my own.
I've found a program that works perfect with wine. After one quick test it seems to be easier to use than Hunter too. Hunter was always a bit more complex than necessary, I thought.

The program is called **The!Checker**. You can get it here:
[http://ourworld.compuserve.com/homepages/vhorch/piccheck.htm](http://ourworld.compuserve.com/homepages/vhorch/piccheck.htm)

EDIT: Just now saw Mar9tin's post (3 above this one) suggesting the same program.:tongue:

---

### Post by futz on 2007-06-09
> **futz said:**
> After one quick test it seems to be easier to use than Hunter too.
After MUCH more testing, I'm sold. The!Checker is a super nice program. Works great, does everything I need and plays nice with Wine. It's a full replacement for Hunter.

---

