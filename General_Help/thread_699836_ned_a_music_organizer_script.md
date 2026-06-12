---
title: "ned a music organizer script"
date: 2008-02-17
forum: General Help
---

### Post by kaiju on 2008-02-17
i'd like to organize my music library. while i'm at it, it would be great to also learn a bit about scripting, so:

- my script needs to be able to read id3 tags and rename files/directories according to them
- i need the same format for all filenames in my music directory: 'artists' - 'year' - 'album'/'track number' - 'title'
- it would be useful if i could automatically replace certain characters while renaming (e.g. 'é' to 'e' or '&#351;' to 's')

any ideas or examples to how i could achieve this or what commands i could build upon or where i should look (instead of posting this here :P) are very welcome.

---

### Post by lloyd_b on 2008-02-18
> **kaiju said:**
> i'd like to organize my music library. while i'm at it, it would be great to also learn a bit about scripting, so:

- my script needs to be able to read id3 tags and rename files/directories according to them
- i need the same format for all filenames in my music directory: 'artists' - 'year' - 'album'/'track number' - 'title'
- it would be useful if i could automatically replace certain characters while renaming (e.g. 'é' to 'e' or '&#351;' to 's')

any ideas or examples to how i could achieve this or what commands i could build upon or where i should look (instead of posting this here :P) are very welcome.

Your third requirement is the easiest - "man tr" in a terminal window.  "tr" stands for "translate".

Install the package "mp3info", and then "man mp3info" in a terminal window.  Using it's "-p [format]" option, you can easily create the new filename from the ID3 info.

Actually creating the directory structure to go with it is a bit trickier, but not impossible.  Use the "dirname" command on the results of the "mp3info" command, then in a script you can use "test -d ..." to determine if such a directory already exists, and if not do a "mkdir ..." command.

One caution - whenever passing a filename that may contain spaces to a command, ALWAYS enclose it in quotation marks.  Embedded spaces in filenames can cause many commands to do weird things.

Here's a link to an [older thread]("http://ubuntuforums.org/showthread.php?t=540836").  The question in that case was a bit different than yours, but the resulting script will provide a good start for you.  Note: Please read the entire thread!

Lloyd B.

---

### Post by kaiju on 2008-02-18
i've read the thread you linked me to, and it looks like i can build on that and the tools you mentioned. thank you.

the tricky part is that i have mp3 as well as ogg files in my music directory.
if i am to integrate both mp3info and ogginfo into the script, can i specify which one of them to be used based on extensions, so that the script only needs to browse through the directory once, or do i have to make the script run e.g. the ogginfo renaming after the mp3info renaming is done?

also, is there a way of adding a "0" in front of all track numbers consisting of only one digit?

---

### Post by lloyd_b on 2008-02-18
> **kaiju said:**
> i've read the thread you linked me to, and it looks like i can build on that and the tools you mentioned. thank you.

the tricky part is that i have mp3 as well as ogg files in my music directory.
if i am to integrate both mp3info and ogginfo into the script, can i specify which one of them to be used based on extensions, so that the script only needs to browse through the directory once, or do i have to make the script run e.g. the ogginfo renaming after the mp3info renaming is done?

also, is there a way of adding a "0" in front of all track numbers consisting of only one digit?

Here's a quick-and-dirty shell script that can provide some help on dealing with ogg vs. mp3 files:
```
#!/bin/bash

for FILENAME in $@; do
        EXT=`echo $FILENAME | cut -d '.' -f 2`

        if test "$EXT" == "mp3"; then
                echo "$FILENAME is an mp3 file"
        elif test "$EXT" == "ogg"; then
                echo "$FILENAME is an ogg file"
        else
                echo "$FILENAME is something else"
        fi
done
```

What this script does is loops through the command line parameters, and checks each one to see if it's an mp3, an ogg, or something else.

The "for ..." line fetches the command line parameters, one at a time, an runs them through the loop.  Note: probably won't work correctly if the filenames have spaces in them.  The other thread touches on this issue an provides a workaround.

In the "EXT=..." line, note the "backtics" (`) surrounding the command.  This causes the command to be run, and the output from it returned, to be stored in the shell variable "EXT".

The "cut -d '.' -f 2" says "Take the text, and using period as a separator, return the 2nd field".  Note that while this will normally return the extension, but will produce garbage if the filename has more than one period in it.

As for forcing a leading zero on the track number, with mp3info it's as simple as using "%02n" in the format.  I have no clue how to accomplish this with ogginfo (not familiar with that program).

Lloyd B.

---

### Post by kaiju on 2008-02-22
i just erased a couple of music directories :)

when there is no id3 tag, or if the required fields are not filled out in the tag, i'm getting all my files renamed to the same name (all but the last one will de erased). mp3info hovewer first gives me a message like this one:

./Rancid_(2000)/21_Reconciliation.mp3 **does not have an ID3 1.x tag.**

can i use this to make the script error out if the required fields are not present in the tag?

---

### Post by lloyd_b on 2008-02-22
> **kaiju said:**
> i just erased a couple of music directories :)

Ouch.  Yeah, debugging a script can cause results like that.

> when there is no id3 tag, or if the required fields are not filled out in the tag, i'm getting all my files renamed to the same name (all but the last one will de erased). mp3info hovewer first gives me a message like this one:

./Rancid_(2000)/21_Reconciliation.mp3 **does not have an ID3 1.x tag.**

can i use this to make the script error out if the required fields are not present in the tag?

Testing against that string is NOT safe.  From some quick tests I've run here, that error does *NOT* appear if the requested tag is missing (it just returns a null string), only if there are no ID3 tags whatsoever.  So testing against that string will still produce potentially destructive errors if there are ID3 tags in the file, but one or more of the fields is missing...

Here's another quick-and-dirty script that demonstrates a way to properly verify that the necessary fields are present:
```
#!/bin/bash

for FILENAME in $@; do

        ARTIST=`mp3info -p "%a" "$FILENAME"`
        YEAR=`mp3info -p "%y" "$FILENAME"`
        ALBUM=`mp3info -p "%l" "$FILENAME"`
        TRACK=`mp3info -p "%02n" "$FILENAME"`
        TITLE=`mp3info -p "%t" "$FILENAME"`

        echo -n "$FILENAME --> "
        if test -n "$ARTIST"; then
                if test -n "$YEAR"; then
                        if test -n "$ALBUM"; then
                                if test -n "$TRACK"; then
                                        if test -n "$TITLE"; then
                                                echo "All required info present"
                                        else
                                                echo "Track Title is missing"
                                        fi
                                else
                                        echo "Track number is missing"
                                fi
                        else
                                echo "Album name is missing"
                        fi
                else
                        echo "Album year is missing"
                fi
        else
                echo "Artist name is missing"
        fi

done
```

Basically, it calls mp3info once for each *field*, rather than once per file.  Then, it uses the "test -n..." conditional (which returns TRUE if the specified string is not zero length) to verify that it got something back from mp3info.

(Note: that "...does not have an ID3 1.x tag..." string is *not* returned, as it's appearing on the "stderr" (standard error) stream, rather than the "stdout" (standard output) stream.)

I'm not particularly happy with this solution (it seems way too cumbersome to me), but it does work.  Maybe someone else will wander by with a more elegant solution.

Lloyd B.

---

