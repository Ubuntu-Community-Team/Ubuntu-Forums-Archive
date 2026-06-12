---
title: "Finding Duplicates"
date: 2022-04-16
forum: General Help
---

### Post by wyattwhiteeagle on 2022-04-16
Can bash or perl search for words and phrases in multiple files, directories, and subdirectories?

I have this bad habit of creating multiple stuff to compare to each other in the future.

When I actually attempt to compare the 2 or more files, whether it be a text file or document, picture, photo, program, package, application, etc...
I get frustrated or something catches my attention and I go off on a goose-chase and so I completely forget all about cleaning out all the duplicated stuff.

I've tried rmlint-gui (it's a GTK*...I haven't found a qt5) but it was lacking in the area of finding matching (similar) words, phrases, etc.

I would rather use the terminal or a script in the terminal to perform in-depth searches, comparison's, and display's each item and filepath.

I can use fdupes, but I would like to use a script for something which is pre-installed by default such as bash, perl, etc.

---

### Post by ActionParsnip on 2022-04-16
You can use grep to search for words. Very powerful tool

---

### Post by wyattwhiteeagle on 2022-04-16
> **ActionParsnip said:**
> You can use grep to search for words. Very powerful tool

I apologize...I'm also wanting to search and compare md5 and hashes.

Can grep compare 2 of the exact same photo, song, etc even when the filename doesn't match?

---

### Post by The Cog on 2022-04-16
Try this:
```
find -type f -exec md5sum '{}' \; | awk 'a[$1]{print a[$1]" = "$2;next}{a[$1]=$2}'
```

---

### Post by wyattwhiteeagle on 2022-04-16
```
find -type f -exec md5sum '{}' \; | awk 'a[$1]{print a[$1]" = "$2;next}{a[$1]=$2}' > /home/wyatt/Desktop/Duplicates.txt
```

When I ran the above...
The following appeared in the results

> ./lib/__init__.py = ./Desktop/New_folder/InstalledPkg.txt

How would I limit it to only the Desktop folder and all of its contents?
The folder has subfolders.

---

### Post by The Cog on 2022-04-17
Cd to the Desktop and then run the above command. Or tell the find command where to search:
```
find Desktop -type f -exec md5sum '{}' \; | awk 'a[$1]{print a[$1]" = "$2;next}{a[$1]=$2}'
```
If you don't specify a folder to start the search, find searches from your current working directory.
I had imagined that you would cd into the directory of interest before running the command. If you run it from your home directory without specifying where to search, it could take a long time. I tried that and it got stuck in the Videos directory for ages. "man find" will show you all the options you can give to the find command - there are lots.

By the way, I would double-check any matches it finds by other means before deleting one of the two. I mean, I *think* it works OK but no guarantees.

---

### Post by wyattwhiteeagle on 2022-04-17
> **The Cog said:**
> Cd to the Desktop and then run the above command. Or tell the find command where to search:
```
find Desktop -type f -exec md5sum '{}' \; | awk 'a[$1]{print a[$1]" = "$2;next}{a[$1]=$2}'
```
If you don't specify a folder to start the search, find searches from your current working directory.
I had imagined that you would cd into the directory of interest before running the command. If you run it from your home directory without specifying where to search, it could take a long time. I tried that and it got stuck in the Videos directory for ages. "man find" will show you all the options you can give to the find command - there are lots.

By the way, I would double-check any matches it finds by other means before deleting one of the two. I mean, I *think* it works OK but no guarantees.

Thank you for that

Yeah...I noticed right at first that the output didn't reveal which of the 2 were the original...or most important,
especially when it came to the ones that I know for sure that I didn't do.

I lost count when I was counting all the web browser duplicates

---

### Post by wyattwhiteeagle on 2022-04-17
> **The Cog said:**
> ...By the way, I would double-check any matches it finds by other means before deleting one of the two. I mean, I *think* it works OK but no guarantees.

Just curious, what other means are available?

---

### Post by The Cog on 2022-04-17
If they're image files, look at them to see if they're the same picture for instance. As a sanity check. Use ls -l to see if they're the same size. 

The chances of two files having the same MD5 are very slim. I'd say the chances that I overlooked some logic error in my code that might occasionally flag two totally unrelated files are somewhat higher, although it worked OK in my test directory.

---

### Post by wyattwhiteeagle on 2022-08-21
If it finds 2 copies of the same image, one being in a desktop folder and the other being in a subdirectory of that same desktop folder...

How would I delete the one in the desktop folder using the terminal?

---

### Post by TheFu on 2022-08-21
> **wyattwhiteeagle said:**
>  How would I delete the one in the desktop folder using the terminal?

$ rm /path/to/the/file/to/be/deleted

Was this a trick question?

---

### Post by wyattwhiteeagle on 2022-08-22
> **TheFu said:**
> $ rm /path/to/the/file/to/be/deleted

Was this a trick question?
No it wasn't.

There are so many cli codes drifting around that I wasn't sure.

Those codes look much like the following...

```
rm -f -i -v /path -r
```
or
```
rm -r -V -P /path -F -i
```

The different switches and their placements in the line are two things that confuses me.

---

### Post by Holger_Gehrke on 2022-08-22
Never ever execute CLI commands you find somewhere on the web without first checking what the switches do. There's documentation for most everything on your system. You can access this documentation with the command 'man'. For example to read up on the switches for the 'rm' command you'd run 'man rm'. 'man' uses the text viewer 'less' for displaying the documentation, so all the usual 'less' commands work like for example '/' for searching.

Also for finding duplicate images the image viewer 'geeqie' has a duplicate finder which can search by similarity and will identify scaled images or images which have been rotated in 90° steps as duplicates

Holger.

---

### Post by TheFu on 2022-08-22
> **wyattwhiteeagle said:**
> No it wasn't.

There are so many cli codes drifting around that I wasn't sure.

Those codes look much like the following...

```
rm -f -i -v /path -r
```
or
```
rm -r -V -P /path -F -i
```

The different switches and their placements in the line are two things that confuses me.
[https://explainshell.com/](https://explainshell.com/) and the man pages help.  Also any beginning Unix book.  I asked if it was a trick question because there are 10 commands that are extremely common for beginners to use, so they aren't really asked very often.  
OTOH, there are some commands like 'find' or 'rsync' which can be confusing to everyone because order and options seem endless, but 'rm' isn't really one of those complex commands.  I don't think order matters with it, though I always do 
```
$ cmd  options  filespec
```
since options that can have multiple, mostly unlimited, inputs of the same type usually need to go last in the 'C' language or with the getopt/getopts C functions.  A filespec is one of those things, so it really should be last, almost always in commands.  Some commands require filespecs to be ordinal, like cp.  The last is the target and the 2nd, 3rd, 4th, 5th to last, if filespecs, have to be where they are in the order.  Perhaps my attempt to explain isn't good on this. If it isn't clear, just ignore it rather than being confused. Nearly all core CLI commands are written in C.

Any rm that used -f or -r options, should be carefully considered.  There is no -F or -V or -P options supported, so if you are seeing those, someone screwed up.  -r and -R and --recursive are all the same.  The manpage spells this out clearly.  We aren't against people asking for help here.  The longer they are here, the more self-help seems reasonable.

---

### Post by wyattwhiteeagle on 2022-08-29
> **TheFu said:**
> There is no -F or -V or -P options supported, so if you are seeing those, someone screwed up.
See, you have the knowledge and experience enough to be able to tell what is good and what isn't.

I'm not seeing those.
I put them there as an example to show how confusing it is to me.

In fact, not too long ago I tried the...
```
rm /path/to/file
```

It didn't work, which led me to ask here.

---

### Post by HermanAB on 2022-08-29
BTW, there are many edge cases and pitfalls when searching for duplicates.  It is really best to use an existing tool for that.  There are several: fdupes, fslint dupeguru, rdfind, etc.

---

### Post by Holger_Gehrke on 2022-08-29
If 'rm' didn't work you either didn't have write permission to the directory the file is in or you tried to erase a directory. Erasing a file means removing a name from a directory, so you need write permission on the directory.  For erasing directories you need to either use 'rmdir' (only works if the directory is empty) or if you want to remove a directory, its content and any sub-directories and their content you can use 'rm' with the options '-r' (recursive) and '-f' (force). Obviously you have to be very careful with the latter variant. I've trained myself to put a space in front of the command when using 'rm -rf' because then the command is not put into history (I had a mishap once which involved reverse search in the history (ctrl-r), an 'rm -rf' command and the enter key ...).

Holger

---

### Post by TheFu on 2022-08-29
> **Holger_Gehrke said:**
> If 'rm' didn't work you either didn't have write permission to the directory the file is in or you tried to erase a directory. Erasing a file means removing a name from a directory, so you need write permission on the directory.  For erasing directories you need to either use 'rmdir' (only works if the directory is empty) or if you want to remove a directory, its content and any sub-directories and their content you can use 'rm' with the options '-r' (recursive) and '-f' (force). Obviously you have to be very careful with the latter variant. I've trained myself to put a space in front of the command when using 'rm -rf' because then the command is not put into history (I had a mishap once which involved reverse search in the history (ctrl-r), an 'rm -rf' command and the enter key ...).

Holger

Almost everyone has horror stories around 'rm -rf'. Some people have multiple horror stories, like me.  Grouped with find, rm can do some real damage.

If 
```
rm /path/to/file
```
doesn't work my first guess is that the person didn't use tab-completion to ensure  /path/to/file was correct.  My 2nd guess would be permissions as Holger says.  My 3rd guess would be that they didn't understand to change /path/to/file to actually point at the absolute or relative path to the actual file to be removed.  It happens. People take things literal sometimes.  Capitalization is a common issue for Unix noobs.  They don't realize that "filename" and "fileName" are completely different files.   Most of those little issues are avoided by using tab-completion.

---

### Post by HermanAB on 2022-08-29
Hmm, in my yoof, I once erased a running web server - that was not much fun.  I have also caused a minor buggerup with deduplication.  There are so many weird edge cases with files, directories and permissions that a single person just won’t think of all of them. 

Therefore I repeat: It is best to use an existing dupe tool - since many people around the world already tried it.

---

### Post by nickycruze2 on 2022-08-30
[COLOR=#000000][INDENT]Can grep compare 2 of the exact same photo, song, etc even when the filename doesn't match?
[SIZE=1][19216811.bid](https://19216811.bid/)[/SIZE]
[SIZE=1][panoramacharter.ltd](https://panoramacharter.ltd/)[/SIZE]


[/INDENT]
[/COLOR]

---

### Post by Holger_Gehrke on 2022-08-30
[LIST=1]
[*]Don't highjack threads.
[*]grep is for searching text for regular expression not for comparing files. For a quick comparison of two binary files try 'cmp', for a comparison of text which can tell you how to turn file1 into file2 use 'diff'. For the details please read the respective manual pages: 'man cmp' and 'man diff'.
[/LIST]

Holger

---

### Post by wyattwhiteeagle on 2023-06-05
```
find /home/wyatt/Desktop/Wyatts-Stuff/Compressed/1-New-folder -type d -exec md5sum '{}' \; | awk 'a[$1]{print a[$1]" = "$2;next}{a[$1]=$2}'
```
Output is...
```
md5sum: /home/wyatt/Desktop/Wyatts-Stuff/Compressed/1-New-folder: Is a directory
```
I'm needing to find duplicates of archive folders.
Changing the "-type f" to "-type d" doesn't seem to find duplicates of archive types, etc.

What do I need to change in the above command to find these duplicates?

---

### Post by TheFu on 2023-06-05
> **wyattwhiteeagle said:**
> See, you have the knowledge and experience enough to be able to tell what is good and what isn't.

I'm not seeing those.
I put them there as an example to show how confusing it is to me.

In fact, not too long ago I tried the...
```
rm /path/to/file
```

It didn't work, which led me to ask here.

Actually, I don't have any knowledge or experience.  I simply read the man page for rm and it told me.  You could have done the same.
A directory and a file are different, in the world of many CLI commands, including **rm**.  To remove a directory, use **rmdir**.  That directory must be empty.

You wrote **rm /path/to/file** .... that's different than **rm /path/to/directory**

---

### Post by TheFu on 2023-06-05
> **wyattwhiteeagle said:**
> ```
find /home/wyatt/Desktop/Wyatts-Stuff/Compressed/1-New-folder -type d -exec md5sum '{}' \; | awk 'a[$1]{print a[$1]" = "$2;next}{a[$1]=$2}'
```
Output is...
```
md5sum: /home/wyatt/Desktop/Wyatts-Stuff/Compressed/1-New-folder: Is a directory
```
I'm needing to find duplicates of archive folders.
Changing the "-type f" to "-type d" doesn't seem to find duplicates of archive types, etc.

What do I need to change in the above command to find these duplicates?

f is a file.
d is a directory.  The find manpage explains this.
You could use explainshell.com to learn it too.

I don't know awk, sorry.  Not my skillset.

Whenever someone is struggling with a command and I think I understand what their final goal is, and I know there are existing, well-tested, tools that do this, I always wonder why they don't just use those tools?

Is there a reason you aren't using an existing tool?  fdupes is one. There are others.
For fun, I wrote my own in perl.  It is longer than your 1 liner to be more efficient for huge numbers of files.

First, if the file size isn't the same, then it isn't an identical file. Getting the size is a low-cost effort.
For all files that have the same size, create a checksum. If that matches, I look at the total length of the directory and filename, then create an rm command for the shorter filename.  Guess my idea was that longer names were more descriptive, so that would be preferred.  After using this script for over 10 yrs, I'd forgotten that choice and noticed that the file getting the 'rm' didn't seem clear.

I use **find** and **stat** for most of the work.  MD5 is known to have collisions at a much higher rate than some other checksum tools.  For very large file sets, using something else would make sense.  BTW, it might be more efficient to perform an initial checksum on only the first 4KB of a file.  If it matches on that, then do the full sha256 checksum to be 99.99999% certain. Seeing that files are not identical ASAP is a good thing to remove them from consideration.

I also have command line switches to limit the types of files searched - say only look for images or only look for videos.  Usually when I'm trying to capture free storage, it is media files that are the big problem.

My script uses 4 temporary files.  I didn't want to maintain millions of records in RAM.  This way, the tool can run on a low-end ARM computer. At the end of the script, those files are cleaned up.  The total script is 243 lines long. It isn't perfect.  In fact, I should probably use **fdupes** myself.
[https://www.tecmint.com/fdupes-find-and-delete-duplicate-files-in-linux/](https://www.tecmint.com/fdupes-find-and-delete-duplicate-files-in-linux/)

If I wanted to find other, similar, tools, I'd use a web search "fdups vs"

Seems lots of smart people have attacked this same issue: [https://unix.stackexchange.com/questions/34366/is-there-a-way-of-deleting-duplicates-more-refined-than-fdupes-rdn](https://unix.stackexchange.com/questions/34366/is-there-a-way-of-deleting-duplicates-more-refined-than-fdupes-rdn)  It is unlikely that re-inventing this wheel is necessary, unless you just want to learn.  Nothing wrong with that, assuming reading the manpages is part of the method.

---

### Post by wyattwhiteeagle on 2023-06-05
I understand "-type f" means file and "-type d" means directory.
Both f and d return no results when used on archived items.
That seems to suggest that archived items are neither file's or directories.


Existing tools have their advantages and disadvantage's.
Most times, existing tools are GUI.
But for archive items, something like Fdupes may be the easier and quicker way.


GUI's have a tendency to use up more RAM than needed just to have it open.
Close the GUI and you get asked if you want to cancel the operation.
It means that if you don't cancel the operation, you agree to keep the resource hog open or running in the background.


Just think, a resource hog running in the background bogging down your computer.
Who wants that?

My resource limited machine or I don't want that.
I wouldn't be able to get anything done.

---

### Post by TheFu on 2023-06-05
> **wyattwhiteeagle said:**
> I understand "-type f" means file and "-type d" means directory.
Both f and d return no results when used on archived items.
That seems to suggest that archived items are neither file's or directories.


I don't know what you mean by "archived items" - if they are in the directory or subdirectories specified at the start of the 'find' AND the current userid has permissions to read those objects, then they will be found.  The manpage for find spells out some special processing for symlinks and hardlinks and named-pipes, but it is unlikely any "archive files" are of those types.  However, I didn't test it.

When I think of archived stuff, I think it has been removed and placed onto off-line storage.  There's no way that **find** will see that storage, when it is off-line.  What some people do, including me, is to make an **ls -lR** listing for my offline storage and retain that listing online so old files can still be found, but only use 1 line in a text file somewhere.  There are lots of ways to do this.  I actually number my offline storage and have numbered filenames for the **ls -Rl** text files.  A quick **grep** can search all of them --- and there are hundreds --- to find results and point me at the specific offline storage holding the file(s) of interest.

> **wyattwhiteeagle said:**
> 
Existing tools have their advantages and disadvantage's.
Most times, existing tools are GUI.
But for archive items, something like Fdupes may be the easier and quicker way.

Most existing tools ARE NOT GUIs.  Most are CLI.  I suspect in searching for tools, some tool that favors GUI results is being used - like _Software Center_.  Or perhaps the search engine you use has figured out that you click on GUI tools more than non-GUI tools and the search results provided have those answers first?  IDK.  I seldom see GUI tools in my search results.

> **wyattwhiteeagle said:**
> 
GUI's have a tendency to use up more RAM than needed just to have it open.
Close the GUI and you get asked if you want to cancel the operation.
It means that if you don't cancel the operation, you agree to keep the resource hog open or running in the background.

What?  Is this a Mac thing? Most Unix tools don't do this.  Perhaps, again, we are using different programs and the ones you use behave like that.  I can't think of any I use that do.  
I wouldn't put up with a program that doesn't close when I tell it to close.  It would be uninstalled immediately.  I've heard that Skype and some other conferencing tools try to do this.  I don't use those. There are plenty of alternatives, like meet.jit.si. If I saw they did keep running after I told them to close, I'd either purge/remove the package or create a wrapper around them to ensure they are killed/closed when I say.  It is my computer, not theirs.  I'm the master, not them.  I'm fairly brutal about which programs I'm willing to install and leave on my systems.

Of course, my experiences from my system(s) may be completely different from what you've experienced. We probably use our computers in completely different ways.

If there is sufficient interest, I can post my crap perl code. It isn't too clean nor is it native 100% - I should use File::Find instead of doing a system call to the 'find' program, for example.  It would be faster in perl, but it is already fast for what it does.  Screw that.  Here's a link for it:  [https://lpi.jdpfu.com/DupFinder/dupfinder](https://lpi.jdpfu.com/DupFinder/dupfinder)

It works how it works. Use or don't as you like.  Don't believe the comments. There could be lots of dead code inside it.  If anyone decides to fork it, please add my handle and the date, but there are better tools. I use it only because it fits almost exactly my needs.

---

### Post by wyattwhiteeagle on 2023-06-05
Archived Items...you know..."*.zip" "*.7z" "*bz".
Compressed folders

Um...these days...I must be incorrect in my last post about fdupes and GUI.

Last time I used fdupes in Ubuntu 14.04 LTS, it had a GUI.
I just installed fdupes and it doesn't have a GUI.

Apparently, the fdupes then and the fdupes now seem to be quite different.

---

### Post by Holger_Gehrke on 2023-06-06
Compressed archive files are just that - files. There's no support in find - or most other tools - for reading inside these per se. There are - of course - many ways to get around this. There are at least two FUSE filesystems for mounting archives as if they were filesystems (archivemount, avfs) and there are several command line front-ends for archiver programs (for example patool). So you can either find all archives in a first step and then mount them all into various places and then search inside those or you can do a 'find ... -exec' combo with one of the frontends to get listings of the contents of all archives and grep through the results. The frontends are useful for this because they have the same syntax for all types of archives. Otherwise  you'd need to do it separately for each type of archive; example: to  get a detailed listing of the files in a zip you do 'unzip -v archive.zip', for rar it's 'unrar lt archive.rar' (and the format is completely different) and for 7z '7z l -slt archive.7z' (with yet another format).

And fdupes has AFAIK always been a CLI tool. There used to be a GUI tool named fslint, but that still uses Python 2.x and has therefore vanished from the repositories. There is a GUI tool that is supposedly a more advanced version of fslint named 'czkawka' (the author is Polish and a bit of a troll: he gave it that name - meaning 'hiccup' - because he wanted to find out how non-polish speakers would pronounce it ;) ). It's not in the repositories, but there is both a snap and a PPA.

Holger

---

