---
title: "Bash script help needed"
date: 2013-07-15
forum: General Help
---

### Post by prem1er on 2013-07-15
I've written a bash script to help me encode some video files in order to standardize my video library. I'm using both mediainfo and handbrake cli in my script in order to achieve this. I'm currently having one issue that given my limited work with bash is causing me some problems. I have two basic paths for the program to take based on the input file.

1. Is it a regular file, i.e. /path/to/file/blah.avi

2. Is it a directory with files in it, i.e. /path/to/season/Futurama/s1e1.avi, /path/to/season/Futurama/s1e2.avi

The issue I am having is with the directory case. Below is my code to kick off the process based on file input. The script correctly identifies whether the input file is a regular file or a directory, but it only runs the rest of the script one time for one .avi file that it finds. The script should be looking for ALL avi files in the directory and running the script for each one. I have run the 'find' command outside of my script and it works properly, so I'm not sure why it isn't looping properly when it is in a script. Let me know if you see something incorrect. TIA.

This is the part of the script causing the issue. If you need the rest let me know, but everything else seems to be working.

```

....

main () {
  inputFile="$input"

  if [[ -d "$inputFile" ]]; then
    CUR_TIME=`date +"%m-%d-%y %T"`
    echo "$CUR_TIME - Running in Directory Mode .." >> $LOG_FILE
    echo "$CUR_TIME - Directory location - $inputFile .." >> $LOG_FILE

    find "$inputFile" -depth -iname "*.mkv" -o -iname "*.avi" -o -iname "*.mp4" | while read temp

    do
      curl -s -d "apikey=$NMA_KEY" -d "&application=Video Encode" -d "&event=Started - $temp" -d "&description=Directory mode" https://www.notifymyandroid.com/publicapi/notify
      CUR_TIME=`date +"%m-%d-%y %T"`
      echo "$CUR_TIME - Input file path $temp .." >> $LOG_FILE 
      runHandbrake $temp
    done
  else
    CUR_TIME=`date +"%m-%d-%y %T"`
    echo "$CUR_TIME - Running in File Mode .." >> $LOG_FILE
    curl -s -d "apikey=$NMA_KEY" -d "&application=Video Encode" -d "&event=Started - $inputFile" -d "&description=File mode" https://www.notifymyandroid.com/publicapi/notify
    echo "$CUR_TIME - Input file path $inputFile .." >> $LOG_FILE
    runHandbrake $inputFile
  fi
}

main
if [[ "$?" -ne 0 ]]; then
  temp="$input"

  fileName=$(basename "$temp") 
  extension="${fileName##*.}"
  fileName="${fileName%.*}"

  curl -s -d "apikey=$NMA_KEY" -d "&application=Video Encode" -d "&event=Error - $fileName.mkv" -d "&description=$CUR_TIME - Error Code $?" https://www.notifymyandroid.com/publicapi/notify
else 
  temp="$input"

  fileName=$(basename "$temp") 
  extension="${fileName##*.}"
  fileName="${fileName%.*}"

  curl -s -d "apikey=$NMA_KEY" -d "&application=Video Encode" -d "&event=Completed - $fileName.mkv" -d "&description=" https://www.notifymyandroid.com/publicapi/notify
fi

```

---

### Post by prodigy_ on 2013-07-15
> **prem1er said:**
> it only runs the rest of the script one time for one .avi file that it finds
Naturally I'd assume that the **else ... fi** is getting executed for some reason. Add **set -x** (somewhere before the problematic part) to get trace log. You'll see what evaluates to what then.

The script itself looks OK but there are some minor issues. **runHandbrake $temp** can potentially break because $temp isn't protected with double quotes. And instead of **find ... | while read temp** you should use something like
```
find ... -print0 | while read -r -d $'\0' temp; do
  ...
done
```

---

### Post by prem1er on 2013-07-15
> **prodigy_ said:**
> Naturally I'd assume that the **else ... fi** is getting executed for some reason. Add **set -x** (somewhere before the problematic part) to get trace log. You'll see what evaluates to what then.


Thanks for the reply. Are you referring to the else ... if that is used here?

```
if [[ -d "$inputFile" ]]; then
...
else
...
fi

```

---

### Post by prodigy_ on 2013-07-15
Yeah. If you meant the part that goes after you call **main**, then of course it only gets executed once - you don't have any loop there.

---

### Post by prem1er on 2013-07-15
Right. So, based on my logs I can see that it is correctly identifying the directory and not going into the 'else' part of that switch. The problem looks to be in the find | while loop. Could you explain your edit a bit more and I will test your changes out. Also, I have added the "" around the parameter that you had suggested.

---

### Post by Vaphell on 2013-07-15
> **prodigy_ said:**
> 
```
find ... -print0 | while read -r -d $'\0' temp; do
  ...
done
```

```
while read -r -d $'\0' temp; do
  ...
done < <( find ... -print0 )
```
would be another way to do it, imho more readable because *while read* is not crammed together with a potentially very long command in a single line



Backticks `` are considered deprecated and $() should be used instead (CUR_TIME=`...`).

basename can be easily achieved without spawning external process with ${fullpath##*/}

All caps variable names seen frequently in scripts are a bad idea, you risk overriding some env variable (env variables are all caps by convention) and then trying to figure out why the script doesn't work. I've seen a guy use PATH and wonder why grep, ls and dozen of other commands he tried to use returned 'command not found'. At least 1 lowercase char and you are golden.

always quote variables, you have nothing to gain from leaving them dangling in the open except bugs caused by whitespace.

---

### Post by prem1er on 2013-07-15
Thanks everyone for the suggestions. I have changed the script and will be able to test later tonight and report back.

---

### Post by prem1er on 2013-07-16
I have made most of the suggestions that were listed here and I'm still having issues, so I'm assuming that the issue is further on in my script. I'm not going to post the whole thing, but will hopefully post the part where I think the issue is happening. From the 'main' method I'm calling another function that inspects the media file using mediainfo and basically creates a list of parameters to use with Handbrake cli. These parameters are all being created properly as I can see from the logs AND also Handbrake cli is being called correctly as it is logging and generating the correct output file. The problem is that after the Handbrake command runs (in the case of a directory being added), the program never returns to the calling loop (pasted below, with mofications based on the responses). 

```

main() {
....

    find "$inputFile" -depth -iname "*.mkv" -o -iname "*.avi" -o -iname "*.mp4" -print0 | while read -r -d $'\0' temp; do
      curl -s -d "apikey=$NMA_KEY" -d "&application=Video Encode" -d "&event=Started - $temp" -d "&description=Directory mode" https://www.notifymyandroid.com/publicapi/notify
      CUR_TIME=$(date +"%m-%d-%y %T")
      echo "$CUR_TIME - Input file path $temp .." >> $LOG_FILE 
      runHandbrake "$temp"
      
      if [[ "$?" -ne 0 ]]; then
	path="${temp##*/}"
	fileName="${path%%.*}"

	curl -s -d "apikey=$NMA_KEY" -d "&application=Video Encode" -d "&event=Error - $fileName.mkv" -d "&description=Error Code $?" https://www.notifymyandroid.com/publicapi/notify
      else 
        path="${temp##*/}"
        fileName="${path%%.*}"

        curl -s -d "apikey=$NMA_KEY" -d "&application=Video Encode" -d "&event=Completed - $fileName.mkv" -d "&description=" https://www.notifymyandroid.com/publicapi/notify
      fi
    done
....
}

```

And here's is the snippet of 'runHandbrake' function that is being called, which I believe is causing the issue. The question is after I call Handbrake at the end of this function why isn't it the code continuing to loop through the rest of the .mkv, .avi or .mp4 files in the directory? TIA.

```

runHandbrake() {
....

  CUR_TIME=$(date +"%m-%d-%y %T")
  echo "$CUR_TIME - Handbrake options .." >> $LOG_FILE
  echo "$CUR_TIME - -v -i $inputFile -o $OUTPUT_FILE -f $OUTPUT_FORMAT -e $VIDEO_FORMAT -r $FRAMERATE --cfr -q $QUALITY $AUDIO_TRACKS $AUDIO_CODEC $AUDIO_BIT $AUDIO_MIX --decomb --strict-anamorphic --display-width $WIDTH --keep-display-aspect --crop --loose-crop $SUB_OPTIONS" &>> $LOG_FILE
  
  HandBrakeCLI -v -i "$inputFile" -o "$OUTPUT_FILE" -f "$OUTPUT_FORMAT" -e "$VIDEO_FORMAT" -r "$FRAMERATE" --cfr -q "$QUALITY" $AUDIO_TRACKS $AUDIO_CODEC $AUDIO_BIT $AUDIO_MIX --decomb --strict-anamorphic --display-width "$WIDTH" --keep-display-aspect --crop --loose-crop "$SUB_OPTIONS" &>> $LOG_FILE
  if [[ "$?" -ne 0 ]]; then
    echo "$CUR_TIME - Error executing Handbrake. Error Code $? .." >> $LOG_FILE
    exit "$?"
  fi
}
```

---

### Post by erind on 2013-07-16
> **prem1er said:**
> [...]
 These parameters are all being created properly as I can see from the logs AND also Handbrake cli is being called correctly as it is logging and generating the correct output file. The problem is that after the Handbrake command runs (in the case of a directory being added), the program never returns to the calling loop (pasted below, with mofications based on the responses). 

[...]

And here's is the snippet of 'runHandbrake' function that is being called, which I believe is causing the issue. **The question is after I call Handbrake at the end of this function why isn't it the code continuing to loop through the rest of the .mkv, .avi or .mp4 files in the directory?** TIA.

[...]

What's happening here is that in a *while* loop, *HandBrakeCLI* is reading from stdin, _consuming  all the arguments at once_. Some other commands such as *ffmpeg, ssh+command* ... in a *while* loop, display the same problematic behavior. One common trick to prevent this, is to redirect HandBrakeCLI's stdin to */dev/null*:

```
HandBrakeCLI -v -i "$inputFile" -o [ ... ] --loose-crop "$SUB_OPTIONS" [COLOR=#0000ff]< /dev/null[/COLOR] &>> $Log_file

```
Check this thread for a similar case and an explanation:
[http://ubuntuforums.org/showthread.php?t=1835021](http://ubuntuforums.org/showthread.php?t=1835021)

--
As a side note and adding to the other posters' advices, you need to group the test options (-iname) in *find*'s statement, to have the correct output:
```
find "$inputFile" -depth[COLOR=#0000ff] \([/COLOR] -iname "*.mkv" -o -iname "*.avi" -o -iname "*.mp4" [COLOR=#0000ff]\) [/COLOR]-print0
```

---

### Post by prem1er on 2013-07-18
Thanks everyone for the help it is working like a charm.

---

