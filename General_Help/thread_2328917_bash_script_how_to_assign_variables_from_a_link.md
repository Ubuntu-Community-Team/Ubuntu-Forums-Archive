---
title: "bash script how to assign variables from a link"
date: 2016-06-25
forum: General Help
---

### Post by YaPaY on 2016-06-25
I have a web link for example 127.0.0.1/list.m3u

list.m3u
```
#EXTINF:-1,Sat 1
http://127.0.0.1:8000/live/rrr/rrr/152.ts
#EXTINF:-1,Pro Sieben
http://127.0.0.1:8000/live/rrr/rr/153.ts

```

Would be possible  from bash script get the link online and with a loop command assign to variables?  according to this example:
Sat 1=152
Pro Sieben=153
RTL=151

thanks a lot

---

### Post by TheFu on 2016-06-26
Well, sorta.  Bash is a glue language used to call other tools. Tools like sed, cut, awk.  It does have looping and other control structures, so you can use it for something like this.  Looks like about 5 lines in perl (my tool of choice), but we'd have to make some strict assumptions about the data file.

Do you just want simple href links?  That isn't hard.

For bash, here's a guide [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) that has lots and lots of examples. There are beginning guides too. "beginning bash" is what I'd use. If you prefer dead trees - I can recommend the "Unix Power Tools" book.

If you wait, someone else might create a script for you. I'm here to help you learn how to do it yourself.  My pseudo-code is:

# loop over the lines in the file (might be easiest to get these from stdin, not a file)
# look for EXTINF lines - use sed/cut to remove everything before the comma
# Look for http lines - save the URL.
# Build the <href> and output it (echo) to be redirected to another file

Might have a template for the stuff above and below it in the html file.

If the playlist is static, it would be easy to just manually do this; perhaps an edit macro. If it changes hourly, the script makes sense. If it changes minute to minute, then a webapp is what I'd create.  There are lots of issues not shown that are likely. For example, if the playlist is created by someone else, they are likely to make it with convoluted javascript. This is happening more and more. What if the playlist is a multi-part playlist pointing to other playlists?  Does the link need to do anything special for that to work?

I'd planned to post some example bash with loops and sed, but didn't find anything easy.  Did find a Vprj to EDL script that uses grep and sed to get the work done. Might show some techniques. Note how it uses a temporary file?
```
#!/bin/bash

# Full paths to some tools
SED=/bin/sed
EGREP=/bin/egrep
RM=/bin/rm

# make output filename from input filename
ROOT=${1/%.Vprj/}

# Find all the _interesting lines_ in the input file with grep 
$EGREP CutStart "$1" > "$1.T"

# Remove all but the beginning and ending timestamps for the cut areas.
$SED -e 's/^.*CutStart="//g' \
    -e 's/" Elapsed.*$//g' \
    -e 's#" CutEnd="# #g' \
    -e 's#;#.#g' \
    -e 's/$/ 3/g' < "$1.T" > "$ROOT.edl"

# clean up temporary file
$RM "$1.T"

```

Input is a file assumed to be in Vprj format.  Output is edl format.  Just the extension is changed in the filename.   File.Vprj --> File.edl. EDL files are used by media players to skip unwanted parts of a video file, usually commercials. A tool like comskip can create many different formats, but sometimes those cut points are slightly off and need manual correction. Vprj is the format for a GUI tool, but EDL is the required format for playback programs, hence why this little script was needed. You can do something similar. Converting 1 input file to a different output file isn't too hard.

The hardest part of this is using the [regular expressions]("https://en.wikipedia.org/wiki/Regular_expression") - regex.  It is a language onto itself used by most of these text parsing tools. There are tutors for it.

How to loop over lines in a file: [https://stackoverflow.com/questions/1521462/looping-through-the-content-of-a-file-in-bash](https://stackoverflow.com/questions/1521462/looping-through-the-content-of-a-file-in-bash)

---

### Post by YaPaY on 2016-06-27
Thank TheFu,

it seems a bit hard for me.

---

### Post by btindie on 2016-06-27
Not entirely sure what it is you're trying to do. You can't however create variable names such as 'Pro Sieben'.

The below bash script will read the m3u file and extract the data as required.
```
#!/bin/bash

FILENAME=list.m3u


while read LINE; do


  if [[ $LINE =~ ^#EXTINF ]]; then
    echo -n "${LINE##*,} "
    read URL
    FILE=${URL##*/}
    echo "${FILE%.*}"
  fi


done < <(grep -v '^$' $FILENAME)
```

Depending on what it is you want to do you could store the data into an array.

You could even use curl to directly fetch the m3u file, e.g.
```
done < <(curl -s http://127.0.0.1/list.m3u | grep -v '^$')
```

---

### Post by YaPaY on 2016-06-27
@btindie 

many thanks. It works great.

---

