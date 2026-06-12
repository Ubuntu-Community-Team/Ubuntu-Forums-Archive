---
title: "Some scripts I wrote for tagging videos and/or moving files (with rsync)"
date: 2013-01-27
forum: General Help
---

### Post by HiImTye on 2013-01-27
[SIZE=2]I just finished tweaking/writing some scripts and thought I'd share them. I didn't like the old way I did this sort of thing, so I re-wrote them to work more intelligently. included in this post are:[/SIZE]
 
[LIST]
[*][SIZE=2]Nautilus scripts for:[/SIZE]
[LIST]
[*][SIZE=2]rsync files that are         selected to another folder (such as a pen drive)[/SIZE]
[*][SIZE=2]rsync files that are         selected to another folder (with rename)[/SIZE]
[*][SIZE=2]tag video files that         are selected (using ffmpeg)[/SIZE]
[/LIST]
     
[*][SIZE=2]cleaning the     filenames of (and tagging, using ffmpeg):[/SIZE]
[LIST]
[*][SIZE=2]Movies (assuming you         follow my folder structure, *see below*)[/SIZE]
[*][SIZE=2]TV Shows (assuming         you follow my folder structure, *see below*)[/SIZE]
[/LIST]
     
[*][SIZE=2]video tagging core script[/SIZE]
[/LIST]
 [SIZE=2](note: I have included these scripts in the attachments)[/SIZE]
 


 [SIZE=2]**as per usual, all of my scripts go to ~/Launchers**. if you are unsure what that means, then open up Nautilus (Files), or whatever file manager you use, then when in your home folder, create a new folder and name it Launchers. all of my scripts will go in there. we will make links to the Nautilus scripts later, see below.[/SIZE]
 


 [SIZE=3]Basic Scripts:[/SIZE]
 [COLOR=#006400][SIZE=2]**tagVideosCore.sh**[/SIZE][/COLOR]
 [SIZE=2]*(keep in mind that this is case sensitive, as it is called by my other scripts)*[/SIZE]
 [SIZE=2]**about:**[/SIZE]
 [SIZE=2]this is the script that lets us tag videos. it is much simpler to give it its' own file. we won't need to make any changes to this file.[/SIZE]
 [SIZE=2]**file:**[/SIZE]
 [SIZE=2]```
#!/bin/bash
while IFS=\| read -r f nF Title; do
# skip the info lines
if echo $f | grep ^#; then
 continue
fi
echo tagging video file "$f" >> fout.txt
echo ffmpeg -i "$f" -metadata title="$Title" -acodec copy -vcodec copy -scodec copy "$nF"
ffmpeg -i "$f" -metadata title="$Title" \
 -acodec copy -vcodec copy -scodec copy "$nF"
file_f=$(stat -c %s "$f")
file_nF=$(stat -c %s "$nF")
if [ "$file_nF" -gt "$file_f" ]; then
 echo new file "$nF" larger than old file, deleting old file >> fout.txt
 rm -f "$f"
else
 echo new file "$nF" not larger than old file, skipping >> fout.txt
 echo $nF >> fout.err # add filename to list of failed files
fi
done < <(cat $1)

exit
```[/SIZE]
 


 [COLOR=#006400][SIZE=2]**cleanFilenamesTV.sh**[/SIZE][/COLOR]
 [SIZE=2]**about:**[/SIZE]
 [SIZE=2]this allows us to automagically rename and tag any video files we keep in our *VideosPath* variable.[/SIZE]
 [SIZE=2]**configuration:**[/SIZE]
 [SIZE=2]**you will want to change VideosPath to what ever your base TV folder is**. if your base TV folder is ***~****/Videos/TV* then you will want to change it to read[/SIZE]
 [SIZE=2]```
VideosPath="**$HOME**/Videos/TV"
```make sure you don't delete the quotes, just in case.[/SIZE]
 [SIZE=2]**you will also want to set your editor**. make sure you use the filename for your editor, and not the program name. if you're unsure of the filename, go to the 'Main Menu' program and then find your editors' launcher. select it and click on 'Properties.' the command will be everything before the first space (if there is one, usually it is *filename %U*, or some such thing). for instance, GVIM displays:[/SIZE]
 [SIZE=2]```
gvim -f %F
```[/SIZE]
 [SIZE=2]in which case, the editors' filename is *gvim*.[/SIZE]
 [SIZE=2]the editor pops up when it's done creating a list, to allow you to change the output filename (although you're better off leaving this, and just renaming your folder) and the title. I did it this way because before I would have the script pop up a zenity input window, but you would have to wait for one file to complete before choosing a second name, or else you would end up with a million ffmpeg processes bogging down your CPU. this way, tagVideosCore will iterate the list file one by one, being nice to your CPU (and your patience).[/SIZE]
 [SIZE=2]**lastly, you can change the 'EditorForks' variable if your editor doesn't fork** (that is, detach itself). if you are unsure, just open up a terminal (usually *ctrl+alt+t*) and type in the editors' filename. if once it opens (before it closes), you are returned to a prompt that looks like this:[/SIZE]
 [SIZE=2]```
[ username: ~ ]$
```[/SIZE]
 [SIZE=2]and you can run other commands, you want the variable to be 'yes' so that it stops the script from proceeding before your editor is done.[/SIZE]
 [SIZE=2]if it doesn't fork, you can change it to 'no' (or anything other than 'yes')[/SIZE]
 [SIZE=2]**usage:**[/SIZE]
 [SIZE=2]the script expects your folder structure to follow one of:[/SIZE]
 ```

 [SIZE=2]VideosPath/TV Show (year)/Season #/garbage.Episode##.garbage.ext[/SIZE]
 [SIZE=2]VideosPath/TV Show (year)/Season #/garbage.E##.garbage.ext[/SIZE]
 [SIZE=2]VideosPath/TV Show (year)/Season #/garbage.#x##.garbage.ext[/SIZE]
 [SIZE=2]VideosPath/TV Show (year)/Season #/garbage.###.garbage.ext[/SIZE]
 
```[SIZE=2]
you will need to set your folders this way, or you will need to change the script.
I did include a filter to remove x264/h264 from the filename. you're welcome.
I make a link to this script and place it in my base TV folder. then I can just run it from there in Nautilus. the 'clicking' way to do this is to right click on the script in *~/Launchers*, and choose '*Make Link*.' Nautilus will then create a file '*Link to <filename>*'. move that to your TV folder and rename it to whatever you want. *pro tip*: it doesn't need the .sh
**tagVideosCore performs a check when it's done with a file.** if the new file is the same size or smaller than the original, it will leave the new file, and the original, and write the filename of the new file to *fout.err* - check this file when you are done. just because the file is smaller or the same size doesn't mean that it failed, but it could have, so always double check these files.[/SIZE]
 [SIZE=2]**file:**[/SIZE]
 [SIZE=2]```
#!/bin/bash

VideosPath="/storage/Videos/TV/(unsorted)"
tagVideosCore=$HOME/Launchers/tagVideosCore.sh
Editor="gnome-terminal -x vim" # your favorite editor
EditorForks=yes # put 'yes' if the editor forks its' own process.
               #  if you are unsure, then run a simple test. open a terminal
               #  window and run your editor from there. if it returns to a
               #  regular prompt, meaning you can tell the terminal to run
               #  something else while your program runs, then your program
               #  forks, and you need to put yes here. otherwise, it's safe
               #  to put no.

# create a temporary database of our videos path, to ensure all file names
#  used by 'locate' are current
updatedb -l 0 -o temp.db -U "$VideosPath"
# empty our output files
echo > out.txt # regular output of this script
echo > fout.txt # regular output of the ffmpeg script
echo "# the list of files that failed the ffmpeg script's \
      size check" > fout.err 
echo '# follows the format:' > list.txt
echo '#  old filename|new filename|title' >> list.txt
echo '# edit the new filename and title if you want them to be different' >> list.txt

while read -r f; do
 echo '****************' >> out.txt
 echo  >> out.txt
 echo "$f" >> out.txt
 # rename episodes according to their folder names, and format episode string
 #  as 'S##E##', according to their path and filename
 # remove 'h264' and 'x264' from filenames as they are troublesome and we are
 #  just going to remove them later anyways
 nF=$(echo "$f")
 nF2=$(echo "$nF" | sed 's|[xXhH]264||g')
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
 # strip garbage between episode number and extension,
 #  then make file extensions lowercase
 nF=$(echo $nF | sed 's|\(E[0-9]\{2\}\).*\(\.[a-zA-Z0-9]*\)$|\1\L\2\E|')
 # add the original filename, the new filename, and the title to our list
 echo "$f|$nF|$Title" >> list.txt
 echo  >> out.txt
 echo '****************' >> out.txt
done < <(locate -q -d temp.db *.avi *.mkv *.mp4)
# delete our temporary database
rm -f temp.db

$Editor list.txt
if [ -n "$EditorForks" ]; then
 # halt until user is done editing
 zenity --info --title="Edit List of Files" --text="Hit OK when finished editing the file list."
fi

# start renaming
gnome-terminal -x $tagVideosCore list.txt

# notify the user that we're finished
zenity --info --title="Filename Check Complete" --text="Finished checking filenames."

exit
```[/SIZE]
 


 [COLOR=#006400][SIZE=2]**cleanFilenamesMovies.sh**[/SIZE][/COLOR]
 [SIZE=2]**about:**[/SIZE]
 [SIZE=2]this allows us to automagically rename and tag any video files we keep in our *VideosPath* variable.[/SIZE]
 [SIZE=2]**configuration:**[/SIZE]
 [SIZE=2]the same as the TV one[/SIZE]
 [SIZE=2]**usage:**[/SIZE]
 [SIZE=2]the script expects your folder structure to follow one of:[/SIZE]
 [SIZE=2]```

VideosPath/Movie (year)/garbage.ext
VideosPath/Movie (year) [some info]/garbage.ext
VideosPath/Movie (year)/garbage-cd#.garbage.ext
VideosPath/Movie (year)/garbage-pt#.garbage.ext
[SIZE=2]VideosPath/Series/# - Movie[SIZE=2] (year)/garbage.ext[/SIZE][/SIZE]
VideosPath/Series/# - Movie (year)/garbage-cd#.garbage.ext
VideosPath/Series/# - Movie (year)/garbage-[SIZE=2]pt[/SIZE]#.garbage.ext

```*note: square bracketed info can be in any of those. I just didn't feel like typing out another one for each of them.*
you will need to set your folders this way, or you will need to change the script.
again, I create a link to this and put it in my Movies folder. then I can just run it from there in Nautilus.[/SIZE]
 [SIZE=2]**file:**[/SIZE]
 [SIZE=2]```
#!/bin/bash

VideosPath="/storage/Videos/Movies/(to watch)"
tagVideosCore=$HOME/Launchers/tagVideosCore.sh
Editor="gnome-terminal -x vim" # your favorite editor
EditorForks=yes # put 'yes' if the editor forks its' own process.
               #  if you are unsure, then run a simple test. open a terminal
               #  window and run your editor from there. if it returns to a
               #  regular prompt, meaning you can tell the terminal to run
               #  something else while your program runs, then your program
               #  forks, and you need to put yes here. otherwise, it's safe
               #  to put no.

# create a temporary database of our videos path, to ensure all file names
#  used by 'locate' are current
updatedb -l 0 -o temp.db -U "$VideosPath"
# empty our output files
echo > out.txt # regular output of this script
echo > fout.txt # regular output of the ffmpeg script
echo "# the list of files that failed the ffmpeg script's \
      size check" > fout.err 
echo '# follows the format:' > list.txt
echo '#  old filename|new filename|title' >> list.txt
echo '# edit the new filename and title if you want them to be different' >> list.txt

while read -r f; do
 echo '****************' >> out.txt
 echo  >> out.txt
 echo "$f" >> out.txt
 # rename movies according to their folder structure
 nF=$(echo "$f")
 nF2=$nF
 echo 'checking for multi-file pattern' >> out.txt
 # for 'cd#' type filenames
 if [[ "$nF2" =~ [cC][dD][0-9] ]]; then
  echo matches 'cd#' pattern >> out.txt
  # folders that end with square-bracketed info, i.e.:
  #   /path/to/folder/title (year) [some info]/file-CD1.ext
  if [[ "$nF2" =~ [\)][\ ][[].*[]] ]]; then # full square bracketed expression
                                # so that it doesn't break syntax highlighting
   echo square brackets follow year >> out.txt
   nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\}) \[.*\]\)/.*[cC][dD]\([0-9]\).*\(\.[a-zA-Z0-9]*\)$|\1\2\3/\2-Pt\4\L\5\E|')
  else
   nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\})\)/.*[cC][dD]\([0-9]\).*\(\.[a-zA-Z0-9]*\)$|\1\2\3/\2-Pt\4\L\5\E|')
  fi
 # for 'pt#' type filenames
 elif [[ "$nF2" =~ [pP][tT][0-9] ]]; then
  echo matches 'pt#' pattern >> out.txt
  # square brackets
  if [[ "$nF2" =~ [\)][\ ][[].*[]] ]]; then
   echo square brackets follow year >> out.txt
   nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\}) \[.*\]\)/.*[pP][tT]\([0-9]\).*\(\.[a-zA-Z0-9]*\)$|\1\2\3/\2-Pt\4\L\5\E|')
  else
   nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\})\)/.*[pP][tT]\([0-9]\).*\(\.[a-zA-Z0-9]*\)$|\1\2\3/\2-Pt\4\L\5\E|')
  fi
 # for all others
 else
  echo did not match any multi-file pattern >> out.txt
  # square brackets
  if [[ "$nF2" =~ [\)][\ ][[].*[]] ]]; then
   echo quare brackets follow year >> out.txt
   nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\}) \[.*\]\)/.*\(\.[a-zA-Z0-9]*\)$|\1\2\3/\2\L\4\E|')
  else  
   nF2=$(echo "$nF2" | sed 's|\(.*/\)\(.*\)\( ([0-9]\{4\})\)/.*\(\.[a-zA-Z0-9]*\)$|\1\2\3/\2\L\4\E|')
  fi
 fi
 # make sure we are actually doing work
 if [ "$nF" = "$nF2" ]; then
  echo no work, continuing >> out.txt
  echo >> out.txt
  echo '****************' >> out.txt
  continue
 else
  nF="$nF2"
 fi
 # configure 'title' metadata
 echo renaming as: >> out.txt
 echo "$nF" >> out.txt
 Year=$(echo "$nF" | grep -o '([0-9]\{4\})')
 Title="${nF%.*}"
 Title=$(echo "${Title##*/}" | sed 's|-Pt[0-9]||;s|[0-9] - ||')
 Title=$(echo $Title $Year)
 # add the original filename, the new filename, and the title to our list
 echo "$f|$nF|$Title" >> list.txt
 echo  >> out.txt
 echo '****************' >> out.txt
done < <(locate -q -d temp.db *.avi *.mkv *.mp4)
# delete our temporary database
rm -f temp.db

$Editor list.txt
if [ -n "$EditorForks" ]; then
 # halt until user is done editing
 zenity --info --title="Edit List of Files" --text="Hit OK when finished editing the file list."
fi

# start renaming
gnome-terminal -x $tagVideosCore list.txt

# notify the user that we're finished
zenity --info --title="Filename Check Complete" --text="Finished checking filenames.\nffmpeg may still be doing work."

exit
```[/SIZE]
 


 [SIZE=3]Nautilus Scripts[/SIZE]
 [SIZE=2]put these in ~/Launchers and then make links to them. place the links in '~/.gnome2/nautilus-scripts' for pre-12.10 versions of Ubuntu, and in '~/.local/share/nautilus/scripts' for 12.10 and higher versions. rename the links to whatever you want them to say in the Nautilus menu (in other words, don't leave the .sh on them, or they will have the .sh in the menu)[/SIZE]
 


 [COLOR=#006400][SIZE=2]**nautilus-rsync (no rename).sh**[/SIZE][/COLOR]
 [SIZE=2]**about:**[/SIZE]
 [SIZE=2]this script pops up a zenity folder selection window, then copies the files that you have selected in Nautilus to the folder you selected in the zenity window. it copies using rsync in its' own Gnome-Terminal window.[/SIZE]
 [SIZE=2]**configuration:**[/SIZE]
 [SIZE=2]**you might want to change the 'defaultfolder' variable.** it is set to the folder 'storage' in the default folder that pendrives are mounted into in 12.10. this is different for versions before 12.10, so if you are using one of those versions, remove $USER/ from this path. you will obviously want to change the actual folder name to that of the pen drive you use the most, as well.[/SIZE]
 [SIZE=2]**usage:**[/SIZE]
 [SIZE=2]just right click once you have a file or several files selected. choose *scripts>scriptname*, where *scriptname* is whatever you called the link.[/SIZE]
 [SIZE=2]**file:**[/SIZE]
 [SIZE=2]```
#!/bin/bash

defaultfolder=/media/$USER/storage/
tmpfolder=/tmp/rsync-$USER

F=$(zenity --file-selection --directory --text="select destination" --filename=$defaultfolder)
mkdir "$tmpfolder"
while read -r f; do
ln -s "$f" "$tmpfolder"
done < <(echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | grep [\da-zA-Z])
gnome-terminal -x rsync -PL "$tmpfolder"/* "$F"
rm -Rf "$tmpfolder"
exit
```[/SIZE]
 


 [COLOR=#006400][SIZE=2]**nautilus-rsync (rename).sh**[/SIZE][/COLOR]
 [SIZE=2]**about:**[/SIZE]
 [SIZE=2]the same as the version that doesn't rename, except like the tagging scripts, it opens up an editor afterwards to let you change the filenames.[/SIZE]
 [SIZE=2]**configuration:**[/SIZE]
 [SIZE=2]the same as the tagging scripts, and the non-renaming script.[/SIZE]
 [SIZE=2]**usage:**[/SIZE]
 [SIZE=2]select files, right click, *scripts>scriptname*, editor opens up, change filenames, save the file, close, viola.[/SIZE]
 [SIZE=2]**file:**[/SIZE]
 [SIZE=2]```
#!/bin/bash

defaultfolder=/media/$USER/storage/
tmpfolder=/tmp/rsync-$USER
Editor="gnome-terminal -x vim" # your favorite editor
EditorForks=yes # put 'yes' if the editor forks its' own process.
               #  if you are unsure, then run a simple test. open a terminal
               #  window and run your editor from there. if it returns to a
               #  regular prompt, meaning you can tell the terminal to run
               #  something else while your program runs, then your program
               #  forks, and you need to put yes here. otherwise, it's safe
               #  to put no.
# clear our list
echo '# follows the format:' > list.txt
echo '#  old filename|new filename' >> list.txt
echo '# edit the new filename and title if you want them to be different' >> list.txt

F=$(zenity --file-selection --directory --text="select destination" --filename=$defaultfolder)
mkdir $tmpfolder
while read -r f; do
# strip the folder from the new filename
nF=$(echo "$f" | sed 's|.*/\(.*\)$|\1|')
# add it to our list
echo "$f|$nF" >> list.txt
done < <(echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | grep [\da-zA-Z])

$Editor list.txt
if [ -n "$EditorForks" ]; then
 # halt until user is done editing
 zenity --info --title="Edit List of Files" --text="Hit OK when finished editing the file list."
fi

# make links to simplify the rsync line
while IFS=\| read f nF; do
# skip the info lines
if echo $f | grep ^#; then
 continue
fi
ln -s "$f" "$tmpfolder/$nF"
done < <(cat list.txt)

# perform the rsync
gnome-terminal -x rsync -PL "$tmpfolder"/* "$F"
rm -Rf "$tmpfolder"
exit
```[/SIZE]
 


 [COLOR=#006400][SIZE=2]**nautilus-tag videos.sh**[/SIZE][/COLOR]
 [SIZE=2]**about:**[/SIZE]
 [SIZE=2]lets you manually tag video files.[/SIZE]
 [SIZE=2]**configuration:**[/SIZE]
 [SIZE=2]the same as the other tagging scripts.[/SIZE]
 [SIZE=2]**usage:**[/SIZE]
 [SIZE=2]select files in Nautilus, right click, *scripts>scriptname*, editor opens up, check filenames and titles, save file, close editor, viola.[/SIZE]
 [SIZE=2]**file:**[/SIZE]
 [SIZE=2]```
#!/bin/bash

tagVideosCore=$HOME/Launchers/tagVideosCore.sh
Editor="gnome-terminal -x vim" # your favorite editor
EditorForks=yes # put 'yes' if the editor forks its' own process.
               #  if you are unsure, then run a simple test. open a terminal
               #  window and run your editor from there. if it returns to a
               #  regular prompt, meaning you can tell the terminal to run
               #  something else while your program runs, then your program
               #  forks, and you need to put yes here. otherwise, it's safe
               #  to put no.

# empty our output files
echo > fout.txt # regular output of the ffmpeg script
echo "# the list of files that failed the ffmpeg script's \
      size check" > fout.err 
echo '# follows the format:' > list.txt
echo '#  old filename|new filename|title' >> list.txt
echo '# edit the new filename and title if you want them to be different' >> list.txt

while read -r f; do
 # the file path of our hidden temporary file.
 nF=${f%/*}/.${f##*/}
 # create title suggestion for this file.
 # strip the file extension and folder path
 Title=${f%.*}; Title=${Title##*/}
 # auto populate 'Show Title S##E##: Episode Title' for filenames using that
  # structure. the episode title will be missing if it is not present in the file
  # name. also, there is no filtering of either the show title or the episode title
  # so that will need to be done in advance.
 if [[ "$Title" =~ [sS][0-9]{1,2}[eE][0-9]{2} ]]; then
 Title=$(echo "$Title" | sed 's|\(.*\)[ .]\([sS][0-9]\{2\}[eE][0-9]\{2\}\)|\1 \U\2: |')
  # check if there is an episode name following the episode number.
  if [[ ! "$Title" =~ [eE][0-9]{2}$ ]]; then
   # if there is, filter out a separating '.' if one exists.
   Title=$(echo "$Title" | sed 's|\([eE][0-9]\{2\}: \)\.|\1|')
  fi
 fi
 # add the original filename, the new filename, and the title to our list
 echo "$f|$nF|$Title" >> list.txt
done < <(echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | grep -iE '.avi$|.mp4$|.mkv$' | sed 's|%20| |g')

$Editor list.txt
if [ -n "$EditorForks" ]; then
 # halt until user is done editing
 zenity --info --title="Edit List of Files" --text="Hit OK when finished editing the file list."
fi

# start renaming
gnome-terminal -x $tagVideosCore list.txt

# notify the user that we're finished
zenity --info --title="Rename Script Complete" --text="Rename Script Complete.\nffmpeg may still be doing work."

# if old file doesn't exist (because the ffmpeg script deleted it), then
#  rename the new file to the old filename
while IFS=\| read -r f nF Title; do
# skip the info lines
if echo $f | grep ^#; then
 continue
fi
 mv -n "$nF" "$f"
done < <(cat list.txt)

exit
```

[SIZE=2]edit: fixed th[SIZE=2]e location for 12.10+ [SIZE=2]nautilus scripts[/SIZE][/SIZE][/SIZE]
[/SIZE]

---

