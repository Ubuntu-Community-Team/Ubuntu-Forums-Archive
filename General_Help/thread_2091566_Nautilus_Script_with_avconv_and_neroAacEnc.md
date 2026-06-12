---
title: "Nautilus Script with avconv and neroAacEnc"
date: 2012-12-05
forum: General Help
---

### Post by evilsoup on 2012-12-05
I'm trying to write up a nautilus script to convert files to an m4a, from within nautilus. I know there are programs that do this already, I'm mostly doing it out of interest, but I've run into a brick wall. Why doesn't this work?

```

#!/bin/bash
for f in "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"; do
filename=$(basename "$f")
zenity --notification --text="Converting $filename"
avconv -i "$f" -f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of "${f%.*}.m4a"
done
exit 0

```I've put the script in the correct directory, and nautilus sees it; and the zenity notification pops up correctly. I've used the avconv|neroAacEnc combination exactly like that on the commandline, within a similar *for* loop, and it works perfectly there... but with this, no file is created. What am I doing wrong?

---

### Post by Isamu715 on 2012-12-05
When invoking a script Nautlus sets the workig directory to the one your selected file is in. Try replacing %f with %filename in the *avconv* command. You can also use output redirection to write command output to a file and see the error message, which should make finding out the reason easier.

---

### Post by evilsoup on 2012-12-13
Well I found a way to make it work

```

#!/bin/bash
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | while read f; do
avconv -i "$f" -f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of "${f%.*}.m4a"
notify-send "Finished converting $f to AAC M4A"
done
exit 0

```

I'm aware that the construction of that first line is really ugly (ugh unnecessary pipes)... but I can't quite get my head around while loops at the moment, and I just copied it from a script somewhere on the internet. If anyone can improve upon it, I'd appreciate it.

---

### Post by andrew.46 on 2012-12-13
Will you extend your script to extract the meta tags from the original files and place them in the final file with AtomicParsley or neroAacTag?

---

### Post by evilsoup on 2012-12-14
I might as well, it shouldn't be much extra effort.

---

### Post by evilsoup on 2012-12-14
> **evilsoup said:**
> I might as well, it shouldn't be much extra effort.

And half an hour fiddling with it gets me this:
```

#!/bin/bash

#### Requires: avconv, neroAacEnc, NeroAacTag

echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | while read f; do
    filename=$(basename "$f")
    if [ "$filename" != "" ]; then
        notify-send "Beginning conversion of $filename to AAC M4A"
    fi

#### First, grab some metadata 
    metadata=$(avprobe "$f" 2>&1)
    title=$(echo "$metadata" | grep -i title | sed 's/.*: //')
    artist=$(echo "$metadata" | grep -i artist .tempfile | sed 's/.*: //')
    track=$(echo "$metadata" | grep -i track | sed 's/.*: //')
    album=$(echo "$metadata" | grep -i album | sed 's/.*: //')
    if [ "$artist" = "" ]; then
        artist=$(echo "$metadata" | grep -i author | sed 's/.*: //')
    fi

#### The actual conversion to AAC M4A
    avconv -i "$f" -f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of "${f%.*}.m4a"

#### Writing the metadata to the new M4A
    neroAacTag "${f%.*}.m4a" -meta:title="$title" -meta:artist="$artist" -meta:track="$track" -meta:album="$album"

    if [ "$filename" != "" ]; then
        notify-send "Finished converting $filename to AAC M4A"
    else
        notify-send "All selected files converted to AAC M4A"
    fi
done
rm .tempfile
exit 0

```Save the above as 'convert to m4a' in ~/.gnome2/nautilus-scripts, mark it as executable, and it should appear in your right-click context menu, under scripts. It will only work on files (using it on a directory will just give out a few misleading messages), but it can do multiple files.

For it to work, you'll need avconv (in the repos) and the neroAAC stuff from [here]("http://www.nero.com/eng/company/about-nero/nero-aac-codec.php"); you'll need to extract the linux executables and put them in your $PATH (either ~/bin or /usr/bin, depending on whether you want it just for one user, or for all). From the command-line:

```

wget http://ftp6.nero.com/tools/NeroAACCodec-1.5.1.zip
unzip NeroAACCodec-1.5.1.zip "linux/neroAacEnc" "linux/neroAacTag"
chmod u+x linux/neroAac*
mv linux/neroAac* ~/bin/
rmdir linux

```DISCLAIMER: NeroAAC is given away for private, non-commercial use. If you are planning on making money using it, contact Nero and see if you can come to a deal with them.

If

---

