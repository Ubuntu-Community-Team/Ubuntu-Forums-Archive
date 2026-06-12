---
title: "bash: convert &quot; /&quot; to &quot;; /&quot; in list of space delimited pathname/filenames"
date: 2013-03-12
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-03-12
I want to script a conversion of format of a space delimited list of filenames like this:
/path/to/some/file.ext /another/path/to/some other file that has spaces in the name /still/another path/bigfile 
to a semicolon-space delimited list like this:
/path/to/some/file.ext; /another/path/to/some other file that has spaces in the name; /still/another path/bigfile

The first format is the one that Caja (and I believe Nautilus also) returns for use in scripts via select and right click. The second format, after I wrap it in double parantheses, is the one I need to use with "for". I can't be the first or even the thousandth person to want to select some files graphically and put them through a "for ... do ... done" statement so some of you must have already invented this wheel.

I thought this would be trivial but despite trying a lot of things that seem like they SHOULD work I haven't been able to make either  sed or the ${string/replacethis/withthis} approachs work. I've tried  escaping the /s with \ and I've tried using alternative characters  instead of / in the sed expressions, with and without a "@" before the  first alternative seperator. I've tried putting the input string, the "  /" and "; /" in variables and using sed or the other approach with the  variables.  I've tried every half-way sane seeming combination of " and '  and different placements of the $.

For what it is worth I'm doing this under 64 bit Oneiric that started as Lubuntu to which I added the Mate DE. Is there some tool better for this than the 2 I've tried? Awk, maybe? Or am I just stupidly missing something in using sed?

---

### Post by Vaphell on 2013-03-12
space delimited list? o.O iirc nautilus stores the list in a newline delimited format.
Are you 100% sure it's spaces?
Can you redirect the input list to the file with double quotes and check? eg
```
echo "$list" > debug.txt
```
double quotes are important because all whitespace chars (tab, newline) degrade to spaces. Could you paste the code you got there?

either way forget *for* loop, *while read* is your friend
with assumption that space+/ = delimiter+first / of the next path
```
$ echo "/a/x x x/x /bc/d /f/g" | sed 's: /:\n/:g'
/a/x x x/x
/bc/d
/f/g
```

```
$ while read -r f; do echo "[$f]"; done < <( echo "/a/x x x/x /bc/d /f/g" | sed 's: /:\n/:g' )
[/a/x x x/x]
[/bc/d]
[/f/g]
```

---

### Post by Dreamer Fithp Apprentice on 2013-04-17
Thanks, Vaphell. I apologise for losing track of this thread. As for being a space delimited list, unless I'm misunderstanding something it sure looks like it to me. 

I wrote this script, naming it /home/user/.config/caja/scripts/test-variables.sh, to test the matter:
```
echo  "The variable  NAUTILUS_SCRIPT_SELECTED_FILE_PATHS is echoed:" > /home/f/.config/caja/scripts/variables-expanded.txt
echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS  >>  /home/user/.config/caja/scripts/variables-expanded.txt
echo  "The variable CAJA_SCRIPT_SELECTED_FILE_PATHS is echoed:" >> /home/user/.config/caja/scripts/variables-expanded.txt
echo $CAJA_SCRIPT_SELECTED_FILE_PATHS  > > /home/user/.config/caja/scripts/variables-expanded.txt

```

I selected some folders and right clicked and ran the script and got this in the resulting text file:
```
The variable  NAUTILUS_SCRIPT_SELECTED_FILE_PATHS is echoed:
/home/user/.config/autostart /home/user/.config/blueman /home/user/.config/caja
The variable CAJA_SCRIPT_SELECTED_FILE_PATHS is echoed:

```
The text file is attached also to reduce possibility of fomatting confusion (this forum has burned me on that before)
I included the spurious variable CAJA_SCRIPT_SELECTED_FILE_PATHS also just to demonstrate there is none such. Caja uses the nautilus-scripts variable names to maintain compatibility. Possibly despite the name Caja is using a different format (an older, pre-fork format maybe?) for the output.

I'll study this whlle read syntax.

---

### Post by Vaphell on 2013-04-17
you should always put $variable in "" to preserve its formatting, otherwise all whitespaces degrade to normal space and output doesn't represent the true value. My experience with nautilus-scripts says it stores a newline-delimited list of files/dirs but you have 3 paths in one line.

```
echo "[COLOR="#0000CD"]'[/COLOR]$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS[COLOR="#0000CD"]'[/COLOR]" >> ~/ns-test.txt
```
yields this:
```
[COLOR="#0000CD"]'[/COLOR]/home/me/.bash_logout
/home/me/.bashrc
[COLOR="#0000CD"]'[/COLOR]
```
as you can see the list is tidy, with one path per line when put inside ""



few nautilus-scripts i wrote long time ago generally go like this ( while-read loop)

```
#!/bin/bash

while read -r f
do
  do_something "$f"
done <<< "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```

or like this (array + for-loop)
```
#!/bin/bash

readarray -t files <<< "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
for f in "${files[@]}"
do
  do_something "$f"
done
```

---

### Post by Dreamer Fithp Apprentice on 2013-04-18
Duh . . . you TOLD me to put quotes around it. I must have got the wrong bottle when I took my smart pills. Can't believe I left out the quotes. /me looks under bed. But there ain't nobody else here I can blame it on. And yes, it works the same way in Caja. I'll study your suggested alternative to "for" before I push ahead with this. Can't say I'm enthusiastic about "for" anyway. I miss my goto. Thanks a heap.

---

### Post by Dreamer Fithp Apprentice on 2013-04-18
I haven't gotten your "read" syntax to work for me yet but I swiped your "for" version and it does the trick fine. Thanks again.

---

