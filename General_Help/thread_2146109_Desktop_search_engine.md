---
title: "Desktop search engine"
date: 2013-05-17
forum: General Help
---

### Post by mbnoimi on 2013-05-17
I'm using [Recoll]("http://www.lesbonscomptes.com/recoll/index.html") as desktop search engine (searching in the documents content), it works fine but I noticed lately that the index files size is so huge so _I'm looking for any alternative (I prefer a solution based on Lucene)_

I googled and tested many solutions before posting this thread the last convenient result I get it [Solr]("http://lucene.apache.org/solr/") I successfully installed it under ubutnu 12.10 but it seems a search engine for servers based not for daily desktop usage... I'm wondering _is there any end-user interface for Slor?_

PS
[LIST]
[*]Theoretically Solr is the one what I'm looking for but I'm missing end-user interface. 
[*]I tested the following solutions all of them not work for me: Recoll - DocFetcher - Searchmonkey - regain - Beagle 
[/LIST]

---

### Post by dino99 on 2013-05-17
what i've found (sorry i've no clue about it)  [http://feinan.com/2012/05/19/how-to-install-solr-3-6-0-on-ubuntu-12-04-lts/](http://feinan.com/2012/05/19/how-to-install-solr-3-6-0-on-ubuntu-12-04-lts/)

---

### Post by mbnoimi on 2013-05-17
> **dino99 said:**
> what i've found (sorry i've no clue about it)  [http://feinan.com/2012/05/19/how-to-install-solr-3-6-0-on-ubuntu-12-04-lts/](http://feinan.com/2012/05/19/how-to-install-solr-3-6-0-on-ubuntu-12-04-lts/)

As I said above. I successfully installed Solr so the link you gave not related to my questions... thanks any way.

---

### Post by ajgreeny on 2013-05-17
How huge is huge?

My home is 169GB in size and contains 27981 files according to folder properties, and the db from recoll is 125MB, large but not what I'd call huge.

Perhaps you can use recoll preferences to remove some folders from the default that the system searches to produce the database.  None of my hidden folders are logged, which removes a lot of files that would otherwise be in the db, and I have added a few others as well as I know there is nothing in them that I would need to search for.

---

### Post by mbnoimi on 2013-05-17
> **ajgreeny said:**
> How huge is huge?

Recoll uses Xapian, the size of the resultant index is bigger than the indexed documents themselves while size of Lucene's index is less than the index documents... this is a known fact. For that I'm looking for an alternative.

---

### Post by mbnoimi on 2013-05-22
Bump

---

### Post by mbnoimi on 2013-05-28
It seems that no one really interest. Any way, I installed Alfresco which is using Lucene although its performance is amazing but unfortunately it deals with files as server repository not as local system files.

---

