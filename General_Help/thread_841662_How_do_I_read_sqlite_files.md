---
title: "How do I read sqlite files"
date: 2008-06-26
forum: General Help
---

### Post by Bari on 2008-06-26
Hi, whilst idly wandering through the hidden files in my Home folder I notice many end in sqlite which is I assume a database of some sort. I can't read these as I am informed that I don't have the necessary application installed. What would i need to install to read these files?  Do I need to know what is in them? I think I do just because I am a nosy person who likes to know whats going on under the bonnet (hood to our colonial brothers)

---

### Post by x1a4 on 2008-06-26
Hi,

.sqlite are indeed database files for a database type called SQLite.  Install the **sqlite** package, which is a command line interface to SQLite databases, and if you like, **sqlitebrowser** which is a SQLite GUI interface.

If you'd like to access SQLite using PHP install **php5-sqlite**, for Python that's **python-pysqlite1.1**.  Just do a search of the repositories for the term 'sqlite'.

---

### Post by onero on 2008-06-26
> **Bari said:**
> Hi, whilst idly wandering through the hidden files in my Home folder I notice many end in sqlite which is I assume a database of some sort. I can't read these as I am informed that I don't have the necessary application installed. What would i need to install to read these files?  Do I need to know what is in them? I think I do just because I am a nosy person who likes to know whats going on under the bonnet (hood to our colonial brothers)

I actually use a [SQLite Manager]("https://addons.mozilla.org/en-US/firefox/addon/5817"). It's a firefox extension that works really well; you can browse the DB, execute queries, even change the records (though for the most part I wouldn't do this for application DBs because I might mess something up ^^).

---

