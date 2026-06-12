---
title: "Meta based file storage and query"
date: 2013-02-22
forum: General Help
---

### Post by cdaringe on 2013-02-22
Hi all,

It's been a long time!  Hope all is well.

I have a database-style need that I'm confident a solution must already exist for.

I have documents that belong to many catagories (1:many relationship).  I want users to be able to "browse" or filter quickly to each document.  I do not want to create folders for each category, and then place copies of each document in many folders.  I also don't want to simply store documents in a rigid folder heirarchy, where document "pertains_to_everything_document" exists only in FolderX and not in FolderY.  FolderY represents category Y, and Y needs that document! X needs it too!

I envision a web based doc uploader that the user must tag meta data onto.  Then, when a user wants to query and open a doc, he/she selects from meta, and documents suddenly begin to appear!  He or she may also be able to browse the raw folder storage or DB, too.  Perhaps a sharepoint [gross] document library-like concept without the traditional storage scheme.

Am I dreaming or what existing tools do I have?

Thx,

cdaringe

---

### Post by Old_Grey_Wolf on 2013-02-22
You mentioned SharePoint so you may want to look at Alfresco.

---

### Post by LewisTM on 2013-02-22
[Linux-based document management system]("http://www.linuxlinks.com/article/20101114192433367/DocumentManagementSystems.html")s are plenty and powerful. However, if you have simple needs, a file/folder scheme might still work for you. All you would need is to place hardlinks of documents in the appropriate folder/category. A hardlink is a "clone" of a file, not a copy, so editing one occurrence edits them all. 

The syntax is 
```
ln SOURCE DESTINATION
```
Point-and-click file managers like Midnight Commander and Krusader allow the creation of hardlinks. Nautilus only creates symbolic links which are merely pointers and are more flimsy; the deletion or displacement of the original (link target) is enough to break the whole set of "replicas".

Cheers!

---

### Post by cdaringe on 2013-02-23
hi all.  Thanks for the quick responses.  These all seem like reasonable solutions.

I left out some key parameters unintentionally on first post.  (1) Web based.  (2)  'Dummies' must be able to use it.

OpenKM inside of one of the links above looks viable.  I'm very keen on the meta association and search.  It's a little simple, and though the hardlink suggestion is somewhat elegant, it doesn't quite meet my above two reqs!

---

