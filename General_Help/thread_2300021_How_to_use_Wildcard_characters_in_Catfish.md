---
title: "How to use Wildcard characters in Catfish"
date: 2015-10-23
forum: General Help
---

### Post by Ralph L on 2015-10-23
Would somebody explain to me what wildcard characters Catfish supports and how to use them.  I tried a Catfish search for *.* and it didn't find a single file.  Plainly, I don't know how to use the * wildcard in Catfish.
Any help appreciated........

---

### Post by TheFu on 2015-10-23
[https://help.ubuntu.com/community/Catfish](https://help.ubuntu.com/community/Catfish)

Almost all searches performed in non-toy interfaces use something called a "regular expression".  This is a pattern matching language.  It is also called "regex".  Perl, Python, grep, Ruby, all use regex for their pattern matching.  Most GUIs created for Unix do as well.

So ... *.* is something you learned in MS-DOS. It doesn't mean the same thing in regex or on Unix/Linux.  Regex is very complex, but very easy to get started.  Try "*" without the quotes to find stuff.  [http://www.regular-expressions.info/](http://www.regular-expressions.info/)  has a quick start.  With just a tiny bit of knowledge, you'll be able to accomplish amazing things with regex that you never knew was possible.

I've never used catfish. Always use **locate**, **find** and on desktops full of documents, **recoll**. Recoll is like google for your computer-amazing.

---

### Post by Dennis N on 2015-10-23
I use it quite a bit. It will match a string of characters within the filename without needing any wildcard character, like search for the string **heart** in my music directory will output these (among others):

Pink_Floyd-Set-the-Controls-for-the-Heart-of-the-Sun.ogg
10_Heartbeat_City.ogg
12 - Black_Hearted_Woman.ogg
03 - sgt_peppers_lonely_hearts_club_band.ogg
09_Heart-of-the-Sunrise.ogg

Check that Filetype filter is not set to something which would restrict expected output, and that modification time is not set and restricting output.

---

