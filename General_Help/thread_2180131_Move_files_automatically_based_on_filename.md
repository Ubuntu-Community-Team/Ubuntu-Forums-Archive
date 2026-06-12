---
title: "Move files automatically based on filename?"
date: 2013-10-11
forum: General Help
---

### Post by derekcentrico on 2013-10-11
I'm trying to find a way to automatically move files in a folder (recursively and not recursively depending on the path) based upon their names into files.

The files are like "Name 01x01 Episode Title.mkv."  I'd like them to be moved to a folder tree like ./Name/Season 01/ where 01 comes from 01x.  

Any thoughts on how to do this?  I'd be running it following an automated filebot command:

```
filebot -rename /media/storage2/videos/ --db TheTVDB non-strict --lang en --action move --conflict skip --def music=n --def artwork=y --def xbmc=192.168.1.49 

```

Thanks in advance!

---

### Post by Vaphell on 2013-10-11
```
for f in *.mkv
do
  dest=$( echo "$f" | sed -r 's:(.*) ([0-9]+)x[0-9]+(.*):\1/Season \2:' )
  mkdir -p "$dest"
  mv -vt "$dest" "$f"
done
```

test
```
$ touch 'Name 02x11 xoxoxo.mkv' 'Some name 03x11 Title.mkv' 'Yet another name 11x111 EpTitle.mkv'
$ for f in *.mkv; do dest=$( echo "$f" | sed -r 's:(.*) ([0-9]+)x[0-9]+(.*):\1/Season \2:' ); mkdir -p "$dest"; mv -vt "$dest" "$f"; done
`Name 02x11 xoxoxo.mkv' -> `Name/Season 02/Name 02x11 xoxoxo.mkv'
`Some name 03x11 Title.mkv' -> `Some name/Season 03/Some name 03x11 Title.mkv'
`Yet another name 11x111 EpTitle.mkv' -> `Yet another name/Season 11/Yet another name 11x111 EpTitle.mkv'
```

as for recursive approach, you'd have to write a bit more about your setup end expected results. Scattered files should be sorted to subdirs in a master dir or to subdirs of their current location?

---

### Post by derekcentrico on 2013-10-11
You're awesome!  Thanks so much for this!

The other approach would be to move a file (.mkv) from a subdirectory to the parent, then remove the subdirectory is possible.  

I'm trying to get this XBMC thing going...  Soooo sorting seems to be important for its library structure.

---

### Post by derekcentrico on 2013-10-11
Crap, I didn't notice there are some that are named like "Name - 01x01 -Episode Title.mkv."

I'm reading the sed manpage and to be honest feel like a total buffoon. 

Does the line just become this for those files: ```
  dest=$( echo "$f" | sed -r 's:(.*) **-** ([0-9]+)x[0-9]+( **-** .*):\1/Season \2:' )
``` ?

---

### Post by Vaphell on 2013-10-11
yes, figuring out the name formats is the hard part. People use spaces, dots, - and seasons come in 09x99, [9x99] or s09e99

my attempt
sortvideos.sh
```

#!/bin/bash

root=.
ep_rgx='(\[?|s)([0-9])+[ex][0-9]+\]?'
ext_rgx='avi|mkv'
rgx=".*($ep_rgx).*\.($ext_rgx)\$"

while read -rd $'\0' f
do
  path=${f%/*}
  fname=${f##*/}
  dest=$root/$( echo "$fname" | sed -r "s:(.*[^. -])[. -]+${ep_rgx}.*$:\1/Season \3:" )
  printf -v dest "%s %02d" "${dest% *}" $(( 10#${dest##* } ))
  echo "is in '$path', should be in '$dest'"
  if [ "$path" = "$dest" ]
  then
    echo "'$fname' in proper place ('$path')"
    echo
    continue
  else
    echo "'$fname' should be in '$dest', is in '$path'"
    mkdir -p "$dest"
    mv -vt "$dest" -- "$f"
  fi
done < <( find "$root" -regextype posix-extended -iregex "$rgx" -print0 )

# del empty dirs
find "$root" -depth -type d -empty -delete

```

i test this using this script which creates dummy dirs/files, runs the scripts and shows before/after
run_test.sh
```
#!/bin/bash

rm -rf ./*/ ./*.avi ./*.mkv

# dummy dirs/files
touch 'awesome movie.avi'
touch 'unnamed (1).mkv'
touch 'some.mkvfile.[01x01] mkv.mkv'
touch 'Yet Another One --- 03x11 mkv.mkv'
mkdir -p 'junk_dir1' 'junk_dir2/garbage'
touch 'junk_dir1/Trolololo s02e11 Episode 11.avi' 'junk_dir1/Trolololo s02e12 Episode 12.avi' 'junk_dir1/Trolololo 2x13 Ep 13.avi'
touch 'junk_dir2/garbage/Title s02e11 lulz.avi'
mkdir -p 'Proper Dir/Season 05/'
touch 'Proper Dir/Season 05/Proper Dir s05e05 - Ep 5.avi'
touch 'Proper Dir/Season 05/Proper Dir s08e11 - What u doin here, moron.avi'
mkdir -p 'junk_dir1/Wrong Place/Season 01/'
touch 'junk_dir1/Wrong Place/Season 01/Wrong Place [03e105] - E105.avi'

echo "TEST: BEFORE ----------------------------------------------------"
tree
# run script with suppressed output 
./sortvideos.sh &> /dev/null
echo "TEST: AFTER------------------------------------------------------"
tree
```

results of the test
```
$ ./run_test.sh
TEST: BEFORE ----------------------------------------------------
.
&#9500;&#9472;&#9472; awesome movie.avi
&#9500;&#9472;&#9472; junk_dir1
&#9474;** &#9500;&#9472;&#9472; Trolololo 2x13 Ep 13.avi
&#9474;** &#9500;&#9472;&#9472; Trolololo s02e11 Episode 11.avi
&#9474;** &#9500;&#9472;&#9472; Trolololo s02e12 Episode 12.avi
&#9474;** &#9492;&#9472;&#9472; Wrong Place
&#9474;**     &#9492;&#9472;&#9472; Season 01
&#9474;**         &#9492;&#9472;&#9472; Wrong Place [03e105] - E105.avi
&#9500;&#9472;&#9472; junk_dir2
&#9474;** &#9492;&#9472;&#9472; garbage
&#9474;**     &#9492;&#9472;&#9472; Title s02e11 lulz.avi
&#9500;&#9472;&#9472; Proper Dir
&#9474;** &#9492;&#9472;&#9472; Season 05
&#9474;**     &#9500;&#9472;&#9472; Proper Dir s05e05 - Ep 5.avi
&#9474;**     &#9492;&#9472;&#9472; Proper Dir s08e11 - What u doin here, moron.avi
&#9500;&#9472;&#9472; run_test.sh
&#9500;&#9472;&#9472; some.mkvfile.[01x01] mkv.mkv
&#9500;&#9472;&#9472; sortvideos.sh
&#9500;&#9472;&#9472; unnamed (1).mkv
&#9492;&#9472;&#9472; Yet Another One --- 03x11 mkv.mkv

7 directories, 13 files
TEST: AFTER------------------------------------------------------
.
&#9500;&#9472;&#9472; awesome movie.avi
&#9500;&#9472;&#9472; Proper Dir
&#9474;** &#9500;&#9472;&#9472; Season 05
&#9474;** &#9474;** &#9492;&#9472;&#9472; Proper Dir s05e05 - Ep 5.avi
&#9474;** &#9492;&#9472;&#9472; Season 08
&#9474;**     &#9492;&#9472;&#9472; Proper Dir s08e11 - What u doin here, moron.avi
&#9500;&#9472;&#9472; run_test.sh
&#9500;&#9472;&#9472; some.mkvfile
&#9474;** &#9492;&#9472;&#9472; Season 01
&#9474;**     &#9492;&#9472;&#9472; some.mkvfile.[01x01] mkv.mkv
&#9500;&#9472;&#9472; sortvideos.sh
&#9500;&#9472;&#9472; Title
&#9474;** &#9492;&#9472;&#9472; Season 02
&#9474;**     &#9492;&#9472;&#9472; Title s02e11 lulz.avi
&#9500;&#9472;&#9472; Trolololo
&#9474;** &#9492;&#9472;&#9472; Season 02
&#9474;**     &#9500;&#9472;&#9472; Trolololo 2x13 Ep 13.avi
&#9474;**     &#9500;&#9472;&#9472; Trolololo s02e11 Episode 11.avi
&#9474;**     &#9492;&#9472;&#9472; Trolololo s02e12 Episode 12.avi
&#9500;&#9472;&#9472; unnamed (1).mkv
&#9500;&#9472;&#9472; Wrong Place
&#9474;** &#9492;&#9472;&#9472; Season 03
&#9474;**     &#9492;&#9472;&#9472; Wrong Place [03e105] - E105.avi
&#9492;&#9472;&#9472; Yet Another One
    &#9492;&#9472;&#9472; Season 03
        &#9492;&#9472;&#9472; Yet Another One --- 03x11 mkv.mkv

13 directories, 13 files
```
play with these scritpts in some sandbox dir where no disaster can happen, try to find broken filename formats :)

---

### Post by derekcentrico on 2013-10-12
That worked amazingly for Seasons 1 - 9 of shows.  Seasons 10 and above were messed up.

Season 10 becomes Season 00.
Season 11 becomes Season 01 (and joins actual Season 1 files)
Season 12 becomes Season 02 (and joins actual Season 2 files)

---

### Post by Vaphell on 2013-10-12
subtle mistake: i typed ([0-9])+ instead of ([0-9]+)

try this one
```
ep_rgx='(\[?|[sS])([0-9]+)[Eex][0-9]+\]?'
```

and maybe add -i switch to mv (mv -ivt), so it asks about overwrite, should such a situation happen. Generate a collision and see what happens.

---

### Post by derekcentrico on 2013-10-12
That worked perfectly!  Man you're awesome.  Wish they had a thanks meter here so I could click it profusely.  

One last question for a bit here...  Let's say the files to be sorted are in /path/to/recent/downloads/shows and I want them to be sorted and moved into /path/to/xbmc/library/shows/.  

The script would execute from within the ..../downloads/ path.

Would I change these lines:
```
    mkdir -p "$dest"
    mv -vt "$dest" -- "$f"
```

So that $dest becomes /path/to/xbmc/library/shows/$dest?

---

### Post by Vaphell on 2013-10-12
```
#!/bin/bash

[COLOR="#0000FF"]src=$HOME/test/sort_mkv
sorted=$HOME/test/sort_mkv_dest[/COLOR]

ep_rgx='(\[?|[sS])([0-9]+)[Eex][0-9]+\]?'
ext_rgx='avi|mkv'
rgx=".*($ep_rgx).*\.($ext_rgx)\$"

while read -r -u3 -d $'\0' f
do
  path=${f%/*}
  fname=${f##*/}
  dest=$sorted/$( echo "$fname" | sed -r "s:(.*[^. -])[. -]+${ep_rgx}.*$:\1/Season \3:" )
#  echo "=== $dest"
  printf -v dest "%s %02d" "${dest% *}" $(( 10#${dest##* } ))
  echo "is in '$path', should be in '$dest'"
  if [ "$path" = "$dest" ]
  then
    echo "'$fname' in proper place ('$path')"
    echo
    continue
  else
    echo "'$fname' should be in '$dest', is in '$path'"
    mkdir -p "$dest"
    mv -ivt "$dest" -- "$f"
  fi
done 3< <( find "$src" -regextype posix-extended -iregex "$rgx" -print0 )

# del empty dirs
find "$src" -depth -type d -empty -delete

```
again, test it
tweak run_test script to show also dest locations afterwards, eg
```
#!/bin/bash

test_dest=../sort_mkv_dest
rm -rf ./*/ *.avi *.mkv
rm -rf "${test_dest}"/*

# dummy dirs/files
touch 'awesome movie.avi'
touch 'unnamed (1).mkv'
# etc etc ...


echo "TEST: BEFORE ----------------------------------------------------"
tree
# run script, suppress output 
./sortvideos.sh #&> /dev/null
echo "TEST: AFTER------------------------------------------------------"
tree .
tree "${test_dest}"
```

I hope you don't keep partial downloads in your source dir :-)

---

### Post by derekcentrico on 2013-10-12
Works perfectly yet again.

Let's say that I have a special directory for files that I want to only go to the root of sorted.  So, /path/to/downloads/special/*.mkv goes to /path/to/xbmc/library/special/ instead of being sorted into directories in any form.  Would I just remove the sed expression?

---

### Post by Vaphell on 2013-10-12
just move these files away before the main part of the script. If the files are not there anymore, they wont be found and sorted

```
#!/bin/bash

# configure these dirs
src=$HOME/test/sort_mkv
sorted=$HOME/test/sort_mkv_dest
[COLOR="#0000FF"]src_special=$src/special
special=$sorted/special[/COLOR]

[COLOR="#0000FF"]mv -ivt "$special" "$src_special"/*[/COLOR]

ep_rgx='(\[?|[sS])([0-9]+)[Eex][0-9]+\]?'
ext_rgx='avi|mkv'
rgx=".*($ep_rgx).*\.($ext_rgx)\$"

while read -r -u3 -d $'\0' f
...
```

---

### Post by derekcentrico on 2013-10-12
Thanks so much for all the help.  I marked the thread as SOLVED.  Hopefully my mind won't come up with any alternatives!  :)

---

### Post by derekcentrico on 2013-10-20
While I consider this solved generally, I ran into a quirky issue.  For the first time that I can recall, a TV show had a sample along with the main video file.

I'm wondering if there's any suggestion as to how to ensure that file is deleted and not processed/moved instead of the real file?  

I think most have the word "sample" in their filenames.  So, my solution is to just use:
```
[COLOR=#111111][FONT=monospace]find . -type f -name "*sample*" -exec rm -f {} \;[/FONT][/COLOR]
```

However, this might be more inefficient than something else...

Suggestions are welcome.

I will post my final setup after resolving the kinks!  ;)

---

### Post by Vaphell on 2013-10-20
you can use -*delete* flag to replace *-exec rm*

It is possible to ignore some files (by adding *-a -not -iname '*sample*'* in this case) but given that you don't care about these files and you want to purge the dirs afterwards preemptive deletion is ok and makes the main task of sorting easier.

preprocessing of input files with find is somewhat wasteful though (2x find) so maybe you can add a condition at the top of the main loop body that checks for the sample string and if it's met, the script deletes the file and jumps to the next file, eg

```

if [[ $f =~ .*[Ss][Aa][Mm][Pp][Ll][Ee].* ]]
then
  rm "$f"
  continue
fi
```



But... what happens when the tv show has sample in the title? ;-)

---

### Post by derekcentrico on 2013-10-21
> **Vaphell said:**
> 

But... what happens when the tv show has sample in the title? ;-)

Valid point.  I wasn't sure about that.  But, the filenames have sample listed at some point after the TV show's name.  I guess it could be possible to find sample after the TV show name and delete that file?

---

### Post by Vaphell on 2013-10-21
after the show name, as in the episode title? Criminal Series [11x11] Blood Sample.avi, now what? ;-)

i think the only safe way is to create a purgatory where *sample*'s land before the main procedure and to check them by hand afterwards. The script would print out a clear warning at the end that there are unresolved cases in purgatory so you know to look there.

---

### Post by derekcentrico on 2013-10-21
Like, "Criminal series * sample * .ext" was my train of thought.  But the likelihood of a series being that and WORTH having isn't so high! 

Here's what I got.  I assume this is what you're suggesting with the insertion above the rest of the script. 

```
#!/bin/bash

#Artwork and Show data
filebot xxxxxxxxxxxxx (FILL THIS IN WITH WHAT YOU WANT)

# rename, move, and organize script
src=/media/path/to/downloads/shows/
sorted=/media/path/to/xbmc/shows/

ep_rgx='(\[?|[sS])([0-9]+)[Eex][0-9]+\]?'
ext_rgx='avi|mkv|mp4|mpg'
rgx=".*($ep_rgx).*\.($ext_rgx)\$"

while read -r -u3 -d $'\0' f
do
if [[ $f =~ .*[Ss][Aa][Mm][Pp][Ll][Ee].* ]]
then
  rm "$f"
  continue
fi

  path=${f%/*}
  fname=${f##*/}
  dest=$sorted/$( echo "$fname" | sed -r "s:(.*[^. -])[. -]+${ep_rgx}.*$:\1/Season \3:" )
#  echo "=== $dest"
  printf -v dest "%s %02d" "${dest% *}" $(( 10#${dest##* } ))
  echo "is in '$path', should be in '$dest'"
  if [ "$path" = "$dest" ]
  then
    echo "'$fname' in proper place ('$path')"
    echo
    continue
  else
    echo "'$fname' should be in '$dest', is in '$path'"
    mkdir -p "$dest"
    mv -ivt "$dest" -- "$f"
  fi
done 3< <( find "$src" -regextype posix-extended -iregex "$rgx" -print0 )


# del empty dirs
find "$src" -depth -type d -empty -delete
```

---

### Post by wright.matt.a on 2014-06-20
This script is awesome, but I'm having one problem. When my files download they come with periods instead of spaces throughout (including the show title). Everything in the sorting works, but is it possible to replace the periods with spaces in the directory name (show title) before creating the directory or moving the file? Currently a show titled "South.Park.S17E09.PROPER.HDTV.XviD-AFG.avi" would move into a folder called "South.Park" instead of "South Park".

---

