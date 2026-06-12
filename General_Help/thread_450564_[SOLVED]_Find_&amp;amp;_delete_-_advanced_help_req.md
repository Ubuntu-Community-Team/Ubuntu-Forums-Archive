---
title: "[SOLVED] Find &amp;amp; delete - advanced help required"
date: 2007-05-21
forum: General Help
---

### Post by chrismyers on 2007-05-21
Hi There...

Is is possible to do a:

Find & delete all files NOT containing "string1" & "string 2"

What tool & syntax should I use?

Is it possible to make this a recursive search?

Many thanks in advance :D

EDIT for clarification:

I'd like to stress that I wish to search the body of files for strings - not the filenames.

---

### Post by blazercist on 2007-05-21
this is an interesting question, I believe it is possible, i dont know how but I'm just posting here so I can keep track of this thread and see the solution.

---

### Post by chrismyers on 2007-05-21
Yeah....

We have a server at work that has 9 gigs of junk that needs cleaning up.

We can't delete files by date order, because some older files still have info we need.

These reports have specific headers, hence my question. I hope it's possible.

---

### Post by newlinux on 2007-05-21
Just as a pointer, this could probably be done using a shell script, the find command, and rm. Someone here who write scripts all the time probably could do this quickly... I'd have to think about it a bit, and I'm not near anything linux right now...

Edit: I should say, it's definitely possible.

---

### Post by chrismyers on 2007-05-21
Where I am so far:

grep -lir "chris" *


This lists all files containing chris

I think the next stage is to look how to use "Regular Expressions" to reverse the search.

When Ive done this I'll have to see about passing the filenames on to rm

I think I might get there eventually. Hopefully someone can give more pointers.  ;)

---

### Post by blazercist on 2007-05-21
if you do figure this out be sure to post the solution here as i think many people would find this useful and quite interesting.

---

### Post by newlinux on 2007-05-21
Find takes regexp (Regular Expressions) as well, and can execute commands on the results (using the -exec option). You actually wouldn't need to write a script using it, now that I think of it. 

[http://en.wikipedia.org/wiki/Find](http://en.wikipedia.org/wiki/Find)

has examples.

[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

Has examples of regexp.

---

### Post by newlinux on 2007-05-21
something like:

find <startingdir> -name '<regexp>' -exec '/bin/rm -f {} ;'


replace <startingdir> with the parent directory of all the directories you want to delete files with, and <regexp> with the Regular expression that matches the files you want to delete. To test, replace /bin/rm with echo or use the -print option.

I think that is about right, but I have no access to linux right now.

---

### Post by Arisna on 2007-05-21
Passing the option `-v' to grep will make it invert the search.  This would not integrate directly into the find command but may get you what you need faster.

---

### Post by newlinux on 2007-05-21
you can use -not with find to invert if you want to go that route...

---

### Post by chrismyers on 2007-05-21
> **newlinux said:**
> something like:

find <startingdir> -name '<regexp>' -exec '/bin/rm -f {} ;'


replace <startingdir> with the parent directory of all the directories you want to delete files with, and <regexp> with the Regular expression that matches the files you want to delete. To test, replace /bin/rm with echo or use the -print option.

I think that is about right, but I have no access to linux right now.


Cheers for the help..

I have had a look at your example. Is 'find' capable of looking at the contents of a file, or does is just search on the filename itself?

Am I mistakenly working with grep? Before your post, I had got this far:

grep -lirLE "\<chris\>" *

This would return a list of files that didn't contain the word 'chris'.

---

### Post by newlinux on 2007-05-21
Man, I thought you were talking about filenames, not file contents. My apologies.  Actually you would use grep with find to return files with a certain content (find -exec grep...). Or just do what you are doing with a shell script.

---

### Post by chrismyers on 2007-05-21
Sorry for wasting your time newlinux.

My fault for not being clearer.

Actually, you did give me some ideas. :D

---

### Post by newlinux on 2007-05-21
Wait, the -regex option to find works like grep. somethnig like:

find <startdir> -regex '<regexp>' -exec rm {} ;

Man, I used to be really good with find, but it seems I can't remember anything these days.

Something like that should work.

Edit: nevermind- I think that's for filenames too. wish I had a linux box with me. I swear I used to do this with find, but maybe I just wrote a shell script.

---

### Post by chrismyers on 2007-05-21
OK..

This is where I am now:

grep -lirLE "\<chris\>" *

This returns a list of files where the body does not contain the word 'chris'.

I now have to find a way to pass the filenames to rm.

I feel like I'm getting somewhere... This is tons more fun than Windows... I love Linux :D

Help appreciated.

---

### Post by newlinux on 2007-05-21
If that returns the whole path to the file:

rm -i $(grep -lirLE "\<chris\>" *)

the -i is for safety :). My shell scripting isn't up to par either...

---

### Post by ghell on 2007-05-21
grep .... | xargs rm ..

or something, fill in the ..s with what you want (I'm not sure if you can put the extra rm flags at the end, I have not tried)

EDIT: watch out for the max length, I think you can only run lines 255 characters long or something. I don't know if xargs gets past this limit.

---

### Post by chrismyers on 2007-05-21
> **newlinux said:**
> If that returns the whole path to the file:

rm -i $(grep -lirLE "\<chris\>" *)

the -i is for safety :). My shell scripting isn't up to par either...

 
This looked like it was going to work:

rm $(grep -lirLE "\<oranges|lemons\>" /test/*)

This deleted all files in the /test directory that did not contain oranges or lemons, so I went one stage further.

I created a sub folder called "untitled folder" & placed a file in there.

This time it returned an error: "rm: cannot lstat `/test/untitled': No such file or directory"

Looks like it cant cope with directory names with a space in it. Any ideas where I go now?

---

### Post by newlinux on 2007-05-21
grep -lirLEZ "\<oranges|lemons\>" ~/test | xargs -0 rm

might work. Otherwise, I'd write a shell script that where it is easier to handle spaces.

---

### Post by chrismyers on 2007-05-22
> **newlinux said:**
> grep -lirLEZ "\<oranges|lemons\>" ~/test | xargs -0 rm

might work. Otherwise, I'd write a shell script that where it is easier to handle spaces.

I've tested it & this does exactly what I need.

Many thanks for your help.  :p

---

