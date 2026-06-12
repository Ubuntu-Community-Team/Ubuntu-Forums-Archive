---
title: "Need advice for collection management: bookkeepeing, backup, searching."
date: 2020-01-06
forum: General Help
---

### Post by antib on 2020-01-06
I need to manage a huge collection of different data type files.

There are several versions of backups of my collection of fiction and non-fiction books and comic books in different formats, Python scripts, lections, etc. Also there are several extractions from other people collections (which surprisingly include their backups of my collection), backups of data files from work and other stuff I can't define without writing another wall of text.

Now I need a tool, to bring some order into this chaos: kill duplicates, make searchable catalogue of collection, with a link to actual file. In ideal condition it should support tags for searching, or how do I place in folders (for example) modern tourist's guides, collection of century old maps and some DnD fan's manual on how to draw a really epic dungeon map. 

I would like advice on this topic, preferably based on personal expirience.

---

### Post by dragonfly41 on 2020-01-06
Takes a bit of setting up but I would give [eXist-db]("http://exist-db.org/") a try as a longer term experiment.
If it is good enough to archive the works of Shakespeare ..

There are python frontend client scripts. Or use the IDE.

Then I would add concordance tools to analyse your corpus.

and ripgrep for searching content via command line.

In short there is no single tool ..  "a tool" .. use a toolchain.

[added thoughts]

The suggested concordance tool in the toolchain .. [AntConc]("https://www.laurenceanthony.net/software/antconc/").

And use Zotero for indexing references. Browser connector plus standalone.

You might also need pandoc.

Then there are [carto maps]("https://carto.net/") you refer to.

These should get you started.

---

### Post by oldfred on 2020-01-06
I have not used either of these, but they still are in repository of 18.04.
Not sure if updated to python3 or not. 

Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

---

### Post by TheFu on 2020-01-06
A few thoughts.  

What does "huge" mean?  3PB?  50TB?  50MB?

There are lots and lots of different ways to parse this issue.  I've never worked in a formal library, but I do have experience in document management in some environments, corporate, govt, and at my home.

IME, the first thing that must be accomplished is what a librarian does.  There is NO replacement for a competent librarian to categorize each file, make metadata as correct as possible, and setup reasonable organizations for those files.  Different sorts of files are best served with different organization structures.  I have structures for code, books, music, videos, photos, project files and general documents.  I don't have good structures for random images and usually just depend on EXIF or filenames.  The goal is to make is as simple as possible for humans to follow or they won't.

For programming stuff, use **git**. There's a reason it won the DVCS tool wars. It is amazing.  I was a professional developer for over 15 yrs and have used all the tools.  Today, I use git.  It is that good.

For books, I use Calibre. That is mostly because it can convert between formats and works with my tablet devices for pulling books in the right format to be read. My tablet also works with my local library, so checking out ebooks from there is pretty easy too.

For media files - video, audio, I use Plex, but there are other solutions. I wish there were F/LOSS alternatives to plex which met all my needs. Alas, there are not.  The biggest thing plex does is transcode media for the end device required codecs. If you don't need that, miniDLNA or Kodi could be alternatives.  I use Kodi as a plex client every day.

For photographs, I use a custom-built web gallery. I've added notes and GPS coordinate handling because the defaults for the gallery software weren't sufficient.  I've been using the same software over 20 yrs now. It isn't pretty, but I have complete control over the data being stored. It isn't buried inside a complex DBMS.

As for searching, the more accurate the file metadata is, the better search results will be.  Bad metadata can make searches difficult.  The perform the indexing and searches, I use **recoll**.  With helpers, it can look at all sorts of files, though I've never tested it using GPS information. Recoll has both a GUI and CLI interface. It is like having a local "google" - it is fast and pretty great.
```
$ time recoll -b -t -q "Scalzi tale"
file:///D/ebooks/Library/John Scalzi/Zoe's Tale (1119)/metadata.opf
file:///D/ebooks/Library/John Scalzi/The Human Division (1121)/metadata.opf
file:///D/ebooks/Library/John Scalzi/Zoe's Tale (1119)/Zoe's Tale - John Scalzi.epub
file:///DD/DVD/dvd-all-on-istar-disk.txt

real    0m0.022s
user    0m0.012s
sys     0m0.004s
```
There is a description in the opf file ...* first time in print&#8212;the first **tale** of Lieutenant Harry* .... so that file specific file makes perfect sense in the results.  There are more than 12TB of files on that machine. The results took only 0.02s. Basically, instantaneous to a human.  Recoll is the easiest of the indexing and search tools that I've found that was also extremely complete.  I've used million dollar cataloguing software that was much.  [http://www.linux-magazine.com/Issues/2018/212/Tutorials-Recoll](http://www.linux-magazine.com/Issues/2018/212/Tutorials-Recoll)

There's also Alfresco, which is used as a replacement to the expensive document management systems like Documentum.  I ran an Alfresco server using their default web GUI for a few years before deciding it was overly complex for almost everyone.  Turns out that most "successful" Alfresco deployments, bring in specialized developers ($250K) who are only allowed to work with the non-F/LOSS ($25K/ea) Alfresco version.  Upgrading Alfresco was always a pain.  Haven't had that issue with recoll in about 8 yrs running it.  whitehouse.gov ran with an Alfresco back-end under the prior administration while using a drupal front-end.  Those prices were averages about 7 years ago shared inside the Alfresco community.  So, if you had production, DR, and pre-prod Alfresco, then you'd spend $75K on those licenses alone.  The F/LOSS versions of Alfresco will not work with any commercial DBMS.

When adding/fixing metadata, be certain to consider how you and others might search for that specific document. A document that cannot be located later, is useless.

Besides recoll, there are other many other search tools - I think beagle is one.  

Regardless of the type of file, I play the role of librarian and carefully organize stuff.  Good organization is key.

As for collections of physical objects, none of mine are so large that I can't just look on the shelves to find them.  I do keep a spreadsheet with all my model aircraft, but that is more to ensure I don't accidentally buy one I already have and to capture technical data about the models that isn't visually obvious, like the scale.

---

### Post by antib on 2020-01-07
> **oldfred said:**
> I have not used either of these, but they still are in repository of 18.04.
Not sure if updated to python3 or not. 


I tried those tools before - theese are software versions of library cards drawers. May be good when one has piles of books and papers IRL, not files on a  hard drive.

For other advices, I thank you for food for thought, I need time to understand them.

---

### Post by TheFu on 2020-01-07
I see nobody answered the duplicate file question.  Everyone has those.  

There are tools which can find duplicate files. Heck, I wrote one in an afternoon as a programming exercise.  Finding the duplicates isn't hard.  It is choosing which to delete that is difficult, especially when there are 10 HDDs connected to a system.  The first issue is defining for your needs what a "duplicate" file actually means.  **fdupes** is probably the best tool. [https://www.tecmint.com/fdupes-find-and-delete-duplicate-files-in-linux/](https://www.tecmint.com/fdupes-find-and-delete-duplicate-files-in-linux/)

---

### Post by antib on 2020-01-11
Actually I have to add to my question in part about duplicate files:  what abot duplicate images and scanned PDFs which are same contetnt but  with different resolutions?

I recall now I used gqview years ago  in Debian, it could search for similar images in different file  resolutions. I tried  to check gqview now, but either way it is severely  downgraded or has those functions hidden/turned off by default and I  could not find them.

---

