---
title: "[SOLVED] Removing Strings in Filenames"
date: 2007-08-27
forum: General Help
---

### Post by Bloaty on 2007-08-27
I have a folder full of files named like this.

Terminator 2 - Judgment Day (U) [!].smc
Terminator, The (U).smc
Test Drive II - The Duel (U) (20429).smc
Test Drive II - The Duel (U) (24291).smc
Tetris 2 (U) (V1.0).smc
Tetris 2 (U) (V1.1) [!].smc
Tetris Attack (U) [!].smc
Tetris & Dr. Mario (U) [!].smc

I need to remove all of these (Including the space between it and the last word).

Terminator 2 - Judgment Day[COLOR="Red"] (U) [!][/COLOR].smc
Terminator, The [COLOR="Red"](U)[/COLOR].smc
Test Drive II - The Duel [COLOR="Red"](U) (20429)[/COLOR].smc
Test Drive II - The Duel [COLOR="Red"](U) (24291)[/COLOR].smc
Tetris 2 [COLOR="Red"](U) (V1.0)[/COLOR].smc
Tetris 2 [COLOR="Red"](U) (V1.1) [!][/COLOR].smc
Tetris Attack [COLOR="Red"](U) [!][/COLOR].smc
Tetris & Dr. Mario [COLOR="Red"](U) [!][/COLOR].smc

After searching for hours and finding things almost perfect like this thread

[Removing # from filenames]("http://ubuntuforums.org/showthread.php?t=532386")
[sed or grep : delete lines containing matching text]("http://www.linuxquestions.org/questions/showthread.php?t=446640")
and reading all of this
[How to use "sed" to insert/replace strings]("http://www.shelldorado.com/newsletter/issues/2000-2-Feb.html")

I ended up writing and rewriting this bash script
```

#!/bin/bash

dir=./emulators/snes/roms/

for file `ls --quote-name $dir` ; do
    newname=`echo $file | grep -v "[!]"`
    mv $dir/$file $dir/$newname
done

```
and trying various commands like this
```
sed 's/[!]//g | ls ./emulators/snes/roms
```

Resulting in nothing. :confused:

I don't get what I'm doing wrong!](*,)

Any gurus care to help?:)

thx:)

---

### Post by bogolisk on 2007-08-27
But solving your problem would end up in some files having the same name. E.g.

Test Drive II - The Duel (U) (20429).smc

Test Drive II - The Duel (U) (24291).smc

Would have the same name:Test Drive II - The Duel.smc

---

### Post by bogolisk on 2007-08-27
Not exactly what you ask for (because it would result in name collision):
Before:
```

$ ls -w 1
Terminator 2 - Judgment Day (U) [!].smc
Terminator, The (U).smc
Test Drive II - The Duel (U) (20429).smc
Test Drive II - The Duel (U) (24291).smc
Tetris 2 (U) (V1.0).smc
Tetris 2 (U) (V1.1) [!].smc
Tetris Attack (U) [!].smc
Tetris & Dr. Mario (U) [!].smc

```
Changing name:
```

$  for i in *\(U\)*; do mv "$i" "$(echo "$i" | sed -re 's/ +\(U\)//g'  -e 's/ +\(([A-Z0-9.]+)\)/ \1/g' -e 's/ +\[!\]//g')"; done

```
After:
```

$ ls -w 1
Terminator 2 - Judgment Day.smc
Terminator, The.smc
Test Drive II - The Duel 20429.smc
Test Drive II - The Duel 24291.smc
Tetris 2 V1.0.smc
Tetris 2 V1.1.smc
Tetris Attack.smc
Tetris & Dr. Mario.smc

```

Hope that helps

---

### Post by Bloaty on 2007-08-27
Could i use wildcards to remove anything in between ()?
none of my files have (something important) so could I use wildcards or a pattern with sed or grep? :confused:

And if it simplifiys things i dont mind running seperate commands for the [] and the ().

---

### Post by yota on 2007-08-27
Have a look at the "rename" command too.
A quote from the manual:
> 
NAME
       rename - renames multiple files

SYNOPSIS
       rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]

DESCRIPTION
       "rename" renames the filenames supplied according to the rule specified
       as the first argument.  The perlexpr argument is a Perl expression
       which is expected to modify the $_ string in Perl for at least some of
       the filenames specified.  If a given filename is not modified by the
       expression, it will not be renamed.  If no filenames are given on the
       command line, filenames will be read via standard input.

       For example, to rename all files matching "*.bak" to strip the exten&#8208;
       sion, you might say

               rename &#8217;s/\.bak$//&#8217; *.bak


p.s. to remove anything inside () you can use
```

rename 's/(.*)//' *

```

where ".*" means any character (.), repeated in a sequence as long as possible (*); the last is "all files in current directory"

Hope this helps!

---

### Post by Bloaty on 2007-08-27
> **yota said:**
> Have a look at the "rename" command too.
A quote from the manual:

I tried this but i need some help with formatting and getting it to actually change the filenames. :???:

```

sed 's/[!]//g | ls ./emulators/snes/roms

```

i tried innumerable variations of this but cant seem to get the formatting right. :(

---

### Post by Bloaty on 2007-08-27
oh never mind. :)
sorry, i misread bogolisk's second post. ;)
That's exactly what I need!:):):)
Thanks for the help guys!
:guitar:

---

