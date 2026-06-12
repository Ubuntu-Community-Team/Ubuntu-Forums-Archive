---
title: "The Powerful Command Line?"
date: 2007-03-25
forum: General Help
---

### Post by martinrandau on 2007-03-25
Throughout my music folder I have ogg files that I want to convert to wav. I can do this with audioconverter, but that means I have to find each file that I want to convert. Since I have 100's of music folders and I don't know where the ogg files are, this will be very tedious.

My question is, provided that I know the command for converting from ogg to wav, is there a command for doing this procedure, ie finding the ogg files and the issuing the convert command? Maybe someone could write a little program for me?

Thanks!

---

### Post by kidders on 2007-03-25
Hi there,

Something like **find /where/to/start -iname "*.ogg" -exec ogg2wav {} \;** should do the trick, where "/where/to/start" is the search path to start at, and "ogg2wav" is the command you use to perform the conversion.

---

### Post by aidanr on 2007-03-25
[http://www.tectonic.co.za/view.php?id=1322](http://www.tectonic.co.za/view.php?id=1322)
i'm pretty sure thats not recursive though, i haven't played around with it and i'm not going to but that might get you started

the command to convert ogg to wav is
```
ogg123 -d wav -f test.wav test.ogg
```

---

### Post by flankker on 2007-03-25
to select all the .ogg files in a folder to apply a command to, u can do this:

the_command  *.ogg

the "*.ogg" will apply the command to all the .ogg files in that folder. hope that helps :)

---

### Post by xadder on 2007-03-25
The syntax of find is rather complex, but it should be able to do the job you want. For example, to do a word count (wc)  on your ogg files you could do:

find . -name "*.ogg" -exec wc '{}' \;

The {} here represents the resulting filename from find, and the ;
marks the end of the exec command. Both have some escaping done,
hence the '{}' and \;.  The find command is here starting to work
from the current folder (.), but you can specify wherever you want.
find digs down through your subdirectories from wherever you
start it.

You should test a few times with safe commands until you get the
hang of find. Be careful if your file names have spaces also.

If you want a cruder variant, you could always just do

find . -name "*.ogg" > LIST.OGG

and then edit LIST.OGG to put in the commands you want. Not so elegant, but
it maybe helps to see what you are doing. (I used OGG here  to avoid LIST.ogg
being written into LIST.ogg).

---

### Post by stokedfish on 2007-03-25
[http://kde-apps.org/content/show.php/soundKonverter?content=29024](http://kde-apps.org/content/show.php/soundKonverter?content=29024)  ;)

---

### Post by lloyd_b on 2007-03-25
A shell script, fed from the "find" command, will do the trick:

```
#!/bin/bash
for OGGFILE in `find . -name *.ogg -print`; do
     BASENAME=`echo "$OGGFILE" | cut -d '.' -f2`
     WAVNAME="$BASENAME".wav
     ogg123 -d wav -f "$WAVNAME" "$OGGFILE"
done
```

An explanation:  The "find" command is executed, and the resulting list is looped through one item at a time.  The base name (the full path, minus the ".ogg") is extracted.  ".wav" is concatenated onto the base name to produce the output file name.  Then the conversion command is called.

Note: Because of the way the "cut" command operates, there will be errors if any of the directory names contain a period (".").

Lloyd B.

---

### Post by xadder on 2007-03-25
Just a small suggestion. The cut in the above script could be avoided with some extra lines, e.g. instead of BASENAME = ..., use:

DIR= `dirname $OGGFILE` 
BASE=`basename $OGGFILE ogg`
WAVNAME =$DIR"/$BASE"wav 

this should work even with filenames such as a.good.record.ogg

---

### Post by lloyd_b on 2007-03-25
> **xadder said:**
> Just a small suggestion. The cut in the above script could be avoided with some extra lines, e.g. instead of BASENAME = ..., use:

DIR= `dirname $OGGFILE` 
BASE=`basename $OGGFILE ogg`
WAVNAME =$DIR"/$BASE"wav 

this should work even with filenames such as a.good.record.ogg

dirname/basename have their own problem - they don't work correctly if there's a <SPACE> character in a directory or filename.

Six of one, half a dozen of the other.

(Edit - open mouth, insert foot.  This problem is a result of the "for" construct using space characters as separators, not a problem with dirname/basename).
Lloyd B.

---

### Post by martinrandau on 2007-03-25
Thanks for the replies. I tried the script but there is a problems with filenames with spaces, ie "Bob Dylan". I get this: 

```
martin@yeah:~/music$ ./oggconvert

Audio Device:   WAV file output

Cannot open ./Bob.


Audio Device:   WAV file output

Cannot open Dylan/Time.


Audio Device:   WAV file output

Cannot open Out.


Audio Device:   WAV file output

Cannot open of.


Audio Device:   WAV file output

Cannot open Mind/01.


Audio Device:   WAV file output
```

Then it stops there for a long time so I cannot deduce whether it's acutally converting the songs, or if it has stopped.

---

### Post by lloyd_b on 2007-03-25
> Thanks for the replies. I tried the script but there is a problems with filenames with spaces, ie "Bob Dylan". I get this: 

Oops.  The problem is that the "for ..." construct sees the space characters as item separators.  Okay, we can fix that...
```
#!/bin/bash
IFS='|'
for OGGFILE in `find . -name *.ogg -printf "%p|"`; do
     DIRNAME=`dirname "$OGGFILE"`
     BASENAME=`basename "$OGGFILE" .ogg`
     WAVNAME="$DIRNAME/$BASENAME.wav"
     echo "Converting <$OGGFILE> to <$WAVNAME>"
     ogg123 -d wav -f "$WAVNAME" "$OGGFILE"
done
```

What I did with this is set the shell variable IFS (the field separator) to "|", which I sincerely hope you don't have in any filenames.  Then I modified the find command to print this character between files, rather than the standard newline.

I also changed that "cut" trick to use the "dirname"/"basename" technique - it turns out that the problem I saw with those was actually from the "find" command.  With the "find" working correctly, dirname/basename *is* the better way.

Finally, I added an echo command so that you can see exactly what filenames it's working with - it should help if any further debugging is required.

I don't have any .ogg files laying around to test against, but I set up some dummy files, and ran the script with the "ogg123..." line commented out - it seems to be working correctly, even with spaces in file and directory names.

Lloyd B.

---

### Post by martinrandau on 2007-03-25
Thank you very much! Your script works very well.

However, the tags are not preserved in the songs. I realize this have nothing to do with the script. But without the tags, the files are pretty worthless as I need them to transfer to the ipod. Any ideas for this?

Thanks again!

---

### Post by lloyd_b on 2007-03-25
> However, the tags are not preserved in the songs. I realize this have nothing to do with the script. But without the tags, the files are pretty worthless as I need them to transfer to the ipod. Any ideas for this?

I'm at a loss on this one - I wasn't even aware the .wav files supported tags (or are you converting to another format that does?).

The tags can (I think) be extracted via the "ogginfo" command.  Beyond that, I'm clueless.

Lloyd B.

---

### Post by stokedfish on 2007-03-27
Why don't you just use [http://kde-apps.org/content/show.php/soundKonverter?content=29024](http://kde-apps.org/content/show.php/soundKonverter?content=29024) ?

Some love to do things the hard way...tzz, tzz.

---

### Post by martinrandau on 2007-03-27
I just realized that soundKonvertor can convert to mp3 recursively so all my problems are solved now.

Thanks Lloyd B and everyone else for taking their time to reply.

---

