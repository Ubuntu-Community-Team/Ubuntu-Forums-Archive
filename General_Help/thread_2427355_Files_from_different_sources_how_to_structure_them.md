---
title: "Files from different sources how to structure them"
date: 2019-09-21
forum: General Help
---

### Post by jenniferruurs on 2019-09-21
I want to create a database where I have many different types of datasources, for example csv, tiff, png, excel, bin.
These files are related to eachother, which I want to use for analysis purposes. 

Is there a way of how I can organize these files and that if I want to locate them that I can find in I database the relations between these files?

---

### Post by dragonfly41 on 2019-09-21
Try to expand further ..

What .. what is the "analysis purpose"?
Why .. why csv, tiff, png, bin and not text, doc
What .. what type of "file organisation"?
What .. what is a typical relationship?

---

### Post by TheFu on 2019-09-21
How are they related?  If it is a project, then I'd keep them in the same project directory.  If it is only date based, I keep directories by date.  Using a date-based directory structure, at a minimum, is a huge help for organizing all sorts of things.

Binary files are different, probably want to generate the important metadata for analysis when it is being loaded into the system.
Depending on the sort of analysis performed/planned, what needs to be pulled out from files will be different.

For computer log files, there are tools like splunk which can be used to store files for searching later.  I use **recoll** indexing to make finding files of almost any type easy to find later. Full text searching is extremely powerful these days.

For highly specialized areas, you'll have to create the analysis/indexing tools yourself.

---

### Post by jenniferruurs on 2019-09-22
For example the CSV file contains information about the images. They are related in the sense that they all have same file name (stuff (different filetypes) that is related to eachother have the same filename). But they are in to many different folders.

---

### Post by dragonfly41 on 2019-09-22
You can make a first step by viewing your csv file (which seems to be some form of catalogue) in LibreOffice Calc (assuming that you have LibreOffice installed).

File > Open > path to your csv file.

Then we can take it from there.

There are other steps to take.

---

### Post by dragonfly41 on 2019-09-22
> [COLOR=#000000]But they are in to[o] many different folders.[/COLOR]

I will add an idea which I am applying myself to keep control of hugely scattered assets.
I installed [Atom editor]("https://atom.io/") (scroll down home page to see the download button).
I installed Krusader as my principal dual pane File Manager (this does come with a lot of kde baggage which may not be acceptable to some).
I created symlinks to various folders/files scattered around my filesystem. These are "virtual projects".
In Krusader top bar I added a new Useraction -> Atom (I attach a screenshot of setup).
Now after launching Atom I can use Krusader as my "Houston Control" to launch any asset in Atom to view and edit.

Downsides.
Krusader and Atom are not for the faint of heart. Atom has a host of community packages to understand. Krusader has huge baggage.
But I have narrowed down my daily toolset to Krusader + Atom.
I can call any resource including CLI through these two tools.

---

### Post by TheFu on 2019-09-22
There are software tools called "Collection Managers".  Some are specialized and others can be customized for anything.  Movies, TV shows, music, photos, collectables, books are all common. Add Linux to the google to find linux versions of those. 

My needs are simpler, non-professional using hundreds of DVDs containing 50K+ images.  Each DVD is numbered ... 001, 002, 003, 567. The number is literally written on each disc and stored in-order in media holders.  These are backups. All the same data is kept on active disk too.

As part of burning each DVD, I create an **ls -Rl** listing that goes into a file named to match the DVD number. These are text files, easily searched using grep or indexed using any search engine you want, like recoll.  The image names and directories are part of the description.  *2013/0326-Holi/829-Kathmandu_OWASP-Aaron.jpg* is an example.  I know the year, month, day, location, purpose and who.  The 829 is strictly an ordinal to keep that image in order with all the others from the say day.  It isn't a perfect system, but it does enough, but doesn't have too much maintenance requirements.  I also add some metadata to the image EXIF - GPS coords if available, more names, more details about the other subjects and minor items in the photo. Any general "feel" or mood that the image causes.  My indexing tool knows how to pull that data out of the EXIF, so finding anything is sub-second, assuming I can remember any of the possible search terms. Often, I have to go through a few hundred image files for a specific date.  Finding the date isn't hard at all.

I specifically use relative paths, so the entire 2013/ directory can be moved somewhere else, but the ls -Rl doesn't change. Use the directories as part of the filenames. Just ensure the naming is consistent. Lacking anything else, use YYYY/MM/DD-Event/

It wouldn't work for a professional photographer, who would need at least 20 other metadata items about the photo contents.  There are specialized DBs just for that, often tied to a photo editor.  The issue with those is that they are all proprietary and all the work spent putting data into the system is usually locked up inside. In 3 yrs, when it is time to change, the data is stuck.

At some point, everyone moved to a spreadsheet or CSV. When that gets outgrown - usually around 5K records - a DB is the correct answer, but most desktop users really don't understand DBs and making it easy to update, search, and get data from is a non-trivial effort.

I worked in document management for about 5 yrs and learned lots of things about not being able to find things later.  Mainly I learned that if a librarian wasn't involved in setting up the metadata, then it can never be trusted.  End users cannot be forced to even update .doc file metadata (properties), so they don't.  What happens is every document has the information that was in the template/copied doc used before.

I worked with a professional videographer for about a year. He sold clips that are commonly used in commercial movies, TV shows, and ads.  You know the clips - like when a TV show comes back after a commercial and shows the outside a some building to establish the location of the next scene with the actors.  Clips could be 2 sec or 45 minutes. Each had about 50 pieces of description so when a client was seeking a specific setting, they could find the clip to match and make a sale.  "outside, night, old brick house, porch light on, windy, untrimmed bushes, full moon" 

Sorry for rambling. Hope it is helpful.

---

### Post by dragonfly41 on 2019-09-22
Something like [eXist-db]("http://exist-db.org/exist/apps/homepage/index.html") might help in the above scenario. It allows collections of unstructured documents and the collections can include uploading images through [extensions]("https://www.exist-db.org/exist/apps/doc/extensions").  And taking the point by TheFu that a librarian should be involved perhaps Zotero stand alone with browser connector might be added to the mix. But there are dozens of tools to try once you have an indexing framework.

---

### Post by HermanAB on 2019-09-22
There are various Document Management solutions available, for example KnowledgeTree and OpenDocMan.  Some googling will find you the gory details.

---

