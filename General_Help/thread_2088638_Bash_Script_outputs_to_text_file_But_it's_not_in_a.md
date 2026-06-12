---
title: "Bash Script outputs to text file But it's not in alphabetical order?"
date: 2012-11-27
forum: General Help
---

### Post by Singtoh on 2012-11-27
Hello All,

I have been trying to get this script to work properly and I have nearly given up. That is why I thought I would post here for some help. This is not my script, I found it on the internet and have tried to adapt it to my needs but am not having to much luck. I know there is some extra stuff in the script that I don't need but it runs sort of? I am not a scripter or coder by any means, getting a bit too old for that I think. The script runs but what I would like it to do is output to a text file in my home directory. It outputs now but the results are not in alphabetical order and I would like all the Artists to be printed from A-Z if this is possible. This script is going to scan my music library and retrieve the replaygain data from all of the flac tags. The reason I am trying to do this is because I am trying to use replay gain values to pick out tracks that are possibly clipped so I don't have to open every single file in audacity one by one. I have had about %60-%70 percent in being able to pick files that have some clipping on them. Unless someone has a better idea or a better way. I have around 700gig of flac files to check, so this will take awhile. Anyway here is the script and I hope someone can help sort this mess out. I thank all of you for any kind help in advance, I really appreciate it:).


Cheers, 

Singtoh

```
#!/bin/bash

if [ ! -d "$1" ]
then
    echo "Arg "$1" is NOT a directory!"
    exit $ARGUMENT_NOT_DIRECTORY
fi

flacnum=`ls "$1" | grep -c \\.flac`

if [ $flacnum -lt 1 ]
then
    echo $1" (No FLAC files, moving on)"
    exit 0
else
    echo $1" ("$flacnum" FLAC files)"
fi

    echo "Tag values:"
flacfiles=`ls -1 "$1"/*.flac`
IFS=$'\012'
for file in $flacfiles
do
    if [ ! -e "$file" ]
    then
    echo "Error: file "$file" not found."
    exit $FILE_NOT_FOUND
    fi

    echo $file
    metaflac --show-tag=ARTIST --show-tag=TITLE --show-tag=REPLAYGAIN_TRACK_GAIN --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_ALBUM_PEAK "$file"
    exec 1>>/home/singtoh/rgvaluesM.txt
    
 done
```

---

### Post by SlugSlug on 2012-11-27
could you post a little bit of the output your currently getting?

---

### Post by Singtoh on 2012-11-27
Hello SlugSlug,

Thank you for the reply. This is a touch of what is outputting now:

```
/media/Storage/Music/Rock/Coldplay - Discography Lite/2000-07-10 - Parachutes - Parlophone 527 7832 GB/10 Everything's Not Lost _ Life Is for Living.flac
artist=Coldplay
title=Everything's Not Lost / Life Is for Living
REPLAYGAIN_TRACK_GAIN=-8.11 dB
REPLAYGAIN_ALBUM_GAIN=-8.11 dB
REPLAYGAIN_ALBUM_PEAK=0.99996948
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/02 In My Place.flac
artist=Coldplay
title=In My Place
REPLAYGAIN_TRACK_GAIN=-8.67 dB
REPLAYGAIN_ALBUM_GAIN=-8.67 dB
REPLAYGAIN_ALBUM_PEAK=0.99996948
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/03 God Put a Smile Upon Your Face.flac
artist=Coldplay
title=God Put a Smile Upon Your Face
REPLAYGAIN_TRACK_GAIN=-9.28 dB
REPLAYGAIN_ALBUM_GAIN=-9.28 dB
REPLAYGAIN_ALBUM_PEAK=0.99996948
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/04 The Scientist.flac
artist=Coldplay
title=The Scientist
REPLAYGAIN_TRACK_GAIN=-8.72 dB
REPLAYGAIN_ALBUM_GAIN=-8.72 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/05 Clocks.flac
artist=Coldplay
title=Clocks
REPLAYGAIN_TRACK_GAIN=-8.85 dB
REPLAYGAIN_ALBUM_GAIN=-8.85 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/06 Daylight.flac
artist=Coldplay
title=Daylight
REPLAYGAIN_TRACK_GAIN=-9.00 dB
REPLAYGAIN_ALBUM_GAIN=-9.00 dB
REPLAYGAIN_ALBUM_PEAK=0.99996948
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/07 Green Eyes.flac
artist=Coldplay
title=Green Eyes
REPLAYGAIN_TRACK_GAIN=-7.32 dB
REPLAYGAIN_ALBUM_GAIN=-7.32 dB
REPLAYGAIN_ALBUM_PEAK=0.99996948
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/08 Warning Sign.flac
artist=Coldplay
title=Warning Sign
REPLAYGAIN_TRACK_GAIN=-7.63 dB
REPLAYGAIN_ALBUM_GAIN=-7.63 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/09 A Whisper.flac
artist=Coldplay
title=A Whisper
REPLAYGAIN_TRACK_GAIN=-9.58 dB
REPLAYGAIN_ALBUM_GAIN=-9.58 dB
REPLAYGAIN_ALBUM_PEAK=0.99996948
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/10 A Rush of Blood to the Head.flac
```The directory part /media/Storage/Music/Rock/ I don't need but couldn't seem to make it go away without making it log nothing??

So if I could get the Artist into alphabetical order for a start would be nice or another idea I had would be to highlight all the numbers of REPLAYGAIN_TRACK_GAIN=-9.58 dB and REPLAYGAIN_ALBUM_GAIN=-9.58 dB to BOLD and RED all the way tru that go below say -4dB then I really wouldn't need to order it from A-Z. That would give me a visual cue of something to look at, then I could adjust that -4dB number to what works best for finding the clipped tracks, or even just have it log to a file anything that goes below -4dB according to REPLAYGAIN_TRACK_GAIN=-9.58 dB and REPLAYGAIN_ALBUM_GAIN=-9.58 dB  or a given number, I don't know of the best way?? I ran this thru my library and its like 3000 pages long:(. I wish there was a program that say would open the flac files one by one, find clipping, close said track, log it to a file and then carry on all the way thru but I think that's a pipe dream?? Do you have any ideas possibly?? I guess it's a start if I can get it in order and/or highlighted in some way?? I just can't get my head around this scripting stuff. Thanks SlugSlug for the reply and hopefully some help:)

Cheers,

Singtoh

---

### Post by Singtoh on 2012-11-27
Hello All,

This is what i have now which outputs to the text file better but it only prints the last bit of the file??

```
#!/bin/bash -u
echo "You entered: '${*-}'"

(
if [ ! -d "$1" ]
then
    echo "Arg "$1" is NOT a directory!"
    exit $ARGUMENT_NOT_DIRECTORY
fi

flacnum=`ls "$1" | grep -c \\.flac`

if [ $flacnum -lt 1 ]
then
    echo $1" (No FLAC files, moving on)"
    exit 0
else
    echo $1" ("$flacnum" FLAC files)"
fi

    echo "Tag Values Retrieved:"
flacfiles=`ls -1 "$1"/*.flac`
IFS=$'\012'
for file in $flacfiles
do
    if [ ! -e "$file" ]
    then
    echo "Error: file "$file" not found."
    exit $FILE_NOT_FOUND
    fi


    metaflac --show-tag=ARTIST --show-tag=TITLE --show-tag=REPLAYGAIN_TRACK_GAIN --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_ALBUM_PEAK "$file"

    
done) 2>&1 | tee rgainvaluesMUSIC.log
```

And here is what is in the text file after I ctrl+c to stop it after a minute or so, it's just the last bit of info from rite before I hit ctrl+c???:

/media/Storage/Music/Rock/REO Speedwagon - Original Album Classics - 5 CD Box Set/1978 - You Can Tune a Piano, But You Can't Tuna Fish - Epic JE35082 US (9 FLAC files)
Tag Values Retrieved:
artist=REO Speedwagon
title=Roll With the Changes
REPLAYGAIN_TRACK_GAIN=-7.88 dB
REPLAYGAIN_ALBUM_GAIN=-8.52 dB
REPLAYGAIN_ALBUM_PEAK=0.99893188
artist=REO Speedwagon
title=Time for Me to Fly
REPLAYGAIN_TRACK_GAIN=-7.49 dB
REPLAYGAIN_ALBUM_GAIN=-8.52 dB
REPLAYGAIN_ALBUM_PEAK=0.99893188

As I said, I am not a coder by any stretch,not even a little bit, just trying get something that works somewhat??

Cheers,

Singtoh

---

### Post by steeldriver on 2012-11-27
I haven't really read your script, but try

```
tee **-a** rgainvaluesMUSIC.log
```(a = append - the default for tee is to overwrite)

---

### Post by Vaphell on 2012-11-27
to print out track/album gains below -4
```
awk -v threshold=-4 '
      /[/]media[/]/ { file=$0 }
      /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
      /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
      /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
    ' in.txt
```

i can only guess what you meant exactly though, your description of the problem is rather chaotic

---

### Post by Singtoh on 2012-11-27
> **steeldriver said:**
> I haven't really read your script, but try

```
tee **-a** rgainvaluesMUSIC.log
```(a = append - the default for tee is to overwrite)

  Thanks Steeldriver. That let it print all 3000 pages of  info. Now if I can narrow it down some I might win. I appreciate the help.

Cheers,

Singtoh

---

### Post by Vaphell on 2012-11-27
read post #6
below -4.0 as in -5, -6... -9, etc?

---

### Post by Singtoh on 2012-11-27
> **Vaphell said:**
> to print out track/album gains below -4
```
awk -v threshold=-4 '
      /[/]media[/]/ { file=$0 }
      /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
      /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
      /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
    ' in.txt
```i can only guess what you meant exactly though, your description of the problem is rather chaotic

Hello Vaphell,

Thanks for the reply. This is a snippet of what I get output with your code inserted to my script:

artist=Queen
title=Man on the Prowl
REPLAYGAIN_TRACK_GAIN=-9.31 dB
REPLAYGAIN_ALBUM_GAIN=-9.20 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=Machines (or 'Back to Humans')
REPLAYGAIN_TRACK_GAIN=-9.16 dB
REPLAYGAIN_ALBUM_GAIN=-9.20 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=I Want to Break Free
REPLAYGAIN_TRACK_GAIN=-5.91 dB
REPLAYGAIN_ALBUM_GAIN=-9.20 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=Keep Passing the Open Windows
REPLAYGAIN_TRACK_GAIN=-9.39 dB
REPLAYGAIN_ALBUM_GAIN=-9.20 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=Hammer to Fall
REPLAYGAIN_TRACK_GAIN=-9.96 dB
REPLAYGAIN_ALBUM_GAIN=-9.20 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=Is This the World We Created...?
REPLAYGAIN_TRACK_GAIN=-4.59 dB
REPLAYGAIN_ALBUM_GAIN=-9.20 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=I Go Crazy
REPLAYGAIN_TRACK_GAIN=-9.17 dB
REPLAYGAIN_ALBUM_GAIN=-9.01 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=I Want to Break Free (single remix)
REPLAYGAIN_TRACK_GAIN=-8.14 dB
REPLAYGAIN_ALBUM_GAIN=-9.01 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=Hammer to Fall (Headbanger's mix)
REPLAYGAIN_TRACK_GAIN=-9.78 dB
REPLAYGAIN_ALBUM_GAIN=-9.01 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=Is This the World We Created...? (live in Rio, January 1985)
REPLAYGAIN_TRACK_GAIN=-6.46 dB
REPLAYGAIN_ALBUM_GAIN=-9.01 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[
awk: line 2: syntax error at or near ]
artist=Queen
title=It's a Hard Life (live in Rio, January 1985)
REPLAYGAIN_TRACK_GAIN=-9.11 dB
REPLAYGAIN_ALBUM_GAIN=-9.01 dB
REPLAYGAIN_ALBUM_PEAK=1.00000000
awk: line 2: regular expression compile failed (bad class -- [], [^] or [)
[

Sorry for the chaotic explanation:( Maybe I can be more clear. I am trying to scan the whole music library of around 700gig of flac files with this replaygain script and pick out high replaygain values, high meaning below -4dB(or I could change that number to what works best for finding clipping). So for instance a replaygain value of -10dB is most likely to have clipping on that track, and a replaygain value of -4dB is most likely to be clean. Then I can go to Audacity and fix it or if it's too bad, throw it out and re-rip the album. So if it prints only what is below i.e -4dB, I might only have to look at 2000 files instead of 8000. I don't know of another way to do this, but I think it's going to be a job to say the least:( I hope that is a bit more clearly put. I thank you very much Vaphell and Steeldriver for the help, I really appreciate it. I don't think I could ever wrap my head around this coding, it's giving me a headache:)

Cheers,
 
Singtoh

---

### Post by Vaphell on 2012-11-27
hm, works here on the test file... maybe try changing the pattern to this one in blue
```
[b]$ awk -v threshold=-4 '
>       [COLOR="Blue"]/^\//[/COLOR] { file=$0 }
>       /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
>       /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
>       /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
>     ' in.txt[/b]
/media/Storage/Music/Rock/Coldplay - Discography Lite/2000-07-10 - Parachutes - Parlophone 527 7832 GB/10 Everything's Not Lost _ Life Is for Living.flac
track gain: -8.11, album gain: -8.11
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/02 In My Place.flac
track gain: -8.67, album gain: -8.67
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/03 God Put a Smile Upon Your Face.flac
track gain: -9.28, album gain: -9.28
...
```

---

### Post by Singtoh on 2012-11-27
> **Vaphell said:**
> hm, works here on the test file... maybe try changing the pattern to this one in blue
```
[B]$ awk -v threshold=-4 '
>       [COLOR=Blue]/^\//[/COLOR] { file=$0 }
>       /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
>       /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
>       /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
>     ' in.txt[/B]
/media/Storage/Music/Rock/Coldplay - Discography Lite/2000-07-10 - Parachutes - Parlophone 527 7832 GB/10 Everything's Not Lost _ Life Is for Living.flac
track gain: -8.11, album gain: -8.11
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/02 In My Place.flac
track gain: -8.67, album gain: -8.67
/media/Storage/Music/Rock/Coldplay - Discography Lite/2002-08-26 - A Rush of Blood to the Head - Parlophone 540 5042 GB/03 God Put a Smile Upon Your Face.flac
track gain: -9.28, album gain: -9.28
...
```

Hello Again Vaphell,

This is a snippet of what I am getting after changing that:
artist=Fleetwood Mac
title=The City
REPLAYGAIN_TRACK_GAIN=-2.05 dB
REPLAYGAIN_ALBUM_GAIN=-2.05 dB
REPLAYGAIN_ALBUM_PEAK=0.73333740
awk: cannot open in.txt (No such file or directory)
artist=Fleetwood Mac
title=Miles Away
REPLAYGAIN_TRACK_GAIN=-3.04 dB
REPLAYGAIN_ALBUM_GAIN=-3.04 dB
REPLAYGAIN_ALBUM_PEAK=0.91717529
awk: cannot open in.txt (No such file or directory)
artist=Fleetwood Mac
title=Somebody
REPLAYGAIN_TRACK_GAIN=-2.24 dB
REPLAYGAIN_ALBUM_GAIN=-2.24 dB
REPLAYGAIN_ALBUM_PEAK=0.93945312
awk: cannot open in.txt (No such file or directory)

So it's still printing higher(or is that lower):) than -4dB and that other awk: ect.ect. A value less than -4dB going toward 0dB is a good thing and I don't need to print that and -4dB going towards -10dB is a bad thing and I do need to print that. Sorry, I get confused a bit on the higher/lower explanation:confused: I guess something in my script might be throwing it off maybe?? I don't have a clue:confused:Thanks again Vaphell

Cheers,

Singtoh

---

### Post by Vaphell on 2012-11-27
obviously you should use your file *rgainvaluesMUSIC.log* instead of *in.txt*, that one was my dummy file for tests.

```
awk -v threshold=-4 '
       /^\// { file=$0 }
       /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
       /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
       /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
     ' **rgainvaluesMUSIC.log**
```

---

### Post by Singtoh on 2012-11-27
> **Vaphell said:**
> obviously you should use your file *rgainvaluesMUSIC.log* instead of *in.txt*, that one was my dummy file for tests.

```
awk -v threshold=-4 '
       /^\// { file=$0 }
       /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
       /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
       /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
     ' **rgainvaluesMUSIC.log**
```

Oooop's :mad:Sorry I sidn't see that one.

I'll give it another look

---

### Post by Singtoh on 2012-11-27
> **Singtoh said:**
> Oooop's :mad:Sorry I sidn't see that one.

I'll give it another look

Heres my script and the results of the las go, Vaphell

```
#!/bin/bash -u
echo "You entered: '${*-}'"

(
if [ ! -d "$1" ]
then
    echo "Arg "$1" is NOT a directory!"
    exit $ARGUMENT_NOT_DIRECTORY
fi

flacnum=`ls "$1" | grep -c \\.flac`

if [ $flacnum -lt 1 ]
then
    echo $1" (No FLAC files, moving on)"
    exit 0
else
    echo $1" ("$flacnum" FLAC files)"
fi

    echo "Tag Values Retrieved:"
flacfiles=`ls -1 "$1"/*.flac`
IFS=$'\012'
for file in $flacfiles
do
    if [ ! -e "$file" ]
    then
    echo "Error: file "$file" not found."
    exit $FILE_NOT_FOUND
    fi


    metaflac --show-tag=ARTIST --show-tag=TITLE --show-tag=REPLAYGAIN_TRACK_GAIN --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_ALBUM_PEAK "$file"

awk -v threshold=-4 '
      /^\// { file=$0 }
      /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
      /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
      /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
    ' rgainvaluesMUSIC.log

    
done) 2>&1 | tee -a rgainvaluesMUSIC.log
```

/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: -1.12, album gain: -1.12
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: +1.09, album gain: +1.09
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: -0.27, album gain: -0.27
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: -3.49, album gain: -3.49
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: -1.85, album gain: -1.85
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: -1.39, album gain: -1.39
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: +0.10, album gain: +0.10
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)
track gain: -0.94, album gain: -0.94
/media/Storage/Music/Rock/U2 - Discography Lite/1993-07-05 - Zooropa - Nippon Phonogram PHCR-1750 JP (10 FLAC files)

Sorry for the earlier mistake Vaphell.

Cheers,

Singtoh

---

### Post by Singtoh on 2012-11-28
> **Vaphell said:**
> obviously you should use your file *rgainvaluesMUSIC.log* instead of *in.txt*, that one was my dummy file for tests.

```
awk -v threshold=-4 '
       /^\// { file=$0 }
       /TRACK_GAIN/ { t_gain=$1; sub( /.*=/, "", t_gain ); }
       /ALBUM_GAIN/ { a_gain=$1; sub( /.*=/, "", a_gain ); }
       /ALBUM_PEAK/ { if (t_gain < threshold || a_gain < threshold) print file "\ntrack gain: " t_gain ", album gain: " a_gain; }
     ' **rgainvaluesMUSIC.log**
```

I guess I replied to my own post, please see the post above. I'm having a bad day I guess:(

Cheers,

Singtoh

---

### Post by Vaphell on 2012-11-28
run that awk once at the end, after the log file is filled with data, not every time you process a dir.
Also if i am not mistaken, each run of the script appends to the file. Wont there be a boatload of redundant data in that file with every execution?


How do you call that script exactly? i think that you could scan all flac files nicely with a single *find* command and then use *awk* similar to the one you have right now. probably 5 lines of code.

edit:
something like this
```
while IFS= read -rd $'\0' dr
  do metaflac --with-filename --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN "$dr"/*.flac
done < <( find /media/Storage/Music/ -type d -print0 ) | awk 'BEGIN {FS="[ =]"}; $(NF-1)<-4 { print $0; }'
```

---

### Post by Singtoh on 2012-11-28
> **Vaphell said:**
> run that awk once at the end, after the log file is filled with data, not every time you process a dir.
Also if i am not mistaken, each run of the script appends to the file. Wont there be a boatload of redundant data in that file with every execution?


How do you call that script exactly? i think that you could scan all flac files nicely with a single *find* command and then use *awk* similar to the one you have right now. probably 5 lines of code.

edit:
something like this
```
while IFS= read -rd $'\0' dr
  do metaflac --with-filename --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN "$dr"/*.flac
done < <( find /media/Storage/Music/ -type d -print0 ) | awk 'BEGIN {FS="[ =]"}; $(NF-1)<-4 { print $0; }'
```

Hello Vaphell,

Sorry for the delay getting back, had to run an errand for the missus. I have been deleting that log file before every run of the script and this is how I call the script:

```
if [ ! -d "$1" ]
then
    echo "Arg "$1" is NOT a directory!"
    exit $ARGUMENT_NOT_DIRECTORY
fi

echo "********************************************************"
echo "Calling metadata.sh on each directory in:"
echo $1
echo ""
find "$1" -type d -exec ~/metadata1.sh '{}' \;

```

Tis is another script in the same directory I call with a bash alias. Yeah, I guess the way I am diong it is a bit convoluted, but I got the script off the internet and adapted it or tried to adapt it to my needs so there is stuff in the script that I am sure I don't need. Like I said I am not a coder, I'm just trying to cobble something together that works. So, I'll give the new code a try and see what happens and post again, the missus has gone to town so she won't be nagging in my ear for awhile:). Thanks Vaphell

Cheers,

Singtoh

---

### Post by Singtoh on 2012-11-28
> **Vaphell said:**
> run that awk once at the end, after the log file is filled with data, not every time you process a dir.
Also if i am not mistaken, each run of the script appends to the file. Wont there be a boatload of redundant data in that file with every execution?


How do you call that script exactly? i think that you could scan all flac files nicely with a single *find* command and then use *awk* similar to the one you have right now. probably 5 lines of code.

edit:
something like this
```
while IFS= read -rd $'\0' dr
  do metaflac --with-filename --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN "$dr"/*.flac
done < <( find /media/Storage/Music/ -type d -print0 ) | awk 'BEGIN {FS="[ =]"}; $(NF-1)<-4 { print $0; }'
```

Ok Vaphell,

This works:

```
#!/bin/bash -u
echo "You entered: '${*-}'"

(
while IFS= read -rd $'\0' dr
  do metaflac --with-filename --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN "$dr"/*.flac
done < <( find /media/Storage/Music/ -type d -print0 ) | awk 'BEGIN {FS="[ =]"}; $(NF-1)<-4 { print $0; }') 2>&1 | tee -a rgainvaluesMUSIC.log

```

and it outputs this:

/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/1999-11-23 - The Complete Blue Horizon Sessions 1967-1969 - Blue Horizon 73003-2 US/5-10 Sugar Mama (take 1).flac:REPLAYGAIN_ALBUM_GAIN=-4.26 dB
/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/1999-11-23 - The Complete Blue Horizon Sessions 1967-1969 - Blue Horizon 73003-2 US/5-11 Sugar Mama.flac:REPLAYGAIN_ALBUM_GAIN=-4.26 dB
/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/1999-11-23 - The Complete Blue Horizon Sessions 1967-1969 - Blue Horizon 73003-2 US/5-12 Homework.flac:REPLAYGAIN_ALBUM_GAIN=-4.26 dB
/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/1999-11-23 - The Complete Blue Horizon Sessions 1967-1969 - Blue Horizon 73003-2 US/5-13 Honey Boy Blues.flac:REPLAYGAIN_ALBUM_GAIN=-4.26 dB
/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/1999-11-23 - The Complete Blue Horizon Sessions 1967-1969 - Blue Horizon 73003-2 US/5-14 I Need Your Love (tak.flac:REPLAYGAIN_ALBUM_GAIN=-4.26 dB
/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/1999-11-23 - The Complete Blue Horizon Sessions 1967-1969 - Blue Horizon 73003-2 US/5-14 I Need Your Love (tak.flac:REPLAYGAIN_TRACK_GAIN=-5.08 dB
/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/1999-11-23 - The Complete Blue Horizon Sessions 1967-1969 - Blue Horizon 73003-2 US/5-15 Horton's Boogie

so now I just have to make it output only ARTIST, ALBUM, REPLAYGAIN_TRACK_GAIN, and REPLAYGAIN_ALBUM_GAIN. The rest of it I don't need. So to clean things up a bit. I think I can make it do that. Your super super Vaphell, I really thank you very very big for your patience and help. This kinda stuff really does my head in:confused:  Big headache:confused:

Thanks again Vaphell:) I'll try and give this a go and see how I get on.

Cheers Vaphell
All the best,

Singtoh

---

### Post by Singtoh on 2012-11-28
> **Vaphell said:**
> run that awk once at the end, after the log file is filled with data, not every time you process a dir.
Also if i am not mistaken, each run of the script appends to the file. Wont there be a boatload of redundant data in that file with every execution?


How do you call that script exactly? i think that you could scan all flac files nicely with a single *find* command and then use *awk* similar to the one you have right now. probably 5 lines of code.

edit:
something like this
```
while IFS= read -rd $'\0' dr
  do metaflac --with-filename --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN "$dr"/*.flac
done < <( find /media/Storage/Music/ -type d -print0 ) | awk 'BEGIN {FS="[ =]"}; $(NF-1)<-4 { print $0; }'
```

Hello Again Vaphell,

I'm stuck. Here is the script I am using and the output that I am trying to achieve with your code to print only anything that is under -4dB:

```
#!/bin/bash -u
echo "You entered: '${*-}'"

(
if [ ! -d "$1" ]
then
    echo "Arg "$1" is NOT a directory!"
    exit $ARGUMENT_NOT_DIRECTORY
fi

flacnum=`ls "$1" | grep -c \\.flac`

if [ $flacnum -lt 1 ]
then
    echo $1" (No FLAC files, moving on)"
    exit 0
else
    echo $1" ("$flacnum" FLAC files)"
fi

    echo "Tag Values Retrieved:"
flacfiles=`ls -1 "$1"/*.flac`
IFS=$'\012'
for file in $flacfiles
do
    if [ ! -e "$file" ]
    then
    echo "Error: file "$file" not found."
    exit $FILE_NOT_FOUND
    fi

    metaflac --show-tag=ARTIST --show-tag=TITLE --show-tag=REPLAYGAIN_TRACK_GAIN --show-tag=REPLAYGAIN_ALBUM_GAIN "$file"

#while IFS= read -rd $'\0' dr
    #do metaflac --show-tag=ARTIST --show-tag=TITLE --show-tag=REPLAYGAIN_TRACK_GAIN --show-tag=REPLAYGAIN_ALBUM_GAIN "$dr"/*.flac 
    #done < <( -type d -print0 ) | awk 'BEGIN {FS="[ =]"}; $(NF-1)<-4 { print $0; }'
    
done) 2>&1 | tee -a rgainvaluesMUSIC.log




```

and some of the output that I would like to see:

Tag Values Retrieved:
artist=The Doobie Brothers
title=Listen to the Music
REPLAYGAIN_TRACK_GAIN=-1.45 dB
REPLAYGAIN_ALBUM_GAIN=-1.45 dB
artist=The Doobie Brothers
title=Rockin' Down the Highway
REPLAYGAIN_TRACK_GAIN=+0.03 dB
REPLAYGAIN_ALBUM_GAIN=+0.03 dB
artist=The Doobie Brothers
title=Mamaloi
REPLAYGAIN_TRACK_GAIN=+1.15 dB
REPLAYGAIN_ALBUM_GAIN=+1.15 dB
artist=The Doobie Brothers
title=Toulouse Street
REPLAYGAIN_TRACK_GAIN=+6.52 dB
REPLAYGAIN_ALBUM_GAIN=+6.52 dB
artist=The Doobie Brothers
title=Cotton Mouth
REPLAYGAIN_TRACK_GAIN=+0.16 dB
REPLAYGAIN_ALBUM_GAIN=+0.16 dB
artist=The Doobie Brothers
title=Don't Start Me to Talkin'
REPLAYGAIN_TRACK_GAIN=-1.73 dB
REPLAYGAIN_ALBUM_GAIN=-1.73 dB
artist=The Doobie Brothers
title=Jesus Is Just Alright
REPLAYGAIN_TRACK_GAIN=-0.56 dB
REPLAYGAIN_ALBUM_GAIN=-0.56 dB
artist=The Doobie Brothers
title=White Sun
REPLAYGAIN_TRACK_GAIN=+0.72 dB
REPLAYGAIN_ALBUM_GAIN=+0.72 dB
artist=The Doobie Brothers
title=Disciple
REPLAYGAIN_TRACK_GAIN=+1.03 dB
REPLAYGAIN_ALBUM_GAIN=+1.03 dB
artist=The Doobie Brothers
title=Snake Man
REPLAYGAIN_TRACK_GAIN=+2.11 dB
REPLAYGAIN_ALBUM_GAIN=+2.11 dB

But I can't seem to get your code to work with my script and print in the format above only tracks that are below the -4dB. Your code works really well. I can change the -4dB to -10dB and it only prints exactly what is below or above the given number, but it's not easily readable, with the directory, file names, album catalog numbers ect.ect. I am trying to get it to work with my script and output in the format above but I am failing miserably and about to give up.:( At the risk of asking you for too much, could I please get some more help from you on this?? Sorry Vaphell, I just can't get it to work. Thanks in advance for any more help you could be so gracious to pass my way.:)

Cheers,

Singtoh

---

### Post by Vaphell on 2012-11-28
no idea if these work, i have no flac collection so i tested this only on few sample files found on the internet

flac_info.sh
```
#!/bin/bash

shopt -s nullglob
while (( $# ))
do
  [ -d "$1" ] && dirs+=( "$1" )
  shift
done
mflac=( --no-filename --show-tag=ARTIST --show-tag=ALBUM --show-tag=TITLE --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN )


while IFS= read -rd $'\0' dr
do
  files=( "$dr"/*.flac )
  [ ${#files[@]} -eq 0 ] && continue
  for f in "${files[@]}"
  do
    metaflac "${mflac[@]}" "$f"
    echo "-----"
  done
done < <( find "${dirs[@]}" -type d -print0 )
```

gain.awk (should be executable)
```
#!/usr/bin/awk -f

        BEGIN { FS="[ =]"; ag=1000; tg=1000; }
    /ARTIST=/ { a=$0; }
     /TITLE=/ { t=$0; }
     /ALBUM=/ { al=$0; }
/ALBUM_GAIN=/ { ag=$2; }
/TRACK_GAIN=/ { tg=$2; }
       /----/ {
                if( ag<x || tg<x )
                { 
                  print a; print t; print al;
                  printf("track gain: %s, album gain: %s\n", tg, ag);
                  print "---------";
                }
                a=""; t=""; al=""; ag=1000; tg=1000;
	      }

```

```
./flac_info.sh /media/Storage/Music /some/other/dir > some.file
./gain.awk -v x=-4 some.file
```
or in 1 line
```
./flac_info.sh /media/Storage/Music | ./gain.awk -v x=-4
```

i think the 1st method is better because you can dump data about the whole music collection to file once and then only work with that file without running everything again and again.

---

### Post by Singtoh on 2012-11-29
> **Vaphell said:**
> no idea if these work, i have no flac collection so i tested this only on few sample files found on the internet

flac_info.sh
```
#!/bin/bash

shopt -s nullglob
while (( $# ))
do
  [ -d "$1" ] && dirs+=( "$1" )
  shift
done
mflac=( --no-filename --show-tag=ARTIST --show-tag=ALBUM --show-tag=TITLE --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN )


while IFS= read -rd $'\0' dr
do
  files=( "$dr"/*.flac )
  [ ${#files[@]} -eq 0 ] && continue
  for f in "${files[@]}"
  do
    metaflac "${mflac[@]}" "$f"
    echo "-----"
  done
done < <( find "${dirs[@]}" -type d -print0 )
```gain.awk (should be executable)
```
#!/usr/bin/awk -f

        BEGIN { FS="[ =]"; ag=1000; tg=1000; }
    /ARTIST=/ { a=$0; }
     /TITLE=/ { t=$0; }
     /ALBUM=/ { al=$0; }
/ALBUM_GAIN=/ { ag=$2; }
/TRACK_GAIN=/ { tg=$2; }
       /----/ {
                if( ag<x || tg<x )
                { 
                  print a; print t; print al;
                  printf("track gain: %s, album gain: %s\n", tg, ag);
                  print "---------";
                }
                a=""; t=""; al=""; ag=1000; tg=1000;
          }

``````
./flac_info.sh /media/Storage/Music /some/other/dir > some.file
./gain.awk -v x=-4 some.file
```or in 1 line
```
./flac_info.sh /media/Storage/Music | ./gain.awk -v x=-4
```i think the 1st method is better because you can dump data about the whole music collection to file once and then only work with that file without running everything again and again.

Hello Vaphell,

And thank you again for the reply. I will give this new code you just sent a try. I have been trying to get the script I have now to do what I want and I am nearly there but for the life of me I can't get it to print the info I want. Here is a snippet of what my script with your previous code inserted is producing:

/media/Storage/Music/Rock/Fleetwood Mac - Discography Lite/2007 - English Rose - Beat Goes On Records BGOCD750 GB (12 FLAC files)
Tag Values Retrieved:
REPLAYGAIN_TRACK_GAIN=-8.87 dB
REPLAYGAIN_TRACK_GAIN=-9.53 dB
REPLAYGAIN_TRACK_GAIN=-10.57 dB
REPLAYGAIN_TRACK_GAIN=-8.58 dB
REPLAYGAIN_TRACK_GAIN=-10.34 dB

And another snippet of the same dump:
/media/Storage/Music/Rock/Joan Baez - Various Albums @320kbps/1995-11 - Diamonds & Rust - Mobile Fidelity Sound Lab UDCD 646 US (11 FLAC files)
Tag Values Retrieved:
album=Diamonds & Rust
title=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust
album=Diamonds & Rust

So as you can see it's not very consistent.:(

And here is a snippet of my script without your code to search the replaygain values:

Tag Values Retrieved:
artist=Fleetwood Mac
title=Emerald Eyes
REPLAYGAIN_TRACK_GAIN=-2.42 dB
REPLAYGAIN_ALBUM_GAIN=-2.42 dB
artist=Fleetwood Mac
title=Believe Me
REPLAYGAIN_TRACK_GAIN=-2.74 dB
REPLAYGAIN_ALBUM_GAIN=-2.74 dB
artist=Fleetwood Mac
title=Just Crazy Love
REPLAYGAIN_TRACK_GAIN=-3.30 dB
REPLAYGAIN_ALBUM_GAIN=-3.30 dB
artist=Fleetwood Mac
title=Hypnotized
REPLAYGAIN_TRACK_GAIN=-3.03 dB
REPLAYGAIN_ALBUM_GAIN=-3.03 dB
artist=Fleetwood Mac
title=Forever

I am pretty sure the problem lies in the awk part of the script. Something not letting it throw the info I need to the log or on the other side throwing too much info to the log, but as you are aware, I am not a coder so I guess that assumption is a wild guess. :confused:Anyway, thanks for the extra help and the new code.:) I will give it a try and post back.

Cheers,

Singtoh

---

### Post by Singtoh on 2012-11-29
> **Vaphell said:**
> no idea if these work, i have no flac collection so i tested this only on few sample files found on the internet

flac_info.sh
```
#!/bin/bash

shopt -s nullglob
while (( $# ))
do
  [ -d "$1" ] && dirs+=( "$1" )
  shift
done
mflac=( --no-filename --show-tag=ARTIST --show-tag=ALBUM --show-tag=TITLE --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN )


while IFS= read -rd $'\0' dr
do
  files=( "$dr"/*.flac )
  [ ${#files[@]} -eq 0 ] && continue
  for f in "${files[@]}"
  do
    metaflac "${mflac[@]}" "$f"
    echo "-----"
  done
done < <( find "${dirs[@]}" -type d -print0 )
```gain.awk (should be executable)
```
#!/usr/bin/awk -f

        BEGIN { FS="[ =]"; ag=1000; tg=1000; }
    /ARTIST=/ { a=$0; }
     /TITLE=/ { t=$0; }
     /ALBUM=/ { al=$0; }
/ALBUM_GAIN=/ { ag=$2; }
/TRACK_GAIN=/ { tg=$2; }
       /----/ {
                if( ag<x || tg<x )
                { 
                  print a; print t; print al;
                  printf("track gain: %s, album gain: %s\n", tg, ag);
                  print "---------";
                }
                a=""; t=""; al=""; ag=1000; tg=1000;
          }

``````
./flac_info.sh /media/Storage/Music /some/other/dir > some.file
./gain.awk -v x=-4 some.file
```or in 1 line
```
./flac_info.sh /media/Storage/Music | ./gain.awk -v x=-4
```i think the 1st method is better because you can dump data about the whole music collection to file once and then only work with that file without running everything again and again.

Hello Vaphell,

At the risk of sounding like a complete bonehead:confused: The first script flac_info.sh runs perfectly and outputs exactly the info I need in the correct format, but I don't see where to adjust the gain so it only outputs the "the less than -XdB values." The gain.awk runs in the terminal but I only see this:

  track gain: -11.51, album gain: -11.51
---------



track gain: -10.54, album gain: -10.54
---------



track gain: -10.28, album gain: -10.28
---------



track gain: -10.05, album gain: -10.05
---------
this was run at -10 to save time. So I ran gain.awk in terminal like this: 
./gain.awk -v x=-10 rgainvaluesMUSIC.log > rgainvaluesFAIL.log and it outputs a log with the same values as above only the track gain: -10.28, album gain: -10.28 values are logged with no ARTIST,ALBUM, ect. ect. ect. ect. . So I assume that gain.awk calls the log "rgainvaluesMUSIC.log" and does it's work, and outputs in this case "rgainvaluesFAIL.log"?? So if that is correct(assuming I am not a complete bonehead) then there is still a problem of sorts. Please sort me out if I am running this incorrectly?? Cheers Vaphell for your help and patience:confused:.

Singtoh

---

### Post by Singtoh on 2012-11-29
> **Vaphell said:**
> no idea if these work, i have no flac collection so i tested this only on few sample files found on the internet

flac_info.sh
```
#!/bin/bash

shopt -s nullglob
while (( $# ))
do
  [ -d "$1" ] && dirs+=( "$1" )
  shift
done
mflac=( --no-filename --show-tag=ARTIST --show-tag=ALBUM --show-tag=TITLE --show-tag=REPLAYGAIN_ALBUM_GAIN --show-tag=REPLAYGAIN_TRACK_GAIN )


while IFS= read -rd $'\0' dr
do
  files=( "$dr"/*.flac )
  [ ${#files[@]} -eq 0 ] && continue
  for f in "${files[@]}"
  do
    metaflac "${mflac[@]}" "$f"
    echo "-----"
  done
done < <( find "${dirs[@]}" -type d -print0 )
```gain.awk (should be executable)
```
#!/usr/bin/awk -f

        BEGIN { FS="[ =]"; ag=1000; tg=1000; }
    /ARTIST=/ { a=$0; }
     /TITLE=/ { t=$0; }
     /ALBUM=/ { al=$0; }
/ALBUM_GAIN=/ { ag=$2; }
/TRACK_GAIN=/ { tg=$2; }
       /----/ {
                if( ag<x || tg<x )
                { 
                  print a; print t; print al;
                  printf("track gain: %s, album gain: %s\n", tg, ag);
                  print "---------";
                }
                a=""; t=""; al=""; ag=1000; tg=1000;
          }

``````
./flac_info.sh /media/Storage/Music /some/other/dir > some.file
./gain.awk -v x=-4 some.file
```or in 1 line
```
./flac_info.sh /media/Storage/Music | ./gain.awk -v x=-4
```i think the 1st method is better because you can dump data about the whole music collection to file once and then only work with that file without running everything again and again.

Hello Vaphell,

I see how this is supposed to work I think. I'm a bit slow in my old age, forgive me.

So i run this from terminal: ./flac_info.sh /media/Storage/Music /home/patrick > rgainFAIL.log ./gain.awk -v x=-4 rgainFAIL.log  and it runs on thru nicely and if I assume correctly the gain.awk is supposed to process the rgainFAIL.log to only log anything below -4dB?? If that is correct then the gain.awk part isn't working yet??. The log goes into my home as it should and in a nice clean perfect format for my needs but, it seems that it is not being processed by the gain.awk because the full list of replaygain values is still there from +3dB to -11dB. So, I am probably doing something wrong somewhere or it's not yet working correctly?? Don't know Vaphell, sorry for all the back and forth, I'm getting a headache again.:confused:

Cheers,

Singtoh

---

### Post by Vaphell on 2012-11-29
paste example from the log file that is supposed to be filtered out yet it gets through

i compare both album gain and track gain (album gain < -4 will make the info to be printed out too) and you probably want only track gain tested?
if that's the case, this is the line you want to modify
```

/----/ {
         if( ag<x || tg<x )
         {
           ...
         }
```
if ( album_gain < threshold ) OR ( track_gain < threshold ) { print stuff }, throw away album gain part and ||

---

### Post by Singtoh on 2012-11-29
> **Vaphell said:**
> paste example from the log file that is supposed to be filtered out yet it gets through

i compare both album gain and track gain (album gain < -4 will make the info to be printed out too) and you probably want only track gain tested?
if that's the case, this is the line you want to modify
```

/----/ {
         if( ag<x || tg<x )
         {
           ...
         }
```if ( album_gain < threshold ) OR ( track_gain < threshold ) { print stuff }, throw away album gain part and ||

Hello Vaphell,

This is what flac_info.sh produces:

artist=The Doobie Brothers
album=Stampede
title=Sweet Maxine
REPLAYGAIN_ALBUM_GAIN=-1.68 dB
REPLAYGAIN_TRACK_GAIN=-1.68 dB
-----
artist=The Doobie Brothers
album=Stampede
title=Neal's Fandango
REPLAYGAIN_ALBUM_GAIN=+0.79 dB
REPLAYGAIN_TRACK_GAIN=+0.79 dB
-----
artist=The Doobie Brothers
album=Stampede
title=Texas Lullaby
REPLAYGAIN_ALBUM_GAIN=-0.84 dB
REPLAYGAIN_TRACK_GAIN=-0.84 dB
-----
artist=The Doobie Brothers
album=Stampede
title=Music Man
REPLAYGAIN_ALBUM_GAIN=-1.61 dB
REPLAYGAIN_TRACK_GAIN=-1.61 dB

Which is perfect for my needs except that it is not filtered by gain.awk. And this is the output after running gain.awk on that same log file. I ran the first snippet at -10 and the second at -7 and it does what it's suppose to do perfectly, except it doesn't output all the info as you can see : 

run at @ -10
---------



track gain: -10.06, album gain: -10.06
---------



track gain: -11.48, album gain: -11.48
---------



track gain: -10.70, album gain: -10.70
---------



track gain: -10.30, album gain: -10.30
---------



track gain: -11.45, album gain: -11.45
---------

run @ -7
-----------------------------------------------------------------------------------------------------------------------------------

track gain: -4.98, album gain: -7.05
---------



track gain: -6.36, album gain: -7.05
---------



track gain: -7.75, album gain: -7.75
---------



track gain: -8.34, album gain: -8.34
---------



track gain: -8.62, album gain: -8.62

And here is my attempt to make it output the same as the first snippet but only filtered, and I have failed miserably:( I just can't get it, it seems I might be close but it denies me joy every time:confused: And you are correct, I really only need ALBUM_GAIN,  ARTIST, TITLE, and ALBUM  to be filtered output, But TRACK_GAIN being included is just fine as well, kind of a bonus I guess.

-7.57
-7.57
ARTIST=
TITLE=
ALBUM=
TRACK_GAIN=-7.57
ALBUM_GAIN=-7.57
-----------------------------------------------------------------------------------------



-8.43
-8.43
ARTIST=
TITLE=
ALBUM=
TRACK_GAIN=-8.43
ALBUM_GAIN=-8.43
-----------------------------------------------------------------------------------------

Thanks Vaphell, I will try that new bit of code now and post back with the results.

Cheers,

Singtoh

---

### Post by Vaphell on 2012-11-29
in the output album=, title= and artist= are lowercase?
then make them lowercase as well in awk.
/pattern/ { ... } means "if line matches /pattern/, do { ... }"
apparently /TITLE=/ doesn't trigger when it looks at "title=..."

or make the test case insensitive so it works with "title=..." and "TITLE=..."

```

...
    toupper($0) ~ /ARTIST=/ { a=$0; }
     toupper($0) ~ /TITLE=/ { t=$0; }
     toupper($0) ~ /ALBUM=/ { al=$0; }
toupper($0) ~ /ALBUM_GAIN=/ { ag=$2; }
toupper($0) ~ /TRACK_GAIN=/ { tg=$2; }
...

```

---

### Post by Singtoh on 2012-11-29
> **Vaphell said:**
> in the output album=, title= and artist= are lowercase?
then make them lowercase as well in awk.
/pattern/ { ... } means "if line matches /pattern/, do { ... }"
apparently /TITLE=/ doesn't trigger when it looks at "title=..."

or make the test case insensitive so it works with "title=..." and "TITLE=..."

```

...
    toupper($0) ~ /ARTIST=/ { a=$0; }
     toupper($0) ~ /TITLE=/ { t=$0; }
     toupper($0) ~ /ALBUM=/ { al=$0; }
toupper($0) ~ /ALBUM_GAIN=/ { ag=$2; }
toupper($0) ~ /TRACK_GAIN=/ { tg=$2; }
...

```

Hello Vaphell,

Running this:

flac_info.sh /media/Storage/Music /home/patrick > rgainvalueMUSIC.log outputs this:

artist=Eric Clapton
album=Back Home
title=Say What You Will
REPLAYGAIN_ALBUM_GAIN=-9.09 dB
REPLAYGAIN_TRACK_GAIN=-8.51 dB
-----
artist=Eric Clapton
album=Back Home
title=I'm Going Left
REPLAYGAIN_ALBUM_GAIN=-9.09 dB
REPLAYGAIN_TRACK_GAIN=-10.31 dB
-----
artist=Eric Clapton
album=Back Home
title=Love Don't Love Nobody
REPLAYGAIN_ALBUM_GAIN=-9.09 dB
REPLAYGAIN_TRACK_GAIN=-8.09 dB

which is true and correct and in the same exact format as what is stored in the replaygain tags in the flac files.:)

Running this: 

gain.awk -v x=-4 rgainvalueMUSIC.log > rgainvalueMUSIC1.log after changing the capitalization ```
/artist=/ { a=$0; }
    /title=/ { t=$0; }
    /album=/ { al=$0; }
    /album_gain=/ { ag=$2; }
    /track_gain=/ { tg=$2; }
``` outputs this:

artist=Doobie Brothers, The
title=Ordinary Man
album=Sibling Rivalry
track gain: -7.68, album gain: -8.97
---------
artist=Doobie Brothers, The
title=Jericho
album=Sibling Rivalry
track gain: -8.46, album gain: -8.97
---------
artist=Doobie Brothers, The
title=On Every Corner
album=Sibling Rivalry
track gain: -7.77, album gain: -8.97
---------
artist=Doobie Brothers, The
title=Angels Of Madness
album=Sibling Rivalry
track gain: -8.65, album gain: -8.97

which is perfect for my needs :)  but it no longer filters, please see below.

So the capitalization was part of the problem and by changing that, it outputs what is required, but it no longer filters the below -4, -5, -10, -15(at -11 thru minus infinity it should output nothing)  whatever number I put in there. It just strictly outputs the same values as above with the same artist and values over and over:confused: But you nailed the capitilization part nicely:) Don't know what to do??

Cheers,

Singtoh

---

### Post by Vaphell on 2012-11-29
file with dummy data:
```
artist=AAA
album=AAA
title=AAA
REPLAYGAIN_ALBUM_GAIN=-5.09 dB
REPLAYGAIN_TRACK_GAIN=-5.51 dB
-----
artist=BBB
album=BBB
title=BBB
REPLAYGAIN_ALBUM_GAIN=-6.09 dB
REPLAYGAIN_TRACK_GAIN=-6.31 dB
-----
artist=CCC
album=CCC
title=CCC
REPLAYGAIN_ALBUM_GAIN=-7.09 dB
REPLAYGAIN_TRACK_GAIN=-7.09 dB
-----
artist=DDD
album=DDD
title=DDD
REPLAYGAIN_ALBUM_GAIN=-8.09 dB
REPLAYGAIN_TRACK_GAIN=-8.09 dB
-----
artist=EEE
album=EEE
title=EEE
REPLAYGAIN_ALBUM_GAIN=-18.09 dB
REPLAYGAIN_TRACK_GAIN=-18.09 dB
-----
```

gain.awk
```
#!/usr/bin/awk -f

        BEGIN { FS="[ =]"; ag=1000; tg=1000; }
    /artist=/ { a=$0; }
     /title=/ { t=$0; }
     /album=/ { al=$0; }
/ALBUM_GAIN=/ { ag=$2; }
/TRACK_GAIN=/ { tg=$2; }
       /----/ {
                if( tg<x )
                { 
                  print a; print t; print al;
                  printf("track gain: %s, album gain: %s\n", tg, ag);
                  print "---------";
                }
                a=""; t=""; al=""; ag=1000; tg=1000;
              }

```

```

**$ ./gain.awk -v x=-4 gain_test.txt **
artist=AAA
title=AAA
album=AAA
track gain: -5.51, album gain: -5.09
---------
artist=BBB
title=BBB
album=BBB
track gain: -6.31, album gain: -6.09
---------
artist=CCC
title=CCC
album=CCC
track gain: -7.09, album gain: -7.09
---------
artist=DDD
title=DDD
album=DDD
track gain: -8.09, album gain: -8.09
---------
artist=EEE
title=EEE
album=EEE
track gain: -18.09, album gain: -18.09
---------
**$ ./gain.awk -v x=-8 gain_test.txt **
artist=DDD
title=DDD
album=DDD
track gain: -8.09, album gain: -8.09
---------
artist=EEE
title=EEE
album=EEE
track gain: -18.09, album gain: -18.09
---------
[B]$ ./gain.awk -v x=-20 gain_test.txt 
$[/B]
```
in other words: works here

---

### Post by Singtoh on 2012-11-29
> **Vaphell said:**
> file with dummy data:
```
artist=AAA
album=AAA
title=AAA
REPLAYGAIN_ALBUM_GAIN=-5.09 dB
REPLAYGAIN_TRACK_GAIN=-5.51 dB
-----
artist=BBB
album=BBB
title=BBB
REPLAYGAIN_ALBUM_GAIN=-6.09 dB
REPLAYGAIN_TRACK_GAIN=-6.31 dB
-----
artist=CCC
album=CCC
title=CCC
REPLAYGAIN_ALBUM_GAIN=-7.09 dB
REPLAYGAIN_TRACK_GAIN=-7.09 dB
-----
artist=DDD
album=DDD
title=DDD
REPLAYGAIN_ALBUM_GAIN=-8.09 dB
REPLAYGAIN_TRACK_GAIN=-8.09 dB
-----
artist=EEE
album=EEE
title=EEE
REPLAYGAIN_ALBUM_GAIN=-18.09 dB
REPLAYGAIN_TRACK_GAIN=-18.09 dB
-----
```gain.awk
```
#!/usr/bin/awk -f

        BEGIN { FS="[ =]"; ag=1000; tg=1000; }
    /artist=/ { a=$0; }
     /title=/ { t=$0; }
     /album=/ { al=$0; }
/ALBUM_GAIN=/ { ag=$2; }
/TRACK_GAIN=/ { tg=$2; }
       /----/ {
                if( tg<x )
                { 
                  print a; print t; print al;
                  printf("track gain: %s, album gain: %s\n", tg, ag);
                  print "---------";
                }
                a=""; t=""; al=""; ag=1000; tg=1000;
              }

``````

**$ ./gain.awk -v x=-4 gain_test.txt **
artist=AAA
title=AAA
album=AAA
track gain: -5.51, album gain: -5.09
---------
artist=BBB
title=BBB
album=BBB
track gain: -6.31, album gain: -6.09
---------
artist=CCC
title=CCC
album=CCC
track gain: -7.09, album gain: -7.09
---------
artist=DDD
title=DDD
album=DDD
track gain: -8.09, album gain: -8.09
---------
artist=EEE
title=EEE
album=EEE
track gain: -18.09, album gain: -18.09
---------
**$ ./gain.awk -v x=-8 gain_test.txt **
artist=DDD
title=DDD
album=DDD
track gain: -8.09, album gain: -8.09
---------
artist=EEE
title=EEE
album=EEE
track gain: -18.09, album gain: -18.09
---------
[B]$ ./gain.awk -v x=-20 gain_test.txt 
$[/B]
```in other words: works here

Hello again Vaphell,

Ok, I'll give it another look and another try. If it works there with you then I must be fingering something up here. With that said if I can't get it to work this time I will try to find another way of doing it. I want to thank you so much for your efforts in trying to help me out. You have been very helpful and gracious with your time and code:)

Cheers Vaphell and all the best!

Singtoh

---

### Post by Vaphell on 2012-11-29
seriously, create a small file with few fake records (even 1 will do) with some made up numbers so you can run predictable tests. Debugging logic flaws with hundreds of records is not the way to go. Move to real data once you nail the tests.

modify BEGIN block so you can check if x is what you think it is, eg
```
BEGIN { FS="[ =]"; ag=1000; tg=1000; printf( "threshold: %s\n", x ); }
```
this will print x at the very top of the output.

Besides i have no idea what your code looks like now.
And for the love of god, don't quote 2 pages of text/code :/, if i want to see it again i can scroll up just fine

---

### Post by Singtoh on 2012-11-29
> **Vaphell said:**
> file with dummy data:
```
artist=AAA
album=AAA
title=AAA
REPLAYGAIN_ALBUM_GAIN=-5.09 dB
REPLAYGAIN_TRACK_GAIN=-5.51 dB
-----
artist=BBB
album=BBB
title=BBB
REPLAYGAIN_ALBUM_GAIN=-6.09 dB
REPLAYGAIN_TRACK_GAIN=-6.31 dB
-----
artist=CCC
album=CCC
title=CCC
REPLAYGAIN_ALBUM_GAIN=-7.09 dB
REPLAYGAIN_TRACK_GAIN=-7.09 dB
-----
artist=DDD
album=DDD
title=DDD
REPLAYGAIN_ALBUM_GAIN=-8.09 dB
REPLAYGAIN_TRACK_GAIN=-8.09 dB
-----
artist=EEE
album=EEE
title=EEE
REPLAYGAIN_ALBUM_GAIN=-18.09 dB
REPLAYGAIN_TRACK_GAIN=-18.09 dB
-----
```gain.awk
```
#!/usr/bin/awk -f

        BEGIN { FS="[ =]"; ag=1000; tg=1000; }
    /artist=/ { a=$0; }
     /title=/ { t=$0; }
     /album=/ { al=$0; }
/ALBUM_GAIN=/ { ag=$2; }
/TRACK_GAIN=/ { tg=$2; }
       /----/ {
                if( tg<x )
                { 
                  print a; print t; print al;
                  printf("track gain: %s, album gain: %s\n", tg, ag);
                  print "---------";
                }
                a=""; t=""; al=""; ag=1000; tg=1000;
              }

``````

**$ ./gain.awk -v x=-4 gain_test.txt **
artist=AAA
title=AAA
album=AAA
track gain: -5.51, album gain: -5.09
---------
artist=BBB
title=BBB
album=BBB
track gain: -6.31, album gain: -6.09
---------
artist=CCC
title=CCC
album=CCC
track gain: -7.09, album gain: -7.09
---------
artist=DDD
title=DDD
album=DDD
track gain: -8.09, album gain: -8.09
---------
artist=EEE
title=EEE
album=EEE
track gain: -18.09, album gain: -18.09
---------
**$ ./gain.awk -v x=-8 gain_test.txt **
artist=DDD
title=DDD
album=DDD
track gain: -8.09, album gain: -8.09
---------
artist=EEE
title=EEE
album=EEE
track gain: -18.09, album gain: -18.09
---------
[B]$ ./gain.awk -v x=-20 gain_test.txt 
$[/B]
```in other words: works here

Hello Vaphell,

Your code is perfect:P it is my fingers and brain that have the problem.:) Sorry, sometimes I try to do things too quickly and end up making a mess of things, but anyway your script is working wonderfully here and its very fast as well and outputs just like I need it to. I was fingering this part up:  if( tg<x ), I misunderstood what you told me to put there on the last post before:popcorn: So, it's all good now and I thank you profusely with great joy that this is working now:) Now I have the big job of processing all this music.:(

Cheers Vaphell and Thanks Again,

Singtoh

---

