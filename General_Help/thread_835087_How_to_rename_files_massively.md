---
title: "How to rename files massively"
date: 2008-06-20
forum: General Help
---

### Post by Xi0N on 2008-06-20
I have different files with this structure:

_file1.rar.whatever
_file2.rar.whatever
_file3.rar.whatever
_file4.rar.whatever

and i want to rename them massively to 


file1.rar.what.ever
file2.rar.what.ever
file3.rar.what.ever
file4.rar.what.ever


But i must do it through console, and not one by one, because this example is with 4 files, but i need to do it with something like 200 :D

¿Is there any console pregram for massively renaming?

---

### Post by Zorael on 2008-06-20
I don't know if it has any CLI capabilities, but a GUI solution would be Métamorphose. debs available over at [http://www.getdeb.net/app/Metamorphose](http://www.getdeb.net/app/Metamorphose), and source at [http://sourceforge.net/project/showfiles.php?group_id=146403](http://sourceforge.net/project/showfiles.php?group_id=146403).

There are also some similar applications available in the official repostories which you could try out. See [http://packages.ubuntu.com/search?keywords=rename&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=rename&searchon=names&suite=hardy&section=all). Some ought to contain CLI apps; perhaps renameutils?

---

### Post by ad_267 on 2008-06-20
There's the command line application called "rename" that can do this. It uses perl regular expressions but I couldn't fully understand the man page for it. Someone else will probably know how to use this to do what you want.

---

### Post by ad_267 on 2008-06-20
This should explain how to do it if you know basics of bash: [http://www.debian-administration.org/articles/150](http://www.debian-administration.org/articles/150)

---

### Post by sisco311 on 2008-06-20
cd to the directory and execute this command:
```
rename -n 's/_()/$1/' *
```
replace the -n (no  action) option with -v(verbose) to rename the files.

---

### Post by Xi0N on 2008-06-20
And how can i do to rename a bunch of files that ends with .rar.html to .rar? (strip the .html)?

---

### Post by ad_267 on 2008-06-20
sisco311, do you mind explaining that a bit for me? The man page was pretty sparse and it seems different to regular expressions I've used before (mainly in php and regexxer). I would have thought you'd use something like:

```
rename -n 's/_(.*)/$1/' *
```

Also the if he wants the "whatever" split into "what.ever" could you use:

```
rename -n 's/()whatever/$1what.ever/' *
```?

Edit: Ok so would removing .html be "rename -n 's/()\.html/$1/' *"?

---

### Post by sisco311 on 2008-06-20
```
rename -n 's/.rar.html$/.rar/' *.html
```more examples:[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

EDIT: You can test your command with the -n option.
> -n, --no-act
               No Action: show what files would have been renamed.

---

### Post by ad_267 on 2008-06-20
So does () mean the same as (.*) in a perl regular expression?

---

### Post by sisco311 on 2008-06-20
> **ad_267 said:**
> So does () mean the same as (.*) in a perl regular expression?

man rename:
> 
SYNOPSIS
       rename [ -v ] [ -n ] [ -f ] **perlexpr** [ files ]

DESCRIPTION
       "rename" renames the filenames supplied according to the rule specified
       as the first argument.  **The perlexpr argument is a Perl expression**
       which is expected to modify the $_ string in Perl for at least some of
       the filenames specified.  If a given filename is not modified by the
       expression, it will not be renamed.  If no filenames are given on the
       command line, filenames will be read via standard input.


---

### Post by aquavitae on 2008-06-20
For something as simple as that you don't need the regexp:
```
rename whatever what.ever *
```

---

### Post by sisco311 on 2008-06-20
You can bulk rename files with thunar file manager(GUI) or krename(GUI).

---

### Post by ad_267 on 2008-06-20
> **sisco311 said:**
> man rename:

Yeah I read the man page, it's just I haven't seen () used without anything inside it before in a regular expression. That confused me a bit.

---

### Post by sisco311 on 2008-06-20
> **ad_267 said:**
> Yeah I read the man page, it's just I haven't seen () used without anything inside it before in a regular expression. That confused me a bit.
you're right you can't use ().
the correct command is:
```
rename -n 's/.rar.html$/.rar/' *.html
```or
```
rename -n 's/.html$//' *.html
```

---

### Post by ghostdog74 on 2008-06-20
learn how to do some simple shell scripting since you are on linux. no need too fancy GUIs or rename which may not be available in every distribution.
```

for files in *rar.html
do
 newfile=${files/.html/}
 mv "$files" $newfile
done

```

---

### Post by cyberkost on 2008-11-16
I have a related need ... I've ripped several CDs with track names originally in Cyrillic.  It took me a while, but I figured that
```
echo 'Ñíåæèíêà.flac'|iconv -t CP1252|iconv -f CP1251
```
gets me the desired
```
&#1057;&#1085;&#1077;&#1078;&#1080;&#1085;&#1082;&#1072;.flac
```
Now I need to automate this with using some scripting MAGIC, e.g.
```
#!/bin/bash
for files in *.flac
do
 newfile=${MAGIC}
# mv "$files" $newfile
 echo $newfile
done
```

What does MAGIC need to be?

---

### Post by ad_267 on 2008-11-16
```
newfile=`echo "$files" | iconv -t CP1252 | iconv -f CP1251`
```

Note that ` is a backtick, not a single quote.

---

### Post by cyberkost on 2008-11-16
> **ad_267 said:**
> ```
newfile=`echo "$files" | iconv -t CP1252 | iconv -f CP1251`
```

Note that ` is a backtick, not a single quote.

Worked like a charm ... and I do appreciate the expediency of the answer.  THANK YOU!

---

### Post by 73ckn797 on 2008-11-16
> **sisco311 said:**
> You can bulk rename files with thunar file manager(GUI) or krename(GUI).

+1 on Thunar.

Works fine for me daily with up to at least 200 photos each day. Have to rename the text part and leave extension unchanged.

---

### Post by cyberkost on 2008-11-16
begin-thread-hijack/

Now that
```
#!/bin/bash
for files in *.flac
do
 newfile=`echo "$files" | iconv -t CP1252 | iconv -f CP1251`
 mv "$files" "$newfile"
# echo "$newfile"
done
```
works in any one directory, how can I modify it so that it runs on all subdirectories (including level-2, level-3, etc.) in a given directory?  I have the whole Music/Artist/Album/Tracks hierarchy and everything except "Music" is in the screwed-up encoding that I need to fix.

/end-thread-hijack

---

### Post by ciscosurfer on 2008-11-16
I'm kinda partial to pyRenamer.  It's worth looking into if you like working in a GUI.

```
[COLOR=Navy]Package[/COLOR]: [COLOR=Red]pyrenamer[/COLOR]
[COLOR=black]State[/COLOR]: installed
[COLOR=black]Automatically[/COLOR] [COLOR=black]installed[/COLOR]: no
[COLOR=black]Version[/COLOR]: 0.6.0-1
[COLOR=black]Priority[/COLOR]: optional
[COLOR=black]Section[/COLOR]: universe/gnome
[COLOR=black]Maintainer[/COLOR]: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
[COLOR=Navy][COLOR=black]Uncompressed[/COLOR] [COLOR=black]Size[/COLOR][/COLOR]: 754k
[COLOR=Black]Depends[/COLOR]: gconf2 (>= 2.10.1-2), python (>= 2.4), python-support (>= 0.7.1), python-gtk2 (>= 2.4),
         python-glade2, python-hachoir-metadata | python-eyed3
[COLOR=Black]Recommends[/COLOR]: python-gnome2
[COLOR=Black]Description[/COLOR]: [COLOR=Black]mass file renamer written in PyGTK
 You can rename files using patterns, search and replace, substitutions, insert or delete text,
 or even rename files manually. You can also rename images using their EXIF tags and music using
 their internal tags.[/COLOR]
[COLOR=Navy]Homepage[/COLOR]: [COLOR=Red]http://www.infinicode.org/code/pyrenamer/[/COLOR]

``````
sudo apt-get update && sudo apt-get install pyrenamer
```

---

### Post by ad_267 on 2008-11-16
Edit. My previous method doesn't seem to work so try this instead:

You can use find to locate files and then pass them to another program.
```
find ~/Music/* -name *.flac -type f -exec ./rename_flac "{}" \;
```

And make a file called rename_flac that has:
```

#!/bin/bash

newfile=`echo $1 | iconv -t CP1252 | iconv -f CP1251`
mv "$1" "$newfile"

```

---

### Post by cyberkost on 2008-11-16
ad_267, the latest revision does not quite work b/c the in the Music/Artist/Album/Track path Artist, Album and Track are also part of the name that gets re-encoded, which causes an attempt to write to a non-existent directory:
```
mv: cannot move `/home/user/Music/RUSSIAN/TEST/Þðèé Àíòîíîâ - Çâåçäíàÿ ñåðèÿ/23 - Âñ¸ êàê ïðåæäå.flac' to `/home/user/Music/RUSSIAN/TEST/&#1070;&#1088;&#1080;&#1081; &#1040;&#1085;&#1090;&#1086;&#1085;&#1086;&#1074; - &#1047;&#1074;&#1077;&#1079;&#1076;&#1085;&#1072;&#1103; &#1089;&#1077;&#1088;&#1080;&#1103;/23 - &#1042;&#1089;&#1105; &#1082;&#1072;&#1082; &#1087;&#1088;&#1077;&#1078;&#1076;&#1077;.flac': No such file or directory
```
Looks like I need to go back to my PEARL library of scripts ... I recall I was doing a lot of parsing of full directory names -- it was just so many years ago that I don't remember anything

---

### Post by ad_267 on 2008-11-17
Oh ok I didn't realise the directories had the wrong encoding too. I guess you could try doing something similar but renaming the directories first. Eg:
find ~/Music/* -type d -exec ./rename_flac "{}" \;

Again that wouldn't work if you had two levels of directories.

---

