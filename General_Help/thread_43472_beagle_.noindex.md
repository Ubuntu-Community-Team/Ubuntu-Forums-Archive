---
title: "beagle .noindex"
date: 2005-06-22
forum: General Help
---

### Post by burlap on 2005-06-22
I have installed 0.0.11.1 (libsqlite0-dev is needed to make file indexing work), and it seems a bit better, but it tries to index everything. 

On beagle page you can read:
> You can put an empty .noindex file in a directory to keep it (and all of its children) from being indexed. If the .noindex file is non-empty, the files/directories listed within will not be indexed. Wildcards are allowed.
So I placed empty .noindex files in the directories I wanted to keep from indexing. And everything was indexed. So I put * in .noindex files. Files in the directories were not indexed, but all children directories were. 

Is the only soultion to place .noindex files in each and every directory?

---

### Post by manicka on 2005-06-22
[QUOTE=burlap]I have installed 0.0.11.1 (libsqlite0-dev is needed to make file indexing work), and it seems a bit better, but it tries to index everything. 
[/QUOTE]
Half your luck. I can't get beagle to index anything properly and 0.0.11.1 still purges for me each time I log in.

---

### Post by burlap on 2005-06-22
So far, so good. It used to purge before, not only on log in, that is why I wanted to restrict indexing only to what is really usefull (documents). If it is not going to purge, faulty .noindex is not that bad, I can afford having a database of ~10000 files but I don't want it to be recreated every five minutes...

I'll give beagle a few days, I've noticed some problems when I first ran 0.0.11.1, but so far I can't reproduce them. 

[quote=manicka]I can't get beagle to index anything properly and 0.0.11.1 still purges for me each time I log in.[/quote]I have everything default - all default backends running (including liferea, and I use it a lot), but I don't use blam, gaim and tomboy (although I have created some notes and they are indexed - however, tomboy is way too unstable), I have no Google API, no networkedbeagle either.

---

### Post by burlap on 2005-06-22
Just few hours of luck: it purged, so I decided to move the description to a more relevant thread - [Beagle File Indexing](http://www.ubuntuforums.org/showthread.php?t=41999). 

.noindex doen't seem to work and I'd still welcome a solution...

---

### Post by burlap on 2005-06-23
I've just learned (browsing beagle mailing lists archive) that .noindex option was removed in favor of AddIgnorePattern (via beagle-config CLI tool and some GUI, which seems to be CVS only).

---

