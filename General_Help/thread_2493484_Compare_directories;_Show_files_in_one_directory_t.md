---
title: "Compare directories; Show files in one directory that aren't in the other?"
date: 2023-12-16
forum: General Help
---

### Post by david503 on 2023-12-16
I have two directories, I want to know which files are in either directory that aren't in the other, including subdirs. 

So basically a diff, but with directories.  Actually I thought of just running find ./ -name "." > dir1.txt and just running a diff but- diff will "complain" (wrong word) about two lines being different, which isn't what I want, you see- it would have so many false positives. 

I figure it's a common need, so maybe there's a way in the terminal or some application? (I'm in Ubuntu 18.04 - in fact the reason I'm doing this as part of backing up to get out of the stone age)  

Or do I have to just write a PERL (or whatever- PHP) script to recursively travers the dirs and etc etc etc.

Thanks.

---

### Post by Dennis N on 2023-12-16
Perhaps **meld** can help.

---

### Post by MAFoElffen on 2023-12-16
This is something that Midnight Commander excels at: <Cntrl><X>,<D>...

Or via CLI using diff
```

diff --brief --recursive <Dir1> <Dir2>
# Or more granularity by adding options or filters
diff --brief --recursive <Dir1> <Dir2> --exclude '*.log'

```

---

### Post by ajgreeny on 2023-12-17
Thunar, the file manager from Xfce can now also show directories side by side in two pane mode (F3) which i use quite a lot.
It is available in xfce-4.18, so needs a newer system than your 18.04 but could be useful in future.

---

### Post by david503 on 2023-12-17
> **MAFoElffen said:**
> This is something that Midnight Commander excels at: <Cntrl><X>,<D>...

Or via CLI using diff
```

diff --brief --recursive <Dir1> <Dir2>
# Or more granularity by adding options or filters
diff --brief --recursive <Dir1> <Dir2> --exclude '*.log'

```

As I said in the op post, diff doesn't work because it returns too many false positives.

If the one directory is

filea
fileb
filec
filed
filee
filef
fileg
fileh
filei

And the other is: 

filea
filec
filed
filee
filef
fileg
fileh
filei

(meaning without the "fileb"),

Then diff will give notifications about every line after filea. 

When really what I want to know is that one directory has fileb and the other doesn't, you see?

---

### Post by dragonfly41 on 2023-12-17
I use dual pane Krusader which I think can be configured to achieve that.

There are useractions and I have previously written two useractions which can

MeldFiles
MeldDirectories

or you can write your own custom scripts (useractions).

Here is a typical MeldFiles command: 

meld %lCurrent% %rCurrent%

and MeldDirs

meld %lPath% %rPath%

See UserActions here...

[https://docs.kde.org/stable5/en/krusader/krusader//](https://docs.kde.org/stable5/en/krusader/krusader//)

[https://docs.kde.org/stable5/en/krusader/krusader//useractions.html](https://docs.kde.org/stable5/en/krusader/krusader//useractions.html)

Instead of Meld (CLI) you might run Python scripts.
I understand that you are looking for files which are **not** common. 
Another idea is to use Albert. But Krusader allows two directories to be easily selected. 
Krusader is similar to Midnight Commander as suggested earlier.

---

### Post by david503 on 2023-12-17
Woa, ActionScript?! That's still alive?  I used to write a whole lot of it before Flash and Flex died.

Yea I'm looking at some of these and it looks like it can only do one directory at a time.  But yea, I'll take a look at those, thanks.

Oh and like I said- rolling my own code (in my case not python- PERL or PHP) is my last resort but I figured the task is commen enough that there might be something.

Thanks

(wow, Actionscript!)

---

### Post by Holger_Gehrke on 2023-12-17
Normally I'd do something like
```

(ls -1 firstdir;ls -1 seconddir)|sort|uniq -u

```
but this has the disadvantage that you can't tell in which directory the unique file(s) is(/are).
A bit of interactive python doesn't have this problem:
```

import os
# replace firstdir and seconddir with the paths to the directories in question
a=os.listdir('firstdir')
b=os.listdir('seconddir')
# this prints the files in firstdir that are not in seconddir
print([x for x in a if x not in b])
# the ones in seconddir but not in firstdir
print([x for x in b if x not in a])

```
Turning this into a script that gets arguments from sys.argv[] to use as firstdir and seconddir is left as an exercise to the reader.

Holger

---

### Post by oygle on 2023-12-17
> **david503 said:**
> I have two directories, I want to know which files are in either directory that aren't in the other, including subdirs. 

Beyond Compare can do this, I've used it for years. The download is at [https://www.scootersoftware.com/download/](https://www.scootersoftware.com/download/)  , from memory it's a 30 day usage for the trial/free.

---

### Post by TheFu on 2023-12-17
My first thought was to use **meld**.  I know that works.

Then I had an idea to use **rsync** in "dry-run" mode (think it is the -n option) which doesn't do anything.  With the verbosity set correctly, the list of files to be transferred will be output.  Then swap the source/target around and get the opposite list. Simple. Elegant. Effective.

```
        -n, --dry-run               perform a trial run with no changes made
```

OT: I love me some BASS!

---

### Post by dragonfly41 on 2023-12-18
> Woa, ActionScript?! That's still alive? I used to write a whole lot of it before Flash and Flex died.


It sure is alive (shades of ActionScript O'Reilly) and I use Actiona with simple Qt5 widgets found here. Sans Flash.


[https://github.com/Jmgr/actiona/issues](https://github.com/Jmgr/actiona/issues)


Actiona (create 16 years ago) is making a revival although there are many other younger kids on the block.


Optionally you can use Actiona in concert with Sublime Text has an ActionScript package as does VSCode.


In fact I use Actiona in concert with Sublime Text (easier on the eyes when writing ActionScript since the Actiona code is tiny) and in an Actiona codebox write Include("myactionscript.as") where myactionscript.as is in same directory as actiona script *.ascr (ext *ascr is in fact XML format). And include any other language such as Python and run in command widget


Here is one example seen today in French forum.You will need to right click on French text and "Translate to English" in browser. 


[https://forum.jmgr.net/viewtopic.php?t=19394](https://forum.jmgr.net/viewtopic.php?t=19394)


Many of early posts were in French since founder Jmgr is French national. But there is an English forum, but none too active. Use the newer Github site given earlier. 


You might also remember openlaszlo for Flash. Deceased. But ... archived ...
[https://www.openlaszlo.org/](https://www.openlaszlo.org/)


You can include any of the above ideas inside an Actiona wrapper.


It allows a basic way of automating many tasks and microservices.

---

### Post by david503 on 2024-01-04
> **TheFu said:**
> My first thought was to use **meld**.  I know that works.

Then I had an idea to use **rsync** in "dry-run" mode (think it is the -n option) which doesn't do anything.  With the verbosity set correctly, the list of files to be transferred will be output.  Then swap the source/target around and get the opposite list. Simple. Elegant. Effective.

```
        -n, --dry-run               perform a trial run with no changes made
```

OT: I love me some BASS!


Ohhhh I should've thought of that.  rsync was my first instinct- I didn't even know it has a dry mode.   Thanks!

---

### Post by The Cog on 2024-01-04
Or how about:
```
# Files unique to dir1:
comm -23 <(cd dir1 ; find | sort) <(cd dir2 ; find | sort)
# Files unique to dir2:
comm -13 <(cd dir1 ; find | sort) <(cd dir2 ; find | sort)
```

---

