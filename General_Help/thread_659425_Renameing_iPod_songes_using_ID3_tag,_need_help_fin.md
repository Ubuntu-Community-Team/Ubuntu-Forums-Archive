---
title: "Renameing iPod songes using ID3 tag, need help finshing the code"
date: 2008-01-05
forum: General Help
---

### Post by uclalinux on 2008-01-05
Hello, I am trying to write a script that will read mp3 or mp4 ID3 information, and then rename using that information. I am using eyeD3 to read the ID3 information. Here is eyeD3 output
```
uclalinux@uclalinux-desktop:~/Desktop/Alissa's Music$ eyeD3 QOXA.mp3 
QOXA.mp3        [ 5.56 MB ]
--------------------------------------------------------------------------------
Time: 3:14      MPEG1, Layer III        [ ~239 kb/s @ 44100 Hz - Joint stereo ]
--------------------------------------------------------------------------------
ID3 v2.3:
title: Andy, You're A Star              artist: The Killers
album: Hot Fuss         year: 2004
track: 6                genre: Rock (id 17)
Publisher/label: Island
Comment: [Description: ] [Lang: eng]
ESCAPE
uclalinux@uclalinux-desktop:~/Desktop/iPodMusic$ 
```

I want to rename the songs from "QOXA.mp3" to "Andy,You're A Star_TheKillers.mp3"
I am still a beginner with BASH but this is what I got so far, if anyone could help that would be great because I got 996 songs to rename. 
 Also If I get this to work I think it should be posted somewhere because I think alot of people would like this script, where should I post it when it is finished?

```
for i in `ls /home/uclalinux/Desktop/iPodMusic/*.mp4`
do
  pre=${i%%\.mp4}
  eye3D $i | grep title=name((I ONLY WANT TO READ 15 characters)) && grep artist [[I ONLY WANT TO READ 12 characters]]=artist
  mv $pre.mp4 $name_$arist.mp4 
done
```

---

### Post by kidders on 2008-01-07
Hi there,

I'm confused by ...> **uclalinux said:**
> I ONLY WANT TO READ 15 characters... and ...> **uclalinux said:**
> I ONLY WANT TO READ 12 charactersI can't figure out where the 15 & 12 come from. :confused:

In any case, there's a massive variety of ways of truncating strings. One that jumps immediately to mind is...```
echo "12345678" | sed 's/\(^.\{5\}\).*/\1/'
```This example truncates "12345678" to a 5-character string. The reason I chose **sed** is that you might want to do some other things while you're performing the truncation, such as stripping away leading/trailing whitespace, so you never end up with [FONT=Courier New]"   The kille"[/FONT] (12 chars) instead of [FONT=Courier New]"The killers"[/FONT] (11 chars). Sed is flexible enough to let you do that sort of thing.

I hope that helps.

---

### Post by uclalinux on 2008-01-07
I think I explained it poorly, When i grep title the entire line of 
```
title: Andy, You're A Star              artist: The Killers
``` 
is returned, but I only what the title "Andy, You're A Star", and when I grep "artist" I only want "The Killers" the problem is I don't know how to only get that information.

---

### Post by kidders on 2008-01-08
Whoops... sorry. I missed that!

You could use sed for that too, if you like. For example...```
echo "title: Andy, You're A Star              artist: The Killers" | sed 's/title: \(.*\)artist:.*/\1/'
```
If, for some reason, artist/album information were unavailable though, the results might be unpredictable, so perhaps there might be a better way of doing it. Whatever approach you take, some kind of regular expression pattern matching is probably the way to go,

---

### Post by uclalinux on 2008-01-08
Kidders, that's exactly what I was looking for. :) Also I think this is a usefully script, where could I post it for others to find it?   Thanks

---

### Post by kidders on 2008-01-08
Right here. :-) ... Googlebot crawls these pages almost constantly, and the forum's own search facility should pick your thread up too. It's a pity there are misspellings in the title though.

You can see how many people have viewed the thread here ... [http://ubuntuforums.org/search.php?do=process&query=4080106](http://ubuntuforums.org/search.php?do=process&query=4080106)

---

### Post by uclalinux on 2008-01-21
For m4a I found this 

```
#!/bin/bash
for i in "where music is"/*.m4a
do
base=`basename "$i" .m4a`
info=`faad -i "$i" 2>&1`
artist=`echo "$info" | grep artist: | sed s/artist:\ //g`
album=`echo "$info" | grep album: | sed s/album:\ //g`
song=`echo "$info" | grep title: | sed s/title:\ //g`
track=`echo "$info" | grep track: | sed s/track:\ //g`
year=`echo "$info" | grep date: | sed s/date:\ //g`
genre=`echo "$info" | grep genre: | sed s/genre:\ //g`
#faad -w "$i"| lame -h -b 128 - "$base.mp3"
#id3 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
#id3v2 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.m4a"
mv "$i" "/home/uclalinux/Desktop/AlissaMusic/F00/$song\_$artist.m4a"
done
```, 
this code also converts the m4a to a mp3, if you want but I didn't need  that. I found it at this site [http://ubuntuforums.org/archive/index.php/t-57282.html](http://ubuntuforums.org/archive/index.php/t-57282.html)

and for MP3 i found a program  called id3ren

---

### Post by nick_h on 2008-01-22
It looks like you can just use the --rename option of eyeD3 to do the whole rename in one step.

Type:
```
eyeD3 --help
```
for details or have a look at [this](http://eyed3.nicfit.net/) page.

---

### Post by pointone on 2008-01-22
Not sure if you're still looking or not, but I created my own little script in Python to accomplish this task not long ago. None of the readily available programs allowed me to rename files in exactly the format I wanted; all of them used some sort of directory structure, as in "/music/Artist/Album/Track - Title.mp3".

I wanted all files in the same base directory, as in "/music/Artist - Album [Track] Title.mp3".

My script only works with .mp3 and .ogg files, though, and doesn't search through subdirectories or support renaming into subdirectories.

It's still a work in progress, though; I'm hoping to add these features eventually.

Give it a try if you want. It successfully renamed my 4000+ file music collection without issue, but I accept no responsibility, etc. for any damages!

You'll need to install the python-mutagen package first, too (it's in the repos).

---

### Post by crshman on 2008-04-13
Here is my version of the script using strictly bash.

**_Instructions:_**
[LIST=1]
[*]Edit the "$PRE_DEST" variable to whatever directory you want to move your files into
[*]Modify the "$FOLDER" and "$DEST" variables to reflect your preferences
[*]Run the script in the directory that contains your .mp3 files
[*]Sit back and relax as the script runs
[/LIST]

**_Caveats_**
[LIST=1]
[*]Untested for subdirectories
[*]Must have id3tool installed
[/LIST]

The Script:
```
#!/bin/bash

LIVE=
# Set to some value for live operation
# ex
# $LIVE=a
# the script will move files around
#
# $LIVE=
# the script won't move anything around

PRE_DEST='/media/Data/Share/Music/'
# Local directory to move files to

for file in *.mp3; do
SP_TITLE="`id3tool "$file" | grep '^Song Title:' | awk '{ for (i=3;i<=NF;i++) { printf $i; printf " " } }'`"
TITLE=${SP_TITLE:0:$((${#SP_TITLE}-1))}
# Title of the track

SP_ARTIST="`id3tool "$file" | grep '^Artist:' | awk '{ for (i=2;i<=NF;i++) { printf $i; printf " " } }'`"
ARTIST=${SP_ARTIST:0:$((${#SP_ARTIST}-1))}
# Artist of the track

FIRST_ARTIST=${ARTIST:0:1}
# First Letter of the artist of the track

SP_ALBUM="`id3tool "$file" | grep '^Album:' | awk '{ for (i=2;i<=NF;i++) { printf $i; printf " " } }'`"
ALBUM=${SP_ALBUM:0:$((${#SP_ALBUM}-1))}
# Album name

SP_YEAR="`id3tool "$file" | grep '^Year:' | awk '{ for (i=2;i<=NF;i++) { printf $i; printf " " } }'`"
YEAR=${SP_YEAR:0:$((${#SP_YEAR}-1))}
# Year of album

TRACKNUM="`id3tool "$file" | grep '^Track:' | awk '{ print $2 }'`"
# Track Title

#Edit these to reflect your preferences
FOLDER="$PRE_DEST$FIRST_ARTIST/$ARTIST/$ALBUM ($YEAR)"
DEST="$FOLDER/$TRACKNUM - $TITLE.mp3"

echo $file
echo $DEST
echo -e "\n"
if [ $LIVE ]; then
mkdir -p "$FOLDER"
mv "$file" "$DEST"
fi
done
```

---

### Post by crshman on 2008-04-13
Here is my version of the script using strictly bash.

_**Updated to read id3v2 tags**_

**_Instructions:_**
[LIST=1]
[*]Edit the "$PRE_DEST" variable to whatever directory you want to move your files into
[*]Modify the "$FOLDER" and "$DEST" variables to reflect your preferences
[*]Run the script in the directory that contains your .mp3 files
[*]Sit back and relax as the script runs
[/LIST]

**_Caveats_**
[LIST=1]
[*]Untested for subdirectories
[*]Must have id3v2 installed
[/LIST]

The Script:
```
#!/bin/bash

# Script By Robert Navarro
# crshman [at] gmail.com
#
# Rename/Moves MP3 files based on
# id3v2 tags

LIVE=
#
# Set to some value for live operation
# ex
# $LIVE=Yes
# the script will move files around
#
# $LIVE=
# the script won't move anything around

PRE_DEST='/media/Data/Share/Music/'
# Local directory to move files to

for file in *.mp3; do
if [ -e $file ]; then
TRACK="`id3v2 -l "$file" | grep TRCK | awk '{ for (i=6;i<=NF;i++) { printf $i; printf " " } }'`"
# Track Number

SP_YEAR="`id3v2 -l "$file" | grep TYER | awk '{ for (i=3;i<=NF;i++) { printf $i; printf " " } }'`"
YEAR=${SP_YEAR:0:$((${#SP_YEAR}-1))}
# Track Year

SP_ARTIST="`id3v2 -l "$file" | grep TPE1 | awk '{ for (i=4;i<=NF;i++) { printf $i; printf " " } }'`"
ARTIST=${SP_ARTIST:0:$((${#SP_ARTIST}-1))}
# Track Artist

FIRST_ARTIST=${ARTIST:0:1}
# First Letter of the Artist of the Track

SP_ALBUM="`id3v2 -l "$file" | grep TALB | awk '{ for (i=4;i<=NF;i++) { printf $i; printf " " } }'`"
ALBUM=${SP_ALBUM:0:$((${#SP_ALBUM}-1))}
# Track Album

SP_TITLE="`id3v2 -l "$file" | grep TIT2 | awk '{ for (i=4;i<=NF;i++) { printf $i; printf " " } }'`"
TITLE=${SP_TITLE:0:$((${#SP_TITLE}-1))}
# Track TITLE


#Edit these to reflect your preferences
FOLDER="$PRE_DEST$FIRST_ARTIST/$ARTIST/$ALBUM ($YEAR)"
DEST="$FOLDER/$TRACK - $TITLE.mp3"

#echo $file
#echo $FOLDER
#echo $DEST
#echo -e "\n"
if [ $LIVE ]; then
mkdir -p "$FOLDER"
mv "$file" "$DEST"
fi
fi
done
```

---

