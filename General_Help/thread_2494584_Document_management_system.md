---
title: "Document management system"
date: 2024-01-20
forum: General Help
---

### Post by jeebasa on 2024-01-20
Hi All,

Considering the amount of files of different types that need to be handled nowadays, such as pictures, pdf, text files (code), I'm looking since a while for a solution that would cover different needs:


[LIST=1]
[*]When creating folder or file, the tool would ask for a name, link with another file/folder/existing project and automatically create it and store it using a predefined name structure (I.e. date and name) / process / path
[*]Each file or folder would be accessible via a single short ID (Like Git is doing)
[*]For collections, for example collection of books, plants or whatever, a dedicated structure would be necessary with a single ID for each item and a defined structure
[*]To find file/folder document,; an index would exist with a search engine for full search (document content and metadata)
[*]A version control would be implemented by default with different status (open, on-going, released, etc.)
[*]Planning tool would also be integrated, with reminders by email for review of some documents
[*]Accessible via a web browser interface
[*]Possibility to export for backup the index structure
[*]Possibility to work with a NAS
[/LIST]

Of course, an open source solution would be appreciated...

I already spent quite long time looking and testing different applications, none fulfilling all those options.

Any idea or name of a solution that would exist ?

Thank you in advance.

Best Regards,

---

### Post by MAFoElffen on 2024-01-20
Here is an Content Contributor Author from RedHat who went on his own journey searching for the same: [https://www.redhat.com/sysadmin/file-server-to-dms](https://www.redhat.com/sysadmin/file-server-to-dms)

Here was only one follow-on to that article:
[https://www.redhat.com/sysadmin/install-seeddms](https://www.redhat.com/sysadmin/install-seeddms)
...though he promised more.

I don't see anything else after that, and nothing from him after August 2021. Maybe contact him and see where that went?

---

### Post by HermanAB on 2024-01-21
I have used Opendocman.

---

### Post by jeebasa on 2024-01-27
Hi MAFoElffen,

Thanks you for the inputs, highly appreciated and very promising.

DMS seems indeed to be the way to go but not solution seems to be implemented by default on linux ditri and most require advanced background for proper implementation and maintenance.

I will anyway investigate on the link you provided to me on RedHat. 

Best Regards,

---

### Post by jeebasa on 2024-01-27
Hi HermanAB,

Thank you, will also investigate this one.

Best Regards,

---

### Post by TheFu on 2024-01-27
I worked with, installed, and maintained document management systems for decades. Initially I worked on a team that wrote our own for a specific client.

You didn't say how many users or how many documents will be in the system.

Here's what I can tell you.

Where the documents are initially placed matters.  That usually requires a full-time librarian - someone versed in library science.  This basically comes down to organization in ways that other people can understand.  Without this, you'll end up with lots of "misc" areas that don't really fit neatly into any category.

Document metadata is the best way to make finding a document later easier. However, nobody - NOBODY - fills that out correctly unless it is their job and they will be fired if it isn't correct.  Trust me. In the end, we've always had to ignore document metadata because none of the document creators bothered, unless the document was machine generated and added the correct metadata automatically.  In a home, this will never happen.

Documents that cannot be easily found later are useless.  That generally means it is part of a major category that is easily found - say "Bills" - and it is placed into the correct structure for the category.

99.999% of the time, people will use full text search to seek documents, but they never know the name. The trick here is to insist that all documents loaded into any DMS are stored with at least 4 keywords likely to be used later.

The single most important metadata for any document is the creation/update date.  Nothing is as important. Nothing.  A document created 20 yrs ago is only important when searching for 20 yr old documents, not more recent documents.  the year is the best timeframe for large buckets for a number of reasons.  Sometimes, a month is useful as well, but without the month, it isn't THAT hard to find a document later if you have the correct year.

I've been exposed to all levels of document managers. From organized directories to $10M software + $20M hardware systems.  The best system I ever used was from Xerox called docushare.  We had a librarian who worked with the different groups in the company to ensure documents were added to the correct places by each group.  DocuShare was pretty cheap in the space, but Xerox decided to start charging by the number of documents placed into the system, which was their downfall.  A system with excellent value for the cost became hugely expensive.

Around 2010, I implemented a DMS for a few small companies based on Alfresco.  This is an enterprise capable DMS with all the bells and whistles of Documentum, but for a small situation, the overhead was just too great.  The users didn't care to know about the underlying DMS and insisted on manually creating versions, though Alfresco would automatically hold 25 versions under the same document title.  It was just too hard for the users to understand this.  In the end, they used it like a file server with shared storage, so I made it available as a CIFS share to them and ignored it.  It wasn't worth the fight.  When it was time to upgrade the OS and software, I backed up all the content and dropped it onto a file server with the same organization.  It quickly became a mess without someone who cared to perform the librarian duties.  

So, what I can suggest is this:
Use a hierarchy based system.
{Group}/{Category}/{Year}/{month}/{descriptive document name-01}

I use different systems for different needs.  For example for ebooks, I use calibre. For Music, I use a file system with different players having read-only access into the file system.  For Financial stuff, I don't have bills or receipts scanned (100% paper on those), but for monthly statements and tax stuff, those are in categories with YYYY sub-directories.  I keep all financial stuff either in Quicken or in Quickbooks for the businesses, so that's how I can quickly find receipts and bills for any specific month.  Just find the date in Quicken, then find the folder holding the paper for that year. I use a paper filing system FIFO.  January will be at the bottom of that stack. December will be on the top.  If I'm looking for a bill/receipt from July, I'll start in the middle of the stack. Usually in about 10 seconds, I'll find what I seek.  Very simple. Trivial to implement and every 10 yrs, I have a folder to be shredded and still be within legal document retention requirements.  

There is a trick.  Anything bought with more than a 10 yr warranty/life, goes into my "forever" file.  For example, my roof has a 30 yr warranty, so in about 11 more yrs, that warranty will be over. The warranty, receipts, and cancelled checks are all together for the roof.  Hardly anything has a warranty of 10 yrs, so there aren't many things in that file.  Additionally, in Quicken, I note the warranty in the transaction record.

It is all in how the documents are stored, specifically, so they can easily be found later.

For example, 
Music, Books, Photos, Financial, Family, are my high level groups.

Versioning seems like a great idea, except the user's need to understand it and not manually do it.  Programmers used to version control will be easy.  Project managers will fight and ignore you.
You didn't mention security at all. Will everyone have access to all documents .... over a web interface ... really?  That seems like a terrible idea.

Have you considered tools like Nextcloud?  While I wouldn't allow them to be accessed over the internet without a full VPN being used, they are popular and easy to understand.  However, the search facilities tend to really suck.  That's putting it nicely.

I think having a single ID known to humans is a waste of time.  If a human needs that magic number for any reason, then the DMS is a failure.

Spent the last few minutes looking at document management system youtube videos.  For scanned documents, PaperMerge was impressive.  I don't know if there's a way to pull all documents out and place them into a file system hierarchy.

Most real DMS don't store documents in a file system. They are stored inside the DBMS, which means that will grow to be very large. It also means that you'll want an excellent DBMS to be used, so Postgress is the only F/LOSS DB I'd use. 

Doubt I've been too helpful. Feel free to ignore me.

---

### Post by jeebasa on 2024-01-28
Hi TheFu,

Inputs are always helpful and welcome, thank you for detailed feedback and return of experience.

I should have precised that my request was for private use, i.e. without dedicated team maintaining the overall architecture but for example a family shared NAS.

About the hierarchy based system, it is the way I work so far but the limitations are highly problematic to me, let me give you two examples:

_Library:_ When coding, e.g. python or Latex, I like to define some libraries (python) or preambles (Latex) that I can reuse from one single location without need to make a copy in each folder I'm working with. For this reason, I need to defined a "root" folder for such elements that is not linked to any date or year, and with version control. A simple "repertory URL", reduced via URL shortener to reach a file with defined versions would be perfect and extremely useful.

_Picture :_ Let's imagine you need to search for a project all the pictures of a family members. Using a date based approach, you would need to open all folders to check whether or not the folder contains a picture of this person, making the overall process extremely long. Of course a specialized software would make the trick but what if you need to search both pictures and documents in which this person appears or any files you got from this person ?

_Collection :_ Imagine you collect plants and want to maintain traceability electronically. A new entry template can be defined (Name, origin, conditions of culture, etc.) ans used to created a file for each not entry. But how to stored the files ? Here as well, it will not fit with a date based system: in case you search for a certain plant, you don't necessarily remember when you created the entry... You would search based on what you see: It looks like a tulip, it's red, what possibilities do I have fitting those characteristics ?

It seems that because no dedicated option exist, best is to consider two options:

1. The dual approach you suggest: dedicated tools for files type (doc, music, pictures, movies, etc.) then a hierarchy based sorting out

2. Second approach I start to investigate is a self hosted wiki (for the hyperlinks, so that you can jump from one topics to another easily) combined with powerful self hosted search engine: by typing "red tulip", options would be proposed just like known search engine, by clicking I can navigates between proposals. Here as well, no native solution exist but who knows... 

I continue to investigate :)

Best Regards

---

### Post by TheFu on 2024-01-28
> **jeebasa said:**
> Hi TheFu,

Inputs are always helpful and welcome, thank you for detailed feedback and return of experience.

I should have precised that my request was for private use, i.e. without dedicated team maintaining the overall architecture. 

Library

Picture

Anyway, it seems that because no dedic

It this is for 1 person, I'd just use a carefully organized file system and **recoll** to index everything for when you need to search.  

Good organization is key.  In general, I use YYYY/MM-{description}/ as the basic outline.

Recoll is an amazing search tool, basically it is like google for your computer.  Searches of everything are sub-second, but indexing can take time, depending on the content.  I've had recoll indexing my NFS server for about 5 yrs now.  I use it to find all sorts of files and content.  I'm a non-GUI person, much prefer CLI interfaces, so I don't really use the Recoll GUI for anything, but have a little script that searches from a terminal using metadata in much of the content - think ID3 tags for music/audiobooks and MKV info for videos.  Of course, it can search PDF, spreadsheets, images with metadata, emails, text, csv, html, basically any sort of content that isn't held inside a DBMS only.

Some example directory structures:
Photos: ```

gallery/2008/02-Hong_Kong0209-Sat-Big_Buddha/
gallery/2013/03-Nepal/0326-Holi/
gallery/2017/11-Chile/1129-Las_Torres_Hike/
```

Music:```

Music/Rock/l/Led_Zeppelin/Physical_Graffiti/
Music/Funk/Kool_n_the_Gang/Greatest_Hits/
```

Financial:```

Financial/Bank-A/YYYY/yyyy-mm-checking.pdf
Financial/Bank-B/YYYY/yyyy-mm-savings.pdf
Financial/Broker/YYYY/{Account}/yyyy-mm-statement.pdf
```

I use a paper filing system for bills and receipts.  [https://blog.jdpfu.com/2011/09/27/document-filing-made-easy](https://blog.jdpfu.com/2011/09/27/document-filing-made-easy)  It is really easy, takes almost zero time, and makes finding things fast based just on the approximate date of the receipt or bill. Less than 10-15 seconds to find almost anything.

For video/TV/Movies, I use the layout required by Kodi/Plex/Jellyfin.  It works well enough and allows multiple disks to be added, while merging all the content into a single view inside the tool used.

Not sure if this is 100% clear, but I don't allow spaces or "funny" characters in directories or filenames. Those break my scripts sometimes, so it just isn't worth it.

BTW, thanks for helping me notice I don't have the PDF statements for 2023 from my broker. I need to go download those.

---

### Post by dragonfly41 on 2024-01-30
I will throw in some references to tools I have looked at. I agree that Recoll is one tool to add to the toolbox.
> [COLOR=#000000]Where the documents are initially placed matters. That usually requires a full-time librarian - someone versed in library science. [/COLOR][COLOR=#000000]
You might explore Zotero for various collections. You can create private groups and collections.
[/COLOR]> _Library:_[COLOR=#000000] When coding, e.g. python or Latex, I like to define some libraries (python) or preambles (Latex) that I can reuse from one single location without need to make a copy in each folder I'm working with. [/COLOR][COLOR=#000000]
I use [CherryTree]("https://github.com/giuspen/cherrytree") as a notes editor which can be organised in different files as containers for different subjects. In particular in each node a codebox can be created in each node to hold Latex (or other languages).
Other thoughts are to try Obsidian and research "vector databases". [/COLOR]such as here: [https://milvus.io/](https://milvus.io/)[COLOR=#000000]
[/COLOR]Another category of tool is "zero trust vault" for encrypted data.
Then there are Jupyter NoteBooks.
I am trying to put jumbled ideas into practice as I migrate from a chaotic Ubuntu 20.04 to a fresh 22.04.
[COLOR=#000000]

[/COLOR]

---

