---
title: "is there video player that does this?"
date: 2013-06-19
forum: General Help
---

### Post by budasfeet57 on 2013-06-19
I have been watching many coursera videos recently. The subtitles are provided. And I would like to search through hundreds of subtitles to find some keywords and then the video player will play the video at the exact time the searched text appeared.

Is there such a video player out there?

---

### Post by Vaphell on 2013-06-19
what does the sub format look like?
It should be easy to whip up a script that will find the proper line in file and run a video player with start time paramater set eg
**mplayer -ss <time> <videofile>**

---

### Post by budasfeet57 on 2013-06-19
srt format.

---

### Post by Vaphell on 2013-06-20
write something about the organization of video files and subtitles. Are they in one place? Sorted to subdirs? Do video file and .srt share the name?

edit:
gnome subtitles which is a tool to edit subs could be used in your case i think. Under the video panel it has the whole sub file listed. You can perform ctrl+f (find) and double click any line to make the video play at that timestamp.

---

### Post by budasfeet57 on 2013-06-21
The subtitles have filenames as same as the videos' filenames. They are all in the same folder.

Thanks for mentioning gnome subtitles, it's good, but it does not search all the srt files at once. 

Just wondering, is it possible to program something that uses **grep** to search text, parses the time label in srt files and uses the **mplayer** command given above, to accomplish what I wanted? And where should I start if I know a little bit of c, c++, and python and has little knowledge in writing a real program that deal with system.

---

### Post by Vaphell on 2013-06-21
```
#!/bin/bash

readarray -t results < <( awk 'BEGIN { RS="\r\n\r\n"; FS="\r\n"; }
                                     {  
                                       gsub( /[<][^<>]+[>]/, "" );
                                       gsub( /,.*/, "", $2 );
                                       printf FILENAME "\t" $2 "\t";
                                       for( i=3; i<=NF; i++ )
                                         printf $i " ";
                                       printf "\n";
                                     }' *.srt | grep -i "$1" )

if [ ${#results[@]} = 0 ]
then
  echo "no matches found"
  exit
elif [ ${#results[@]} = 1 ]
then
  r=${results[0]}
else                  
  select r in "${results[@]}"; do break; done
fi

IFS=$'\t' read f ts _ <<< "$r"
f=${f/%srt/mp4}

echo "opening '$f' @ $ts"
mplayer -ss "$ts" "$f"
```

---

### Post by budasfeet57 on 2013-06-25
Thank you for the shell script. I am not very familiar with shell script, would you tell me where I should add the string I am searching? Thank you.

---

### Post by Vaphell on 2013-06-25
run it with argument where arg will be the string, eg
```
chmod +x playvideo.sh     # make script executable
./playvideo.sh "a b c"         # look for 'a b c' 
```

everything happens in the first 'line'
awk is used to flatten the srt files to easy to use format (filename, timestamp, potentially multiline text stripped of formatting markers and reduced to a single line) and then **grep -i "$1"** is what looks for the phrase ($1 = 1st parameter of the script). The results are stored in an array which is used to create a menu if more than 1 result.

if you don't want to pass the string as an argument, but prefer to be prompted for it by the script, before *readarray* line you can add
```
read -p "Enter string: " str
```
and then change **grep -i "$1"** to **grep -i "$str"**

you could also prettify the script a bit with zenity or yad - they are able to create a simple gui window to type the text which would potentially allow not to deal with terminal window at all.

---

