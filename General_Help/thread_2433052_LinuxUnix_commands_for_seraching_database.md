---
title: "Linux/Unix commands for seraching database"
date: 2019-12-12
forum: General Help
---

### Post by satimis on 2019-12-12
Hi all,

Which Linux/Unix command lines shall I use to search files containing words/phrase on database ?
grep/find/locate ?

Example:
words - English/French/Chinese
phrases - speech to words/words to speech
etc.

Thanks in advance

Regards
satimis

---

### Post by NM5TF on 2019-12-12
grep would certainly do it

maybe awk ???
[http://linuxcommand.org/lc3_adv_awk.php](http://linuxcommand.org/lc3_adv_awk.php)

---

### Post by SeijiSensei on 2019-12-13
What kind of "database?" If it's an SQL system like MySQL or PostgreSQL, you'd need to use the native client for those systems and write a query in SQL. Something like
```
select * from tablename where field='someword';
```
That's the most basic type of matching. You can use wildcards like % ('%someword%')  or comparisons using regular expressions.

I don't how to search a Berkeley DB database since I never use them.

You can use the client in a command like this (using the psql client for Postgres):
```
psql -c "select * from tablename where field='someword'" databasename
```

---

### Post by satimis on 2019-12-13
> **SeijiSensei said:**
> What kind of "database?" If it's an SQL system like MySQL or PostgreSQL, you'd need to use the native client for those systems and write a query in SQL.  - deleted 
Oh sorry.

I meant my hard drives.

I have 2 hard drives on the PC
Drive-1 for running OS
Drive-2 for storage

Regards
satimis

---

### Post by TheFu on 2019-12-13
You can load a search tool, like recoll, point the index engine at the directories you want indexed then use the GUI search to ... er ... search.

For filenames, I use **locate -i**.
For stuff inside files in 1 directory, I use egrep ... like 
```
cd ~/bin/
egrep convert *sh

```For random searches where I don't know the filename, part of the filename or specific spelling of the words, I'll use **recoll**.

recoll has a thick client and a CLI version.  I use both, just depends.

There are a number of similar tools to recoll - beagle?  I've never used them.  Recoll has the soundex engine, so it can find stuff based on what the works sound-like, not just spelling. It also deals with different suffixes.  Recoll indexing can take a while and the index files get large.  I refresh the index weekly. Example recoll CLI:
```
recoll -b -t -q "$1"
```

locate needs to be pre-indexed too. updatedb is the tool for that.  By default it ignores anything in /media/ and /mnt/, so if you want to index stuff there, config changes are necessary.

Lots-o-methods. Each has a place.

---

### Post by Impavidus on 2019-12-13
Of course, you can only search for text in files with a file format understood by the search tool. Plain text is easy, but if you design your own binary format, you'll have to write your own search tool (or at least some sort of filter).

---

### Post by dragonfly41 on 2019-12-13
[ripgrep]("https://phiresky.github.io/blog/2019/rga--ripgrep-for-zip-targz-docx-odt-epub-jpg/") is a useful tool which can also search multiple file types.

---

### Post by satimis on 2019-12-13
> **TheFu said:**
> 
- snip -
For random searches where I don't know the filename, part of the filename or specific spelling of the words, I'll use **recoll**.

recoll has a thick client and a CLI version.  I use both, just depends.

There are a number of similar tools to recoll - beagle?  I've never used them.  Recoll has the soundex engine, so it can find stuff based on what the works sound-like, not just spelling. It also deals with different suffixes.  Recoll indexing can take a while and the index files get large.  I refresh the index weekly. Example recoll CLI:
```
recoll -b -t -q "$1"
```

- snip - 

Thanks for your advice.

I expect to find the filename which contains a phrase```

french to english

```

Performed following steps

$ sudo updatedb

$ recoll -b -t -q "french to english"```

:3:common/rclinit.cpp:308::Configuration directory: /home/satimis/.recoll
:2:rcldb/rcldb.cpp:875::Db::open: exception while opening [/home/satimis/.recoll/xapiandb]: Couldn't stat '/home/satimis/.recoll/xapiandb'
Cant open database in /home/satimis/.recoll/xapiandb reason: Couldn't stat '/home/satimis/.recoll/xapiandb'

```

$ recoll -b -t -q "french"```

:3:common/rclinit.cpp:308::Configuration directory: /home/satimis/.recoll
:2:rcldb/rcldb.cpp:875::Db::open: exception while opening [/home/satimis/.recoll/xapiandb]: Couldn't stat '/home/satimis/.recoll/xapiandb'
Cant open database in /home/satimis/.recoll/xapiandb reason: Couldn't stat '/home/satimis/.recoll/xapiandb'

```

same result

Regards
satimis

---

### Post by TheFu on 2019-12-14
updatedb is for locate. Nothing else.  Locate only looks at filenames. Nothing else and it only lets the user see filenames that userid is allowed to see.

recoll needs to be run first, configured, then run in *index mode* before you can search using it. It is looking for a set of index files in '/home/satimis/.recoll/xapiandb'.  There are a few how-to articles on using recoll if the manpage isn't sufficient.

Don't assume there is a single space between each word or that the words are on the same lines.  I would use the longest, most unique word to do a case insensitive search to get close.

---

