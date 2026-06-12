---
title: "Looking for a file manager that uses tags"
date: 2016-06-23
forum: General Help
---

### Post by Spae on 2016-06-23
I don't know what section this question should be in. My problem is that I am finding standard file system based on directories very inefficient to use.
I want a file manager/browser that allows the use of tags rather than directories. I want to be able to find files using one or multiple tags, ideally the tag list would also be browse-able so I don't have to type them out every time. I also want it to show file previews as other standard file managers can - and generally not have missing features compared to the standard file manager. 

I have searched a bit but can't find solutions. I feel like the directory based system is very outdated, not sure how others feel. One file doesn't really belong in a single category, human brains don't work like that so why should file browsers.

---

### Post by Impavidus on 2016-06-23
I don't know your brain, but mine is quite comfortable with directories. But in Linux you can put a file in as many directories simultaneously as you want, using hardlinks. For directories that doesn't work, but you can use symlinks to simulate the effect. You can use symlinks on files too. I think there are tag-based programs for managing image files, which can store the tag in the file itself.

I imagine that a tag-based file browser could exist, maybe even as a plug-in of a traditional file browser. It would need an index file of all files in your home directory, along with their tags. Internally the file system is hierarchically organised and there's no way to change that without completely redesigning the operating system.

---

### Post by Spae on 2016-06-23
I understand the file system was designed in a heierachal way and I know all file systems are like that - although I think that changing this would be interesting and not impossible. 

I was wondering if anyone had made a layer to the current file system to allow categorisations that are not hierarchal. 

In reality objects exist in multiple categories.  Our mind are not full of hierarchal folders. 

I mean, we have the search function already. But it's not indexed (at least not on my system, is it an option?). I suppose file names could be replaced by tags very easily, no major changes needed, although excessive amounts of numbers would be needed on file names that are sharing the same tag(s) as a replacement for their file names. Then if all files were indexed and search times were reduced that could be a solution. But the only problem with that is I wouldn't be able to search using multiple tags at once because the search by default can only search for one string. And that's only one of many problems so I don't see that idea as a solution rather I want it built in and functional.

---

### Post by dragonfly41 on 2016-06-23
You might find that recoll (in Ubuntu Software Centre) meets your requirements.

And as another suggestion perhaps explore zotero standalone utility (or Firefox zotero add-on). You can bookmark files with tags.

eXist is useful for XML documents in collections.  [http://exist-db.org/exist/apps/homepage/index.html](http://exist-db.org/exist/apps/homepage/index.html)

---

### Post by HermanAB on 2016-06-23
It seems that the OP is the one person in the world that needs desktop search like KDE Nepomuk or the Canonical Lense - that fancy feature that everyone else always disables...

---

