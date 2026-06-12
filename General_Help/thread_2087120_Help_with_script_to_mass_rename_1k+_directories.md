---
title: "Help with script to mass rename 1k+ directories"
date: 2012-11-22
forum: General Help
---

### Post by TheForumTroll on 2012-11-22
I just noticed that all my old photos on my backup are stored in some different directory naming conventions than my newer ones and renaming everything by hand... well lets just say that there is 1000 plus directories that needs fixing and I've let myself become extremely rusty in scripting :roll:

Does anyone have time on their hands to write a small script that mass renames them for me? [-o< 

What I got: 
[INDENT](YEAR) XXX YYY
XXX YYY (YEAR)[/INDENT]

How they should be named:
[INDENT]YEAR - XXX YYY[/INDENT]


**Examples:**

From this:
[INDENT](2001) International Space Station (ISS)
My Dark Basement (1984)[/INDENT]

To this:
[INDENT]2001 - International Space Station (ISS)
1984 - My Dark Basement[/INDENT]

There's a few [ ] and dashes in the directory names too I think (they don't need changing - just a warning if it messes with the script). The files are fine too (DDMMYYYY.xxx) so it's just the directories that need fixing. I tried googling but only found file mass renaming.

It's on a headless server, so no GUI tools :KS

---

### Post by Vaphell on 2012-11-22
always 4digits in ()?

---

### Post by TheForumTroll on 2012-11-22
Yes the year is always in four digits :)

EDIT: Uh, forgot to say that some directories have no year at all (and hence need no fixing).

---

### Post by steeldriver on 2012-11-22
The rename command works pretty well for stuff like this - like Vaphell implies, you can refine the expression if you need to be more (or less) specific about the match condition e.g.'[0-9]{4}' (exactly 4 digits) instead of '[0-9]+' (1 or more digits)

```

$ mkdir "(2001) International Space Station (ISS)"
$ mkdir "My Dark Basement (1984)"
$
$ rename -nv 's/\(([0-9]+)\) (.*)/$1 - $2/' */
(2001) International Space Station (ISS)/ renamed as 2001 - International Space Station (ISS)/
$
$ rename -nv 's/(.*) \(([0-9]+)\)/$2 - $1/' */
My Dark Basement (1984)/ renamed as 1984 - My Dark Basement/

```You can use globstar if you need to do it recursively on subdirectories

---

### Post by TheForumTroll on 2012-11-22
Hmm, I don't know why but I get no output out of the script at all and nothing changes :confused: 


**EDIT**: Oh, there's two different lines. Doh. Let me try again
**EDIT 2**: Nope, no luck. One line does nothing, the other says it changes it but doesn't.

---

### Post by cjhabs on 2012-11-22
The -n option to rename shows what the command would do but doesn't actually do it. Once you are happy with the command, remove the -n option.

---

### Post by TheForumTroll on 2012-11-22
Oh, that will teach me to look more closely at a script before running it :oops:

It doesn't go into subdirs and change it, even with globstar on though.

---

### Post by Vaphell on 2012-11-22
```
rename -nv 's/(.*) \(([0-9]+)\)/$2 - $1/'
```
this will probaly fail with paths

```
$ rename -nv 's/(.*) \(([0-9]+)\)/$2 - $1/' ../mass_rename/*(*)*
../mass_rename/abcdef ghi XoXoXo (2063) renamed as [COLOR="Red"]2063 - ../mass_rename/[/COLOR]abcdef ghi XoXoXo
```

standard *while read*
```
#!/bin/bash

while IFS= read -rd $'\0' d
do
  p=${d%/*}; nd=${d##*/}
  if [[ $nd =~ [(][0-9]{4}[)]$ ]]
  then
#    yr=${nd##*(}; yr=${yr%?}
#    nd="$yr - ${nd% *}"
#    echo mv -v "$d" "$p/$nd"
    rename -nv 's|(.*)/(.*) \(([0-9]+)\)|$1/$3 - $2|' "$d"
  elif [[ $nd =~ ^[(][0-9]{4}[)] ]]
  then
#    yr=${nd%%)*}; yr=${yr#?}
#    nd="$yr - ${nd#* }"
#    echo mv -v "$d" "$p/$nd"
    rename -nv 's/\(([0-9]+)\) (.*)/$1 - $2/' "$d"
  fi
done < <( find . -iname '*([0-9][0-9][0-9][0-9])*' -type d -print0 )
```

as a bonus pure bash manipulation in comments.

---

### Post by TheForumTroll on 2012-11-22
That's....beautiful :)

Thank you. I had to run it more than once (it doesn't enter a directory after it has been renamed and rename directories in it) but it works. So much time saved. I owe you a beer :P

---

