---
title: "recursive hard link video files, renamed to another directory"
date: 2014-09-18
forum: General Help
---

### Post by c@ssie on 2014-09-18
Hi I have shows in my itunes directory eg:

```
./iTunes/iTunes Media/TV Shows/Rookie Blue/Season 5/01 Blink.m4v
./iTunes/iTunes Media/TV Shows/Haven/Season 3/11 Last Goodbyes.m4v
./iTunes/iTunes Media/TV Shows/Doctor Who (2005)/Season 5/10 Vincent and the Doctor.m4v

```
I want to hard link them to another directory with different names e.g:

```
./TV/Rookie.Blue/Season.05/Rookie.Blue.S05E01.Blink.mp4
./TV/Haven/Season.03/Haven.S03E11.Last.Goodbyes.mp4
./TV/TV Shows/Doctor.Who.2005/Season.05/Doctor.Who.2005.S05E10.Vincent.and.the.Doctor.mp4
```

So it in general, would be ```
/TV/[COLOR=#ff0000]Show.Name[/COLOR]/Season.[COLOR=#ff0000]nn[/COLOR]/[COLOR=#ff0000]Show[/COLOR].[COLOR=#ff0000]Name[/COLOR].S[COLOR=#ff0000]nn[/COLOR]E[COLOR=#ff0000]nn[/COLOR].[COLOR=#ff0000]Episode[/COLOR].[COLOR=#ff0000]Name[/COLOR].mp4
``` ([COLOR=#ff0000]red[/COLOR] is [COLOR=#ff0000]variable[/COLOR], black is literal)

Is there a command or script that would do this for all my TV shows?

---

### Post by TheFu on 2014-09-18
**cp -l**

You'd have to write the script.  Also - hardlinks only work on the same file system i.e. same partition.

I would strongly suggest avoiding the use of '.' characters since those make regex matching a little harder. Use _ instead or spaces. For scripting, spaces are a hassle.  Doesn't m4v have DRM?  Renaming them to a different extension without actually converting the file container might be bad.

---

### Post by Vaphell on 2014-09-18
```
#!/bin/bash

srcroot="./iTunes/iTunes Media/TV Shows"
destroot="./TV"

for f in "$srcroot"/*/*/*.{m4v,mp4,avi}
do
    [[ -f $f ]] || continue
    IFS=/ read -a vid <<< "${f// /.}"
    vid=( "${vid[@]: -3}" )
    show=${vid[0]}
    season=${vid[1]}
    episode=${vid[2]}
    [[ $show =~ \([0-9]{4}\)$ ]] && show=${show:0:-6}${show: -5:4}
    sn=${season#*.}
    IFS=. read ep eptitle <<< "${episode%.*}"
    ext=${episode##*.}
    
    printf -v hldir -- '%s/%s/%s' "$destroot" "$show" "$season"
    printf -v hlname -- '%s.s%02de%02d.%s.%s' "$show" "$sn" "$ep" "$eptitle" "$ext"
    echo "from: '$f'"
    echo "to: '$hldir/$hlname'"
    mkdir -p "$hldir"
    ln "$f" "$hldir/$hlname"
    echo
done
```

```
$ ./hl.bash
from: './iTunes/iTunes Media/TV Shows/Doctor Who (2005)/Season 5/10 Vincent and the Doctor.m4v'
to: './TV/Doctor.Who.2005/Season.5/Doctor.Who.2005.s05e10.Vincent.and.the.Doctor.m4v'

from: './iTunes/iTunes Media/TV Shows/Haven/Season 3/11 Last Goodbyes.m4v'
to: './TV/Haven/Season.3/Haven.s03e11.Last.Goodbyes.m4v'

from: './iTunes/iTunes Media/TV Shows/Rookie Blue/Season 5/01 Blink.m4v'
to: './TV/Rookie.Blue/Season.5/Rookie.Blue.s05e01.Blink.m4v'
```

---

### Post by c@ssie on 2014-09-19
> **Vaphell said:**
> ```
#!/bin/bash

srcroot="./iTunes/iTunes Media/TV Shows"
destroot="./TV"

for f in "$srcroot"/*/*/*.{m4v,mp4,avi}
do
    [[ -f $f ]] || continue
    IFS=/ read -a vid <<< "${f// /.}"
    vid=( "${vid[@]: -3}" )
    show=${vid[0]}
    season=${vid[1]}
    episode=${vid[2]}
    [[ $show =~ \([0-9]{4}\)$ ]] && show=${show:0:-6}${show: -5:4}
    sn=${season#*.}
    IFS=. read ep eptitle <<< "${episode%.*}"
    ext=${episode##*.}
    
    printf -v hldir -- '%s/%s/%s' "$destroot" "$show" "$season"
    printf -v hlname -- '%s.s%02de%02d.%s.%s' "$show" "$sn" "$ep" "$eptitle" "$ext"
    echo "from: '$f'"
    echo "to: '$hldir/$hlname'"
    mkdir -p "$hldir"
    ln "$f" "$hldir/$hlname"
    echo
done
```

```
$ ./hl.bash
from: './iTunes/iTunes Media/TV Shows/Doctor Who (2005)/Season 5/10 Vincent and the Doctor.m4v'
to: './TV/Doctor.Who.2005/Season.5/Doctor.Who.2005.s05e10.Vincent.and.the.Doctor.m4v'

from: './iTunes/iTunes Media/TV Shows/Haven/Season 3/11 Last Goodbyes.m4v'
to: './TV/Haven/Season.3/Haven.s03e11.Last.Goodbyes.m4v'

from: './iTunes/iTunes Media/TV Shows/Rookie Blue/Season 5/01 Blink.m4v'
to: './TV/Rookie.Blue/Season.5/Rookie.Blue.s05e01.Blink.m4v'
```

Thank you so much, this Is very helpful,  but there is one little problem when it got to "/iTunes/iTunes Media/TV Shows/Doctor Who (2005)", it gave the error:

```
/home/cassie/hl.bash: line 12: -6: substring expression < 0
```

it appears that the parenthesis crashed it

---

### Post by TheFu on 2014-09-19
Remember when I said above that '.' characters screw with scripts and to avoid spaces in names?  Many special characters do that and need to be avoided *at all costs* in file/directory names.  Parenthesis, square/curly brackets, ', ", need to be included in those characters to avoid.

Not exactly relevant to the issue here, but part of the solution (IMHO), I fix file names as they arrive myself, so the processing later doesn't get stuck.

There is a handy "rename" tool on most Linixen - **rename**. It doesn't fix those things automatically, but it is handy.  It uses regex and perl.  I remove spaces and unwanted whitespace in file names with it.

This script is named "ren-fav.sh" - as in my favorite rename fix:
```
#!/bin/sh
IN="$1"
if [ "X$IN" = "X" ] ; then
  echo "no input match. 
 Usage:
   $0 lead-character-filename-pattern
  eg.
   $0 FX
"
  exit 1
fi
rename 's/ /_/g' $IN*;
rename 's/_-_/-/g' $IN*;
rename 's/-_/-/g' $IN*

```

Generally,   I'd call it on a directory - **ren-fav.sh [A-Z]** and that would rename all the files starting with uppercase A-Z.  I've been burned by ()'"; and a few other characters - should modify the script to remote those too, but it just doesn't happen that often to have become an itched for me. ;)

---

### Post by c@ssie on 2014-09-19
> **TheFu said:**
> Remember when I said above that '.' characters screw with scripts and to avoid spaces in names?  Many special characters do that and need to be avoided *at all costs* in file/directory names.  Parenthesis, square/curly brackets, ', ", need to be included in those characters to avoid.

Not exactly relevant to the issue here, but part of the solution (IMHO), I fix file names as they arrive myself, so the processing later doesn't get stuck.

There is a handy "rename" tool on most Linixen - **rename**. It doesn't fix those things automatically, but it is handy.  It uses regex and perl.  I remove spaces and unwanted whitespace in file names with it.

This script is named "ren-fav.sh" - as in my favorite rename fix:
```
#!/bin/sh
IN="$1"
if [ "X$IN" = "X" ] ; then
  echo "no input match. 
 Usage:
   $0 lead-character-filename-pattern
  eg.
   $0 FX
"
  exit 1
fi
rename 's/ /_/g' $IN*;
rename 's/_-_/-/g' $IN*;
rename 's/-_/-/g' $IN*

```

Generally,   I'd call it on a directory - **ren-fav.sh [A-Z]** and that would rename all the files starting with uppercase A-Z.  I've been burned by ()'"; and a few other characters - should modify the script to remote those too, but it just doesn't happen that often to have become an itched for me. ;)
That would work if I had write permission on the source directory, but I don't.   The source directory belongs to someone else, and I have read only permissions.  The target directory belongs to me.

---

### Post by Vaphell on 2014-09-19
no char should be avoided at all costs, that's a huge exaggeration, though you need to know what you are up to. You can have newlines in filenames if you want, but you got to know the tricks how to deal with them


which version of bash do you have?
what happens if you run this in terminal?

```
title='Doctor Who (2005)'
printf 'name: %s\nyear: %s\n' "${title: 0:-6}" "${title: -5:-1}"
```

i get
```
name: Doctor Who 
year: 2005
```



if that really doesn't work replace this line
```
[[ $show =~ \([0-9]{4}\)$ ]] && show=${show: 0:-6}${show: -5:4}
```
with this one
```
[[ $show =~ \([0-9]{4}\)$ ]] && show=${show: 0:${#show}-6}${show: ${#show}-5:4}
```

test if it works
```
$ show='Doctor Who (2005)'
$ [[ $show =~ \([0-9]{4}\)$ ]] && show=${show: 0:${#show}-6}${show: ${#show}-5:4}
$ echo $show
Doctor Who 2005
```

---

### Post by c@ssie on 2014-09-19
> **Vaphell said:**
> no char should be avoided at all costs, that's a huge exaggeration, though you need to know what you are up to. You can have newlines in filenames if you want, but you got to know the tricks how to deal with them


which version of bash do you have?
what happens if you run this in terminal?

```
title='Doctor Who (2005)'
printf 'name: %s\nyear: %s\n' "${title: 0:-6}" "${title: -5:-1}"
```

i get
```
name: Doctor Who 
year: 2005
```



if that really doesn't work replace this line
```
[[ $show =~ \([0-9]{4}\)$ ]] && show=${show: 0:-6}${show: -5:4}
```
with this one
```
[[ $show =~ \([0-9]{4}\)$ ]] && show=${show: 0:${#show}-6}${show: ${#show}-5:4}
```

test if it works
```
$ show='Doctor Who (2005)'
$ [[ $show =~ \([0-9]{4}\)$ ]] && show=${show: 0:${#show}-6}${show: ${#show}-5:4}
$ echo $show
Doctor Who 2005
```

Thank you, that solved the problem.

---

