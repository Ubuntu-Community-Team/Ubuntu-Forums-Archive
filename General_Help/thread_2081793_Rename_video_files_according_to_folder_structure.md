---
title: "Rename video files according to folder structure"
date: 2012-11-07
forum: General Help
---

### Post by HiImTye on 2012-11-07
I made a new bash script! this one takes your video files from your TV folder and renames them according to your folder structure. here's how it works:

it assumes your folder structure is like so:
```
../base TV folder/Show Title (year)/Season #/Video File Name.Episode #.garbage stuff after.extension
```it extracts the following information:
```
../base TV folder/[COLOR=DarkGreen]Show Title [COLOR=Black](year)[/COLOR][/COLOR]/Season [COLOR=DarkRed]#[/COLOR]/Video File Name.Episode [COLOR=Blue]#[/COLOR].[COLOR=Purple]garbage stuff after[/COLOR].[COLOR=Sienna]extension[/COLOR]
```then it renames it as so:
```
../base TV folder/Show Title (year)/Season #/[COLOR=DarkGreen]Show Title[/COLOR].S[COLOR=DarkRed]##[/COLOR]E[COLOR=Blue]##[/COLOR].[COLOR=Sienna]extension[/COLOR]
```I know, you may be thinking "what about the 'garbage stuff after extension? that's purple!" and you're right! it keeps that data for the last step! it offers to tag the file with the episode information in the 'title' field, like so:
```
[COLOR=DarkGreen]Show Title[/COLOR] S[COLOR=DarkRed]##[/COLOR]E[COLOR=Blue]##[/COLOR]: [COLOR=Purple]garbage stuff after[/COLOR]
```this pops up in a little window like so:
[ATTACH]226843[/ATTACH]
as you can see, it also gives you the new file name in the popup! it also removes 'x264' and 'h264' in advance, since they would mess with episodes that just use a '###' episode number.
anyways, it tags videos using ffmpeg, so make sure you have that installed! (it works using the ffmpeg in the repos, that's the version I'm using)

the script accepts the following  episode naming conventions:
```
episode [COLOR=Blue]#[/COLOR]
s##e[COLOR=Blue]##[/COLOR]
#x[COLOR=Blue]##[/COLOR]
#[COLOR=Blue]##[/COLOR]
```so long as your folder structure is as above (including the year)

make sure that you change the 'VideosPath' variable to the base folder of your TV episodes.
for instance, if you want it to be the home folder of every user, use something like
```
VideosPath='$HOME/Videos/TV/'
```I separated the ffmpeg job into a second bash script, so that I could both detach the ffmpeg process from the terminal (allowing it to move on to the next file), test the results to make sure that the file size is different, and output the results of that test to a text file. the path to the ffmpeg script needs to be specified in the main script so that it can run it. on my system I keep all of my bash scripts in '$HOME/Launchers' so that's where its' default is.

the main script outputs to 'out.txt' and the ffmpeg script outputs to 'fout.txt' - both in the folder that you run the main script from.

Clean Filenames.sh
```
#!/bin/bash

VideosPath='$HOME/Videos/TV/'
tagVideosCore=$HOME/Launchers/tagVideosCore.sh

# create a temporary database of our videos path, to ensure all file names used by
 # 'locate' are current
updatedb -l 0 -o temp.db -U "$VideosPath"
# empty our ffmpeg output file
echo > fout.txt

while read -r f; do
 echo '****************' > out.txt
 echo  >> out.txt
 echo "$f" >> out.txt
 # rename episodes according to their folder names, and format episode string
  # as 'S##E##', according to their path and filename
 # remove 'h264' and 'x264' from filenames as they are troublesome and we are
  # just going to remove them later anyways
 nF=$(echo "$f" | sed 's|[xXhH]264||g')
 nF2="$nF"
 # for 'e##' type filenames
 if [[ "$nF2" =~ [sS][0-9]{1,2}[eE][0-9]{2} ]]; then
  echo matches 'e##' pattern >> out.txt
  nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\})/[sS]eason \)\([0-9]\{1,2\}\)/.*[0-9][eE]\([0-9]\{2\}\)|\1\2\3\4/\2.S\4E\5|')
 # for 'episode ##' type filenames
 elif [[ "$nF2" =~ [eE]pisode[\ .]?[0-9]{1,2} ]]; then
  echo matches 'episode ##' pattern >> out.txt
  nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\})/[sS]eason \)\([0-9]\{1,2\}\)/.*[eE]pisode[ .]\{0,1\}\([0-9]\{1,2\}\)|\1\2\3\4/\2.S\4E\5|')
 # for '#x##' type filenames
 elif [[ "$nF2" =~ [0-9][xX][0-9]{1,2} ]]; then
  echo matches '#x##' pattern >> out.txt
  nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\})/[sS]eason \)\([0-9]\{1,2\}\)/.*[0-9][xX]\([0-9]\{1,2\}\)|\1\2\3\4/\2.S\4E\5|')
 # for '###' type filenames
 elif [[ "$nF2" =~ [^0-9][0-9]{3}[^0-9] ]]; then
  echo matches '###' pattern >> out.txt
  nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\})/[sS]eason \)\([0-9]\{1,2\}\)/.*[0-9]\([0-9]\{2\}\)|\1\2\3\4/\2.S\4E\5|')
 else
  echo did not match any pattern, continuing >> out.txt
  continue
 fi
  # ensure 'S##' and 'E##' if only either 'S#' or 'E#'
 nF2=$(echo "$nF2" | sed 's|S\([0-9][^0-9]\)|S0\1|;s|E\([0-9][^0-9]\)|E0\1|')
 echo "$f"
 echo "$nF"
 echo "$nF2"
 # make sure we are actually doing work
 if [ "$nF" = "$nF2" ]; then
  echo false match, continuing >> out.txt
  echo >> out.txt
  echo '****************' >> out.txt
  continue
 else
  nF="$nF2"
 fi
 # configure 'title' metadata
 echo renaming as: >> out.txt
 echo "$nF" >> out.txt
 Title="${nF%.*}"
 Title=$(echo "${Title##*/}" | sed 's|\(.*\)[ .]\([sS][0-9]\{2\}[eE][0-9]\{2\}\)|\1 \U\2: |;s|\([eE][0-9]\{2\}: \)\.|\1|')
 Title=$(zenity --entry --title="Video Title" \
  --text="Enter a new title for the video  file $Title." --entry-text="$Title")
 # strip garbage between episode number and extension,
  # then make file extensions lowercase
 nF=$(echo $nF | sed 's|\(E[0-9]\{2\}\).*\(\.[a-zA-Z0-9]*\)$|\1\L\2\E|')
 # do work
 if [ -n "$Title" ]; then
  # add title metadata if it exists
  gnome-terminal -x $tagVideosCore "$f" "$nF" "$Title"
  echo tagging video file with ffmpeg, refer to fout.txt to see results >> out.txt
 else
  mv -f "$f" "$nF"
 fi
echo  >> out.txt
echo '****************' >> out.txt
done < <(locate -q -d temp.db *.avi *.mkv *.mp4)
# delete our temporary database
rm -f temp.db
exit
```tagVideosCore.sh
```
#!/bin/bash
echo tagging video file "$1" >> fout.txt
echo ffmpeg -i "$1" -metadata title="$3" -acodec copy -vcodec copy -scodec copy "$2"
ffmpeg -i "$1" -metadata title="$3" \
 -acodec copy -vcodec copy -scodec copy "$2"
file_f=$(stat -c %s "$1")
file_nF=$(stat -c %s "$2")
if [ "$file_nF" -gt "$file_f" ]; then
 echo new file "$2" larger than old file, deleting old file >> fout.txt
 rm -f "$1"
else
 echo new file "$2" not larger than old file, skipping >> fout.txt
 rm -f "$2"
fi

exit
```

---

