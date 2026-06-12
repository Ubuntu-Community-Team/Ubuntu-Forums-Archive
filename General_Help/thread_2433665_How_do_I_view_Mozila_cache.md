---
title: "How do I view Mozila cache?"
date: 2019-12-23
forum: General Help
---

### Post by iamtheeggman2 on 2019-12-23
Hi,

I had been on a page on ebay showing the list of people who were bidding on an item however i cannot access this list anymore, i was wondering if I can see the page I had previously viewed by accessing the cache? I tried the about:cache however although there's a lot of links for all the sites ive been on lately, for some reason i cant find in the page anything with the name of item that was being sold on ebay or the word "bids". In windows you could search the contents of a file, is there way I can search the contents of mozialla cache folder? also where is the cache folder? Thanks in advance.

---

### Post by TheFu on 2019-12-23
Teaching you to fish ... 

There are a few different commands to search a file system for stuff.  The main two that I use are **locate** and **find**.
Both have manpages.

```
locate(1)                   General Commands Manual                  locate(1)

NAME
       locate - find files by name

SYNOPSIS
       locate [OPTION]... PATTERN...

DESCRIPTION
       locate  reads  one or more databases prepared by updatedb(8) and writes
       file names matching at least one of the PATTERNs  to  standard  output,
       one per line.
...
```
```
FIND(1)                     General Commands Manual                    FIND(1)

NAME
       find - search for files in a directory hierarchy

SYNOPSIS
       find  [-H]  [-L]  [-P]  [-D  debugopts]  [-Olevel]  [starting-point...]
       [expression]

DESCRIPTION
       This manual page documents the GNU version of find.  GNU find  searches
       the  directory  tree  rooted at each given starting-point by evaluating
       the given expression from left to right,  according  to  the  rules  of
       precedence  (see  section  OPERATORS),  until the outcome is known (the
       left hand side is false for and operations,  true  for  or),  at  which
       point  find  moves  on  to the next file name.  If no starting-point is
       specified, `.' is assumed.
...
```

Find is always installed on every Unix system that isn't stripped down to the bare minimal stuff. It is on your box right now.

locate is part of the mlocate package and needs to be manually installed.  **sudo apt install mlocate**, told to make a DB using **sudo updatedb**, then the **locate** command can be used.

**locate** will update the file list DB automatically, once a day.  Any brand new files won't show up in that DB until tomorrow. It is just a list of files, permissions, owner.  Using locate is *really fast* since it is just 1 DB file, pre-indexed.
```
$ locate cache
```
it is case-sensitive.
```
$ locate -i cache
```
is case-insensitive.

But sometimes we need to look for current files on a system.  That's were **find** shines.
```
$ find ~/ -type d -iname \*cache\*
```
is a case-insensitive search of the current userid's HOME, but only for directories.  Find can filter based on age, size, types of files.  Want only symbolic links over 20 days old?  Find can do that.  Want all files over 500MB in size over 30 days old?  Find can do that too.
```
find / -type f -size +500M -ctime +30
```

Find will access mounted network storage if you don't tell it not to do so using the -mount option.

The find manpage isn't always clear for beginners.  Examples are extremely helpful, so google "find examples linux" and some *top 10* or *top 20* or *top 35 useful* find commands will be returned.

Now you can go fishing and get your 'grep' going.  grep is a text search tool, BTW. But that is a completely different question and uses a language called regex for matching patterns of text inside files.  **find** supports using *regex* in the name globbing, if you like, and we can feed the results of find directly into grep.  You'll probably see some examples which do that.

---

### Post by iamtheeggman2 on 2019-12-24
well it looks like this wont work, mozila gzips everything to mke it smaller.

---

### Post by Holger_Gehrke on 2019-12-24
Actually Firefox stores the files in the cache in the way it got them. Most servers compress their HTML, CSS and Javascript to save bandwidth if the headers sent by the browser in the request tells them that the browser can handle this.

You could just loop over the files, check their mimetype and for mimetype 'application/gzip' do 'gunzip -c filename|grep 'bids'. Somewhat like this:
```

for i in *; do if [[ $(mimetype -b "$i") = 'application/gzip' ]] ; then gunzip -c $i 2>/dev/null |grep -i 'bids' && echo $i; fi ;done

```

Checked this with my cache searching for 'tagesschau' (a german news TV show whose website I visit regularly) and found several files.
Only problem is that neither 'mimetype' nor 'grep' are fast, so expect to wait an hour or two for this to complete ...

Holgeh

---

