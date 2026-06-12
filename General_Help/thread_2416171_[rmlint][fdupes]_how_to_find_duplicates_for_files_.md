---
title: "[rmlint]/[fdupes] how to find duplicates for files which i point"
date: 2019-04-06
forum: General Help
---

### Post by alex346 on 2019-04-06
Hey,


 I have huge problem. There is a lot of dirs and lot of files ( few TB's). COntents of that dirs are very mixed, but I am going to make some ordered hierarchy in the other place.
There is a lot of duplicates of files. 
There is a tons of them.
Files are different - all file types possible. (my archive from 10+ years)


I have to make order in photo files - ex from one holiday tour:


So, I am putting some files to side storage and I treat that as the good one. Any duplicate of them should be removed from any other storage. 
**I would like to find any solution to point only that files as an input to looking for their duplicates.**


**So I would like to start rmlint/fdupes tool to find only duplicates that specific files which I prepared in 1st step.**


Is that doable?


I have tried with grepping looong list of output file from rmlint but when the grep finds the . (dot) in string it trying to use any character. And some of these files have long names, and lot of dots in    name :( 
So that is unusable for me - I suppose.


regards

---

### Post by TheFu on 2019-04-06
I can't tell what you understand and don't from the question. Take this as information for lurkers, if you know it already.

If there are only specific files you want, then search for files of that size in the directories involved.  Store that list in a temporary file. Use 'find'.
If you like, you could look for all the image files with the same extension over a certain size to limit what is found. Deleting larger files first helps most.

**find** has all sorts of options. The best way to learn it is to look for examples online. There are many, many, examples on how to search by names or sizes or file ages.  You can also control the file attributes which are displayed, but I usually start with -ls as the option, then use either awk or sed to remove columns that aren't wanted.

A few years ago, I wrote a perl script that would find duplicate files.  It was extremely custom for my situation, has external dependencies and perl modules, so wouldn't help you much.  Wrote it after someone asked a similar question on /. for duplicate files. I had a few hours and this sort of problem is interesting enough, but not so complex as to be impossible to solve in that time.  In the end, my script generates a shell script with mostly comments, but some "rm" lines too.  I've never trusted it enough to just run the output without manually looking through all the lines. There's something funky in how it picks which of the dups to be removed that I've never looked into.  Just ran it on my tiny "Pictures/" directory and the output was 175 lines - so about 58 rm commands.

For all my photos, I use a .../yyyy/MM/dd-event-location/ directory structure.  Any photos outside my core photo storage area are duplicates, though it does take some time to process new photos sometimes.  I always process a full day, so that limits my confusion. That's the theory. I probably have some unprocessed days in 3 different locations. They are all backed up, daily, constantly. Such is life.

I've never looked at fdupes. Sorry.  The manpage for it ... [https://manpages.ubuntu.com/manpages/bionic/man1/fdupes.1.html](https://manpages.ubuntu.com/manpages/bionic/man1/fdupes.1.html) seems like it would work.

I can't imagine that dots in a name would matter at all.  Unix doesn't see dots as special characters in filenames.  Extensions don't matter to any of the shell commands, just some GUI tools care, and some humans.  The OS doesn't.

grep uses a pattern matching language called regex - or Regular Expressions.  Knowing this language is extremely helpful because most shells use it too (many people don't know that) and so do almost all Unix commands.   For example, **ls *.jpg** is really the same as **ls *jpg**.  The period in regex matches *any* character.  MS-Dos and Windows care very much about that period and it is required for their pattern matching, but Unix does not.  You can look for files with 'Z' anywhere in the same using **ls *Z*** on Unix. Windows will cry with that input.   If you actually want to find a dot, then escape it like this **ls *\.jpg**.
Another common technique to reduce the number of files being handled at any time is by doing the same command on all files that begin with 'a' at once.  **ls a*jpg**.  Then work on 'b', and then 'c' ... you get the idea. You can use ranges **ls [a-k]*jpg** if you like.  Or all lowercase- **ls [a-z]*jpg **- folllowed by all uppercase **ls [A-Z]*jpg**  and numbers **ls [0-9]*jpg** .  How you split them up is up to you and your needs.    Any command that takes filenames as inputs can use this, since the "globbing" is performed by the shell. The shell is usually bash.  Globbing is a real term you can search in google.

---

