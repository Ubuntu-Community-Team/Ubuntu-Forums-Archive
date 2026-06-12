---
title: "Enter word from File name into File"
date: 2013-07-02
forum: General Help
---

### Post by MickoD on 2013-07-02
[COLOR=#444444][FONT=verdana]Hi folks,[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]First post - hope I'm in the correct forum.[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]Need to run a script on a folder file of files. The script needs to replace a variable (same variable in each file) with a word taken from the file name of the file.[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]For example 3 files;[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]file-one-name.txt[/FONT][/COLOR]
[COLOR=#444444][FONT=verdana]file-tom-name.txt[/FONT][/COLOR]
[COLOR=#444444][FONT=verdana]file-mpo-name.txt[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]Inside each file is the word/variable $pop and this word needs to be replaced each time it appears in all the files by the the 3 letter word that appears in the filename. e.g. in file 1 above $pop should be substituted with one and in file 2 above $pop should be substituted with tom, etc.[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]I don't even know where to start with this but I suspect it's something that could be achieved with sed in a for in loop or some such?[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]Thanks in advance,[/FONT][/COLOR]

[COLOR=#444444][FONT=verdana]Mick[/FONT][/COLOR]

---

### Post by steeldriver on 2013-07-02
Hello and welcome to the forum

You could use bash's own substitution capabilities to strip the filename down to get the replacement string, e.g. if variable 'f' contains the filename then

```
${f#file-}
```

is the filename with 'file-' removed from the front, and

```
${f%-name.txt}
```

is the filename with '-name.txt' removed from the back - I don't know a way to remove both in one shot but you can chain them e.g.

```
r="${f#file-}"; r="${r%-name.txt}"
```

Then you should be able to use a loop with sed like you suggested - since the thing you are trying to replace ($pop) has a 'special' character in it ($) you will need to backslash escape that I think e.g.

```
$ for f in *.txt; do r="${f#file-}"; r="${r%-name.txt}"; sed "s/\$pop/$r/g" "$f"; done
```

[NB you do need to use caution with shell expansions inside of 'sed' - it will all go horribly wrong if $r expands to something with characters that are special in sed (like /;&\ etc), especially in the pattern portion - in this case it's OK I think provided your filenames are basically alphanumeric]

---

### Post by coffeecat on 2013-07-02
> **MickoD said:**
> hope I'm in the correct forum.

Not quite. :wink: The Ubuntu, Linux & OS chat section is for:

> This is the place for chat and discussion about any aspect of Ubuntu, Linux or any operating system and its software. Technical support requests should be posted in an appropriate support sub-forum.

I've moved this to General Help. Good luck.

---

