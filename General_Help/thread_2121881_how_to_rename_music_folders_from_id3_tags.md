---
title: "how to rename music folders from id3 tags"
date: 2013-03-03
forum: General Help
---

### Post by asensio on 2013-03-03
Hi guys,

this must be very simple, but i'm not getting to do it...

I have my, rather big, music colection in folders in this form: **Artist - Album**
and I want to rename my folders so they look like this: **Artist - Album (Album Year)**
Simply, I just want to add the "Album Year", inside brackets, to the folder name... but the "Album Year" should only appear if the ID3 tag has that information, if not, keep inicial form.

I tried to do this with a Rhythmbox plugin, "fileorganizer" I think, but it messed up my sample of 10 albuns (sample, in case something went wrong) and added year "0" when ID3 has no year...

Can this be done easily in the command line? Or is there an application that can do this?
If there's a script, or someone can lend a hand on writing one, if it helps, I can copy my colection when renaming it.

I will be very grateful for any help
Cheers
**ASENSIO**

---

### Post by Vaphell on 2013-03-03
> Can this be done easily in the command line?
yes

are the files in album tagged uniformly? or is there a possibility that there are files with different year (maybe some kind of best of collection) or some do have it and some dont?

---

### Post by asensio on 2013-03-03
Thanks for your reply, Vaphell.

All the files are tagged uniformly, I've been using MusicBrainz Picard for tagging. It sets the year for all the files of the folder... when, for some reason, it can't set the year in all files of the album I leave it blank.

Cheers
**ASENSIO**

---

### Post by Vaphell on 2013-03-04
```
#!/bin/bash

music=$HOME/Music    # path of music collection
shopt -s nullglob

while read -rd $'\0' d
do
  [[ $d =~ .*[(][0-9]{4}[)]$ ]] && echo "skipping '$d'" && continue
  year=''
  for f in "$d"/*.[mM][pP]3
  do
    year=$( mp3info2 -p '%y' "$f" )
    break
  done
  
  if [ "$year" ]
  then
    echo "$year: $d"
    echo mv -- "$d" "$d ($year)"    # if the printout is ok, remove echo to perform mv
  else
    echo "????: $d"
  fi
done < <( find "$music" -mindepth 1 -type d -print0 )
```

this script ignores directories in XXX (2000) format, checks the first file in each dir (requires mp3info2) and if the year is not empty, it prints the mv command that is supposed to be run. If you like what you see, remove *echo* to actually do mv-ing.

---

### Post by asensio on 2013-03-04
First of all, thank you very much for your trouble, Vaphell.

The script works perfectly, but seems that several files have the YEAR tag in the format **YYYY-MM-DD** (example, using mp3info2 - Album: The Feeding   Year: 2005-02-15)
Weird, for the same album of that example, rhythmbox only shows the year 2005, no month and no day... that's why I told my tags where uniform. I was wrong...

I hope it's not too much to ask but is there anyway to amend the script so it cuts the date so I can get only the year?
Sorry about the extra work and thanks again.
**ASENSIO**

---

### Post by CaptainMark on 2013-03-04
banshee will keep your music folder organized and it has an option to use the format you requested too in "preferences>source specific>music>tick update file & folder name / folder hierarchy". 

If you do decide to use banshee then for the intial addding of your current music I would use the option "preferences>source specific>copy files to media folder when importing", then move your music collection out of your music folder, empty your banshee library then reimport your music through banshee this will copy your music files back to your music folder.  This sounds stupid but banshees music organiser is excellent at organising music you add through banshee but not so excellent at re-organising and moving an existing collection and this method will avoid getting a load of broken links in the banshee library and avoid empty folders in your music folder, banshee does have an annoying habit of doing that because the organiser won't remove empty directories

---

### Post by asensio on 2013-03-04
Thanks for the reply CaptainMark,

I tried to use banshee, not for this specifically, but to use normaly as a audio player, about 3 to 6 months ago... but adding my collection to the library kept crashing banshee, i tried several times and gave up. If nothing else works, I'll give it a go again. I don't think I'll switch from rhythmbox, but I can use banshee just to do this little, and apparently simple, job :)

Cheers
**ASENSIO**

---

### Post by Vaphell on 2013-03-04
in the script replace $year with ${year:0:4}, it will take only first four chars

```
$ year=2011-11-15
$ echo $year
2011-11-15
$ echo ${year:0:4}
2011
```

---

### Post by asensio on 2013-03-04
it worked perfectly, thank you very much Vaphell. My music collection is exactly has i wanted :)

I think this thread is Solved

Again, thanks for your help
Cheers
**ASENSIO**

---

