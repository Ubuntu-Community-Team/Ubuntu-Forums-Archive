---
title: "command line help - list and delete files excluding a certain character"
date: 2008-04-09
forum: General Help
---

### Post by dylanologist on 2008-04-09
I need some help formulating a few terminal commands.

I combined two separate directories (with numerous subdirectories) with music files in them, but many of the files overlap.  The only difference between the overlapping files is the presence of a "-".  Ex.:

01 Extraordinary Machine.mp3
01 - Extraordinary Machine.mp3

I need to (A) list all files (including subdirectories) WITHOUT the "-" in the filename.  That way I can look over the list and make sure they are all safe to delete.

Then I need to (B) delete all files (including subdirectories) WITHOUT the "-" in the filename.

Then I would like to (C) delete all empty subdirectories.

Obviously I will back up everything first, so that if something goes wrong I don't have to weep about it, but there are quite a large number of files (maybe 3500 or 4000) so backing up and reinstating takes some time.  Thus, I would rather get it all right the first time.  Any help is greatly appreciated.


Edit:

Alternatively, I could search for all files that begin with:  [digit][digit][space][letter or digit]*.  That would exclude all the files with a "-" as the fourth character.

---

### Post by fguilhon on 2008-04-09
You can list the files you want with:
```
$ ls -R --hide \*\ -\ \* -1
```
But I don't know any options to rm to achieve your goal... so, that means shell scripting...
Hope that helps..

---

### Post by fguilhon on 2008-04-09
Okay... find command does the job
To list files with " - " in it:
```
find . -not -name \*\ -\ \*
```
And to delete them:
```
find . -not -name \*\ -\ \* -delete
```

---

### Post by bodhi.zazen on 2008-04-09
find is the way to go ...

FYI, in case it is helpful, you can also use grep :

```
ls -R | grep -v -
```

also, with find, you can use a command with the -exec flag

find . <expression> -exec rm -i {} \;

using rm -i will ask for confirmation before deleting.

You can use the rm -r to remove directories, rm -ri for confirmation.

---

### Post by dylanologist on 2008-04-10
Thanks for the help guys.

The only problem with those solutions is that they seem to list directories without the "-" in the title, as well as files, and I don't want to go and delete a whole bunch of directories unless I know that they are empty (in fact, those commands would find (and in some cases delete) nearly every folder in my music collection).

EDIT  I just realized that the difference between rm and rmdir would mean that those proposed solutions actually probably would have worked. EDIT

I was unaware of the "find" command, and I as looked into it I realized it will be a useful command to know even if it didn't solve this problem.  It seems a bit more user friendly than the "ls" command for some reason.  For one thing, it allows me to easily remove my empty directories from my music folder:

find -type d -empty -exec rmdir {} \;
or
find -type d -empty -ok rmdir {} \;   (asks for confirmation)

I definitely thank you guys for turning me onto that command.  I did solve my main problem by working within Amarok though.  I created a playlist with my entire collection and then within the playlist searched for:  filename:"-"
I removed those files from the playlist, cancelled the search parameters, and the remaining files I deleted through Amarok.  For some reason I expected the command line to be better at this sort of thing, and never really thought about how simple it might be working through a GUI program.

It's not a perfect solution as I may still have both files in cases like this one:

14 - Four White Stallions - Bonus Track.mp3
14 Four Whitle Stallions - Bonus Track.mp3

Thanks again for the responses.

---

### Post by stylishpants on 2008-04-10
You could find your remaining dups by taking your list of files, removing all spaces and hyphens, and printing the original filenames of all the duplicates.

```

# Simple version, just prints the mangled version of each duplicated filename
find . -type f -printf "%f\n" | sed 's/[- ]//g' | sort | uniq -d

# Long version: For each set of duplicate files, prints the full path of each file
find . -type f | ruby -e 'h=Hash.new(){|ha,k|ha[k]=[]}; ARGF.readlines.map {|f| key=File::basename(f).gsub(/[ -]/,""); h[key] << f.chop; }; h.values.each { |arr| puts arr.join("\n"),"" if arr.size > 1}'


# A totally different approach: just list files by md5sum and filter out the non-dups
find . -type f -exec md5sum {} \; | sort | uniq -D -w 32


```

---

### Post by dylanologist on 2008-04-11
Thanks stylishpants,

Those first two entries look interesting (as in, I'm not really sure what's happening there).  Even the simpler one is a bit above my still pretty noobish head.  The third suggestion, using the md5sums, I tried to great success.  It found 30 or so duplicate files, some of which I do not believe would have been discovered by any of the other methods (filenames were identical, directories were different).

So thanks for that.  I believe my iTunes and Amarok have now been successfully combined without duplicates.  Thanks for the help from everyone.

---

