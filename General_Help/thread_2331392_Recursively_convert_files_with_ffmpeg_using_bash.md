---
title: "Recursively convert files with ffmpeg using bash?"
date: 2016-07-21
forum: General Help
---

### Post by madhartigan on 2016-07-21
I am unable to resurrect old posts (for very good reasons). 

[This](https://ubuntuforums.org/showthread.php?t=1545493) post from 2010 is essentially my exact question with some slight changes to the input and output folder/file locations.

Here is the text of the linked forum post (reformatted), for reference.  I have modified the details of the post so they apply to my specific parameters.  The quoted items are generic placeholders if that isn't immediately evident: (I recognize alac is lossless. "compressed" is the folder itunes watches for any compatible files and has mp3's in it, as well.)

> I have several large sets of .flac files that are all organized like so:

/home/storage/music/lossless/"Artist"/"Album"/"Song.flac"

I would like to convert these to alac's (.m4a) in order to play them on my iPhone. I have a script that will convert all the flac's in a folder to alac .m4a's and it looks like this:

```
for i in *.flac; do ffmpeg -i "$i" -acodec alac "`basename "$i" .flac`.m4a"; done;
```

The problem is that with my current file structure I have to run that command in the folder of every album, which would take a long time. 

What I would like to do is a write a script that would just run ffmpeg, recursively, in every folder found in /home/storage/music/lossless.  

Then, I'd like to append a script to move all the newly created alac's to another folder in a way that retains the current structure so I could end up with something like:

input = /home/storage/music/**lossless**/"Artist"/"Album"/"Song.flac" and output = /home/storage/music/**compressed**/"Artist"/"Album"/"Song.m4a"

Any suggestions/advice/feedback would be appreciated.

Thanks for your time,
Sohex


The final reply, with a solution, is as follows:

> [QUOTE="Originally Posted by Sohex"]
The converted m4a's show up in the directory containing Music and Music_too (or FLAC and ALAC if you will) instead of in the appropriate location, how can I fix that?
Sorry, my fault. The "basename" removes the directory part of the names.

Either replace "`basename "${i/Music/Music_too}" .flac`.m4a" with "`dirname ${i/Music/Music_too}"`/`basename "$i" .flac`.m4a" or edit $i in two steps using neither dirname nor basename, like o=${i/Music/Music_too}; o=${o%.flac%.m4a} and then use "$o" in the ffmpeg command.

```
for i in Music/*/*/*.flac; do o=${i/Music/Music_too}; o=${o%.flac%.mp4}; ffmpeg -i "$i" -acodec alac "$o"; done
```

Put an echo before the ffmpeg the first time you run the command to see what it will do:

```
for i in Music/*/*/*.flac; do o=${i/Music/Music_too}; o=${o%.flac%.mp4}; echo ffmpeg -i "$i" -acodec alac "$o"; done
```[/QUOTE]

I was able to figure out that for the beginning, I can substitute ```
for i in /home/storage/music/lossless/*/*/*.flac; 
``` My confusion lies with the parameters for the do function.  Specifically, the subsequent string variable.  I am unable to figure out how to properly substitute my parameters into this case and use the script suggested.

If possible, an additional step that checks the respective "compressed" folder for .m4a's already existing would aid in being able to reuse this single script each time I've added files to the "lossless" folder.  Perhaps, as a CRON job that is run nightly.  This is not a priority or needed at all, just a hopeful wish, if easily executed.

Any help would be greatly appreciated.

---

### Post by &amp;KyT$0P# on 2016-07-21
The solution for you probably involves [FONT=Courier New]find[/FONT] command, but I don't know exactly how it'd work.  Here's an example of how I might go about something like this, **NOT TESTED and it probably doesn't quite work how you want**
```
cd /home/storage/music/lossless
find . -iname \*.flac -exec foo.sh {} \;
```

foo.sh
```
#!/bin/bash

basedir='/home/storage/music/compressed'
dest=`dirname "$1"`

[ ! -d "$dest" ] && mkdir -p "$dest"

ffmpeg -i "$1" -acodec alac "${basedir}/$dest"/`basename "$1"`.m4a
```

I would strongly recommend you test and refine this on some dummy audio files until you're really sure it works exactly how you want, before setting this loose on anything important.

Refer to man page of find for more information

Does this help?

---

### Post by Keith_Helms on 2016-07-21
Try this:
```

inputdir="/home/storage/music/lossless/"
outputdir="/home/storage/music/compressed/"
while IFS= read -r file ; do
  song=`basename "$file"`
  dir=`dirname "$file"`
  varyingdir=${dir:${#inputdir}}
  songnotype=${song:0:${#song}-4}
  outputfile="${outputdir}${varyingdir}/${songnotype}m4a"
  # check if output file already exists
  if [ ! -e "$outputfile" ]
  then
    # check if output directory exists
    if [ ! -e "$outputdir/$varyingdir" ]
    then
      mkdir -p "$outputdir/$varyingdir"
    fi
    avconv -i "$file" -acodec alac "$outputfile"
  fi
done < <(find "$inputdir" -name "*.flac" | head -10)

```

ffmpeg was replaced by avconv at some point in Ubuntu, so change it back if you need to.  Remove the "| head -10" after testing.  That limits the loop to only process 10 files.

---

### Post by &amp;KyT$0P# on 2016-07-21
> **Keith_Helms said:**
> ffmpeg was replaced by avconv at some point in Ubuntu, 
Not any more
[http://packages.ubuntu.com/xenial/ffmpeg]("http://packages.ubuntu.com/xenial/ffmpeg")
[http://packages.ubuntu.com/xenial/libav-tools]("http://packages.ubuntu.com/xenial/libav-tools")

---

### Post by Keith_Helms on 2016-07-21
Ah.  Any news on which is better?  Are both being maintained?

---

### Post by &amp;KyT$0P# on 2016-07-22
That libav-tools package only contains symlinks to ffmpeg binaries & man pages, so someone who actually wants avconv & Co. will have to build from source.

---

### Post by madhartigan on 2016-07-22
> **Keith_Helms said:**
> Try this:
```

inputdir="/home/storage/music/lossless/"
outputdir="/home/storage/music/compressed/"
while IFS= read -r file ; do
  song=`basename "$file"`
  dir=`dirname "$file"`
  varyingdir=${dir:${#inputdir}}
  songnotype=${song:0:${#song}-4}
  outputfile="${outputdir}${varyingdir}/${songnotype}m4a"
  # check if output file already exists
  if [ ! -e "$outputfile" ]
  then
    # check if output directory exists
    if [ ! -e "$outputdir/$varyingdir" ]
    then
      mkdir -p "$outputdir/$varyingdir"
    fi
    avconv -i "$file" -acodec alac "$outputfile"
  fi
done < <(find "$inputdir" -name "*.flac" | head -10)

```

ffmpeg was replaced by avconv at some point in Ubuntu, so change it back if you need to.  Remove the "| head -10" after testing.  That limits the loop to only process 10 files.


Thank you very much for the replies!!  

I know this script *can* work, there are just some details that I've probably neglected to include that are tripping up the script.

This is very close.  I'm not sure how to explain what is going wrong, but I'll do my best.  If you suggest where I could put an echo statement, or have it output to a logfile, I could certainly copy that to Pastebin or share it from my cloud storage.

The only edit I made to the script was to change 'avconv' to 'ffmpeg'.  I used nano to create a file named "flactoalac" and pasted your script into that file.  Once it was edited with ffmpeg and saved, I did chmod 755 flactoalac so I could execute the file, then ran ./flactoalac

Once it completed, I checked the "compressed" folder.  

In the artist directory (/home/storage/music/compressed/"artist"), it had placed an empty directory with a partial string of the input directory's name.  In the album directory (/home/storage/music/compressed/"artist"/"album"/), there was a directory with the proper *full* string of the input directory's album title.  In that directory, there were three files properly converted to .m4a.

That was what happened the *first* time.  

I deleted all the output including the stray directory in the "artist" directory, the properly named album directory in the "album" directory and its contents.

I ran it again.  Same type of symptoms, different partial string left in the compressed "artist" directory and now an additional empty directory with the full input directory's name also in the "artist directory.  In the album directory, again, the proper *full* string of the input directory's album title with two (not three) properly converted files.

Similar symptoms, different specific results.


I apologize if that explanation is nearly impossible to understand.  The option for a logfile would probably help you pinpoint precisely what is going on.

I know nearly nothing about proper bash scripting, but I'm wondering if special characters or spaces in my album and song titles would possibly be the cause?  Both album and song titles contain spaces, commas, brackets or parentheses, and dashes (-).  I apologize for not including that detail in my original post.

I very much appreciate your effort and again, thank you very much for this effort.  I can understand the gist of what your script is doing, but attempting to debug would likely take me down a rabbit hole rather than fix anything.

Let me know what I can do to help you help me.

---

### Post by Keith_Helms on 2016-07-22
When you put it in "flattoalac" to make a script out of it, did you add the following line at the top of the file?
```
#!/bin/bash
```

If not, make that change and try again.

If you already had that in there, please list what was created by the script by running the following command
```
ls -R /home/storage/music/compressed
```
and posting the output.

---

### Post by Keith_Helms on 2016-07-22
By the way, what version of Ubuntu are you running?   Your profile shows 9.10.   You're not *really* on that old a version are you?  The bash code I posted should run on relatively recent Ubuntu releases, but I don't know about 7 year old ones.

---

### Post by madhartigan on 2016-07-22
I apologize for not updating my profile.  It's been that long since I have needed support.  Once I got my 10.04 LTS up and running, I was easily able to repeat the same steps to set up when upgrading to 12.04 LTS and 14.04 LTS. So, I had no real need for support outside of what I was able to search on Google. 

I'm now on 16.04 LTS.

I did *not* place that header at the top of the script.  Although, placing the hash bang header doesn't seem to have the effect of changing the output.

[http://pastebin.com/MnG1T91F](http://pastebin.com/MnG1T91F)

That will take you to the output you requested.  For the sake of demonstrating how it is not consistent I deleted those output folders and ran it again to show you how it changes.

[http://pastebin.com/sWdCfrx9](http://pastebin.com/sWdCfrx9)


Thank you for sticking with me and helping out.

---

### Post by Keith_Helms on 2016-07-22
Okay, I've determined the script "goes off the rails" if you actually  have a directory name ending in ".flac".  I also found a minor bug where  the script was generating a path with two consecutive slashes.  I don't  think that hurts, but I'm fixing that also.
```
inputdir="/home/storage/music/lossless/"
outputdir="/home/storage/music/compressed/"
while IFS= read -r file ; do
  song=`basename "$file"`
  dir=`dirname "$file"`
  varyingdir=${dir:${#inputdir}}
  songnotype=${song:0:${#song}-4}
  outputfile="${outputdir}${varyingdir}/${songnotype}m4a"
  # check if output file already exists
  if [ ! -e "$outputfile" ]
  then
    # check if output directory exists
    if [ ! -e "**$outputdir$varyingdir**" ]
    then
      mkdir -p "**$outputdir$varyingdir**"
    fi
    avconv -i "$file" -acodec alac "$outputfile"
  fi
done < <(find "$inputdir" **-type f** -name "*.flac" | head -10)

```

I've bolded the fixes.  The first two just remove an extra slash from the directory path being generated.  The third change adds a " -type f " qualifier to the find command so that it only selects regular files and not directory names.

---

### Post by madhartigan on 2016-07-22
I have made the changes you suggested and modified the command "avconv" to "ffmpeg".  

I'm not sure if there is a change in the output or not.  It's not doing what we're expecting, but it seems to possibly be getting further through the directory name?  I'm clueless.

[http://pastebin.com/CDN3uitH](http://pastebin.com/CDN3uitH)

For the sake of additional data sets, I deleted the directories that were created and ran it again.

[http://pastebin.com/2bahYu9G](http://pastebin.com/2bahYu9G)



For a third run, I set Putty to retain 5000000 lines of scrollback and I had it log the terminal's Printable output.

This is a link to the entire log: (it was too long for pastebin)



Hopefully that can assist you in diagnosing what might be going awry.

I'm probably wrong, but is there a possibility that passing the same "$file" string in lines 4 and 5 :

```
  song=`basename "$file"`
  dir=`dirname "$file"`
```

causing the error?  

Seems like that method would require both the dirname and the basename to be identical.  Which is not the case.  Is it possible that each should have a unique string variable?  Totally taking a shot in the dark.


I am very grateful for your help here.  Please don't view my suggestion as anything done in poor taste.

Thank you!!

---

### Post by mc4man on 2016-07-22
seems to skip a lot of tracks & create nonsense folders, attaching a log of simple test of last script with the head removed
2 folders of flac, 1 in sub folder
```
~/Music/flac$ ls -R -1A
rock
The Rolling Stones-Beggars Banquet

./rock:
Jimi Hendrix Experience-Electric Ladyland

./rock/Jimi Hendrix Experience-Electric Ladyland:
01.And the Gods Made Love.flac
02.Have You Ever Been (To Electric Ladyland).flac
03.Voodoo Chile.flac
04.Little Miss Strange.flac
05.Long Hot Summer Night.flac
06.Come On, Pt. 1.flac
07.Rainy Day, Dream Away.flac
08.1983... (A Merman I Should Turn to Be).flac
09.Moon, Turn the Tides...Gently Gently Away.flac
10.Still Raining, Still Dreaming.flac
11.House Burning Down.flac
Electric Ladyland.m3u

./The Rolling Stones-Beggars Banquet:
01.Sympathy For The Devil.flac
02.No Expectations.flac
03.Dear Doctor.flac
04.Parachute Woman.flac
05.Jig-Saw Puzzle.flac
06.Street Fighting Man.flac
07.Prodigal Son.flac
08.Stray Cat Blues.flac
09.Factory Girl.flac
10.Salt Of The Earth.flac
Beggars Banquet.m3u
```

What is produced - 
```
~/Music/compressed$ ls -R -1A
ck
e Rolling Stones-Beggars Banquet
rock
The Rolling Stones-Beggars Banquet

./ck:
Jimi Hendrix Experience-Electric Ladyland

./ck/Jimi Hendrix Experience-Electric Ladyland:

./e Rolling Stones-Beggars Banquet:

./rock:
Jimi Hendrix Experience-Electric Ladyland

./rock/Jimi Hendrix Experience-Electric Ladyland:
01.And the Gods Made Love.m4a
09.Moon, Turn the Tides...Gently Gently Away.m4a
11.House Burning Down.m4a

./The Rolling Stones-Beggars Banquet:
02.No Expectations.m4a
10.Salt Of The Earth.m4a
```

---

### Post by Keith_Helms on 2016-07-22
Time for a little debugging.  After the line that reads
```
outputfile="${outputdir}${varyingdir}/${songnotype}m4a"
```
Please add the following lines
```
echo "file: $file" >> ~/flactoalac.log
echo "song: $song" >> ~/flactoalac.log
echo "dir: $dir" >> ~/flactoalac.log
echo "varyingdir: $varyingdir" >> ~/flactoalac.log
echo "outputfile: $outputfile" >> ~/flactoalac.log
```

Post the flactoalac.log file and that should tell me where names are getting mangled.

---

### Post by madhartigan on 2016-07-22
Here ya go!

```
file: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d1_10_Party_Time.flac
song: ph160715d1_10_Party_Time.flac
dir: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: phish/2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-07-15 George, WA (FLAC)/ph160715d1_10_Party_Time.m4a
file: sic/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d1_13_Rift.flac
song: ph160715d1_13_Rift.flac
dir: sic/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir:  George, WA (FLAC)
outputfile: /home/storage/music/compressed/ George, WA (FLAC)/ph160715d1_13_Rift.m4a
file: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d3_05_Wilson.flac
song: ph160715d3_05_Wilson.flac
dir: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: phish/2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-07-15 George, WA (FLAC)/ph160715d3_05_Wilson.m4a
file: /storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d2_03_Whats_The_Use.flac
song: ph160715d2_03_Whats_The_Use.flac
dir: /storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: /2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed//2016-07-15 George, WA (FLAC)/ph160715d2_03_Whats_The_Use.m4a
file: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d1_05_Bouncing_Around_The_Room.flac
song: ph160715d1_05_Bouncing_Around_The_Room.flac
dir: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: phish/2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-07-15 George, WA (FLAC)/ph160715d1_05_Bouncing_Around_The_Room.m4a

```

---

### Post by madhartigan on 2016-07-22
. . . and the output after running it a second time (different result):

```
file: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d1_10_Party_Time.flac
song: ph160715d1_10_Party_Time.flac
dir: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: phish/2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-07-15 George, WA (FLAC)/ph160715d1_10_Party_Time.m4a
file: usic/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d1_13_Rift.flac
song: ph160715d1_13_Rift.flac
dir: usic/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: 5 George, WA (FLAC)
outputfile: /home/storage/music/compressed/5 George, WA (FLAC)/ph160715d1_13_Rift.m4a
file: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d3_05_Wilson.flac
song: ph160715d3_05_Wilson.flac
dir: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: phish/2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-07-15 George, WA (FLAC)/ph160715d3_05_Wilson.m4a
file: /music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d2_03_Whats_The_Use.flac
song: ph160715d2_03_Whats_The_Use.flac
dir: /music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: -15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/-15 George, WA (FLAC)/ph160715d2_03_Whats_The_Use.m4a
file: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d1_05_Bouncing_Around_The_Room.flac
song: ph160715d1_05_Bouncing_Around_The_Room.flac
dir: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: phish/2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-07-15 George, WA (FLAC)/ph160715d1_05_Bouncing_Around_The_Room.m4a
```

---

### Post by Keith_Helms on 2016-07-22
Looks like the handoff between find and read is not always working.  Give me a little while to research how to bulletproof those commands.  

I hate to say "it works for me", but I have 15,290 flac files with all sorts of special characters in the names and it looks like it handled the directory and file names properly.  :)  I didn't actually convert them, but I did run all the names through and logged the same info about variables you just provided.

---

### Post by Keith_Helms on 2016-07-22
Let's try this.  Change the first line to
```
while IFS= read -r -d $'\0' file ; do
```
and the last line to 
```
done < <(find "$inputdir" -type f -name '*.flac' -print0)
```

Leave the debug lines in and, if it still doesn't work, post the log file.

---

### Post by papibe on 2016-07-22
Hi madhartigan,

The variable 'file' is not being read correctly. I would assume there are some non graphic character in some of the filenames or dir names. I'd recommend using this structure to navigate the tree directory:
```
while **IFS=** read -r **-d ''** file
do
    # do something with file
    echo $file
done< <(find -type f -name '*.txt' **-print0**)

```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by madhartigan on 2016-07-22
Thank you both for your replies.

I'm seeing the suggestion from pabibe as being analogous to what Keith is suggesting.  

I am not sure how to incorporate the suggestion from pabibe, so I stuck with modifying flactoalac as Keith suggested.  Hopefully this output can provide both of you with useful information.


```
file: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)/ph160715d1_10_Party_Time.flac
song: ph160715d1_10_Party_Time.flac
dir: /home/storage/music/lossless/phish/2016-07-15 George, WA (FLAC)
varyingdir: phish/2016-07-15 George, WA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-07-15 George, WA (FLAC)/ph160715d1_10_Party_Time.m4a
file: flac
song: flac
dir: .
varyingdir: 
outputfile: /home/storage/music/compressed//m4a
file: /home/storage/music/lossless/phish/2016-06-22 St. Paul, MN (FLAC)/ph160622d1_08_Round_Room.flac
song: ph160622d1_08_Round_Room.flac
dir: /home/storage/music/lossless/phish/2016-06-22 St. Paul, MN (FLAC)
varyingdir: phish/2016-06-22 St. Paul, MN (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-06-22 St. Paul, MN (FLAC)/ph160622d1_08_Round_Room.m4a
file: A (FLAC)/ph160629d2_01_Crosseyed_And_Painless.flac
song: ph160629d2_01_Crosseyed_And_Painless.flac
dir: A (FLAC)
varyingdir: 
outputfile: /home/storage/music/compressed//ph160629d2_01_Crosseyed_And_Painless.m4a
file: /home/storage/music/lossless/phish/2016-06-29 Philadelphia, PA (FLAC)/ph160629d2_08_Backwards_Down_The_Number_Line.flac
song: ph160629d2_08_Backwards_Down_The_Number_Line.flac
dir: /home/storage/music/lossless/phish/2016-06-29 Philadelphia, PA (FLAC)
varyingdir: phish/2016-06-29 Philadelphia, PA (FLAC)
outputfile: /home/storage/music/compressed/phish/2016-06-29 Philadelphia, PA (FLAC)/ph160629d2_08_Backwards_Down_The_Number_Line.m4a
file: Hartford, CT [FLAC]/ph160709d2_03_Sand.flac
song: ph160709d2_03_Sand.flac
dir: Hartford, CT [FLAC]
varyingdir: 
outputfile: /home/storage/music/compressed//ph160709d2_03_Sand.m4a
file: /home/storage/music/lossless/phish/2016-07-09 Xfinity Theatre, Hartford, CT [FLAC]/ph160709d1_07_Let_Me_Lie.flac
song: ph160709d1_07_Let_Me_Lie.flac
dir: /home/storage/music/lossless/phish/2016-07-09 Xfinity Theatre, Hartford, CT [FLAC]
varyingdir: phish/2016-07-09 Xfinity Theatre, Hartford, CT [FLAC]
outputfile: /home/storage/music/compressed/phish/2016-07-09 Xfinity Theatre, Hartford, CT [FLAC]/ph160709d1_07_Let_Me_Lie.m4a
file: Bill Graham Civic Auditorium, San Fransisco, CA [FLAC]/ph160718d2_04_My_Sweet_One.flac
song: ph160718d2_04_My_Sweet_One.flac
dir: Bill Graham Civic Auditorium, San Fransisco, CA [FLAC]
varyingdir:  San Fransisco, CA [FLAC]
outputfile: /home/storage/music/compressed/ San Fransisco, CA [FLAC]/ph160718d2_04_My_Sweet_One.m4a
file: /home/storage/music/lossless/phish/2016-07-18 Bill Graham Civic Auditorium, San Fransisco, CA [FLAC]/ph160718d1_02_Halleys_Comet.flac
song: ph160718d1_02_Halleys_Comet.flac
dir: /home/storage/music/lossless/phish/2016-07-18 Bill Graham Civic Auditorium, San Fransisco, CA [FLAC]
varyingdir: phish/2016-07-18 Bill Graham Civic Auditorium, San Fransisco, CA [FLAC]
outputfile: /home/storage/music/compressed/phish/2016-07-18 Bill Graham Civic Auditorium, San Fransisco, CA [FLAC]/ph160718d1_02_Halleys_Comet.m4a
```


Once the script got to that last file, it hanged and left me with the following:

```
Enter command: <target>|all <time>|-1 <command>[ <argument>]
^Z
[3]+  Stopped                 ./flactoalac

```

I pressed "Break" to get back to the command prompt.

So you can verify I modified the script properly:

```
darryl@helios:~$ cat flactoalac
#!/bin/bash

inputdir="/home/storage/music/lossless/"
outputdir="/home/storage/music/compressed/"
while IFS= read -r -d $'\0' file ; do
  song=`basename "$file"`
  dir=`dirname "$file"`
  varyingdir=${dir:${#inputdir}}
  songnotype=${song:0:${#song}-4}
  outputfile="${outputdir}${varyingdir}/${songnotype}m4a"
  echo "file: $file" >> ~/flactoalac.log
  echo "song: $song" >> ~/flactoalac.log
  echo "dir: $dir" >> ~/flactoalac.log
  echo "varyingdir: $varyingdir" >> ~/flactoalac.log
  echo "outputfile: $outputfile" >> ~/flactoalac.log
  # check if output file already exists
  if [ ! -e "$outputfile" ]
  then
    # check if output directory exists
    if [ ! -e "$outputdir$varyingdir" ]
    then
      mkdir -p "$outputdir$varyingdir"
    fi
    ffmpeg -i "$file" -acodec alac "$outputfile"
  fi
done < <(find "$inputdir" -type f -name '*.flac' -print0)
darryl@helios:~$
```



Thank you both, very much, for your time and suggestions.

---

### Post by madhartigan on 2016-07-22
I doubt it has any significance, but just in case, I'm using the server edition of 16.04 LTS.  It's a headless server I connect to using KiTTY from my Windows 10 machine.




In case this helps, here is the output of 'ls -R /home/storage/music/lossless'

[http://pastebin.com/TjxvksL7](http://pastebin.com/TjxvksL7)

Thought it might be helpful to see the contents of that directory so you knew what input was being read.


The mention of non graphic characters also led me to test some of the potential culprits.  When I type ' (' into the command prompt and press ENTER, it drops into a different mode.  

```
darryl@helios:~$  (
> ^C
darryl@helios:~$
```


I don't know what else to call it, but I do know that some of my directory names definitely have a space preceding a parentheses.

Any chance that has anything to do with it?

Apologies if it's completely irrelevant.

---

### Post by mc4man on 2016-07-22
Fixed the script here by adding < /dev/null to front of ffmpeg encoding line, (was using previous script, ie the one that ends in
done < <(find "$inputdir" -name "*.flac" ) as hadn't seen final redo..
```
     < /dev/null ffmpeg -i "$file" -acodec alac "$outputfile"
```
Also to note that here (Desktop install), did not use full path in script for inputdir= & outputdir=" , eliminated behind the prompt so for example outputdir="Music/alac1"

---

### Post by mc4man on 2016-07-22
> **mc4man said:**
> Fixed the script here by adding < /dev/null to front of ffmpeg encoding line, 
For reference, ect - [http://mywiki.wooledge.org/BashFAQ/089](http://mywiki.wooledge.org/BashFAQ/089)

---

### Post by papibe on 2016-07-22
> **mc4man said:**
> For reference, ect - [http://mywiki.wooledge.org/BashFAQ/089](http://mywiki.wooledge.org/BashFAQ/089)
good one!

---

### Post by Keith_Helms on 2016-07-22
Interesting.  Looking at the log you provided it appears that every OTHER file has what looks like correct values for the variables.  I expect that's a big clue, but I don't know what it tells me.

---

### Post by Keith_Helms on 2016-07-22
> **mc4man said:**
> Fixed the script here by adding < /dev/null to front of ffmpeg encoding line, (was using previous script, ie the one that ends in
done < <(find "$inputdir" -name "*.flac" ) as hadn't seen final redo..
```
     < /dev/null ffmpeg -i "$file" -acodec alac "$outputfile"
```
Also to note that here (Desktop install), did not use full path in script for inputdir= & outputdir=" , eliminated behind the prompt so for example outputdir="Music/alac1"

By fixed the script, do you mean it works correctly with the </dev/null and does not create "garbage" directory names?

Dang, I had no idea ffmpeg was trying to read from stdin.

Now that I've thought about it for a few minutes, it explains what the script was doing.  The loop read in a line and split it out in the desired variables, then the ffmpeg command "ate" up part of the following line and the next iteration of the loop was left with only a partial path and filename.  Repeat over and over.

I was sure it was some kind of special character that was hosing things, so I was concentrating on trying to bulletproof the find and read commands.

Well, you learn something every day (if you can't avoid it). :o

---

### Post by mc4man on 2016-07-22
> **Keith_Helms said:**
> By fixed the script, do you mean it works correctly with the </dev/null and does not create "garbage" directory names?

Dang, I had no idea ffmpeg was trying to read from stdin.

Yeah, works perfectly, zips right along from file to file.

When using the 2nd posted script with full paths for input & output on the couple of tracks ffmpeg would actually encode I'd say the terminal output was 10000 -15000 lines per track! It was like ffmpeg was giving a complete 'analysis' of the file including all this hex stuff at the end. Never seen that before. For some reason shortening the path at least allowed seeing the constant error about "Parse error, at least 3 arguments were expected, only 1 given .."  on all the failed files. It always got the first one correct, then started failing, then maybe another correct after some fails, ect.

Whether the </dev/null should be in front or at end or doesn't matter haven't tried, works fine in front. I figured the issue started on 2nd iteration so maybe in front?

---

### Post by madhartigan on 2016-07-23
Thank you to everyone for the collaborative effort.  This is working as stated . . . Perfectly.

For those who are following along or come after, here is the full, working script in case it's not immediately clear what edits are necessary: (echo statements can be removed if you're not interested in logging)

```
#!/bin/bash

inputdir="/home/storage/music/lossless/"
outputdir="/home/storage/music/compressed/"
while IFS= read -r file ; do
  song=`basename "$file"`
  dir=`dirname "$file"`
  varyingdir=${dir:${#inputdir}}
  songnotype=${song:0:${#song}-4}
  outputfile="${outputdir}${varyingdir}/${songnotype}m4a"
  echo "file: $file" >> ~/flactoalac.log
  echo "song: $song" >> ~/flactoalac.log
  echo "dir: $dir" >> ~/flactoalac.log
  echo "varyingdir: $varyingdir" >> ~/flactoalac.log
  echo "outputfile: $outputfile" >> ~/flactoalac.log
  # check if output file already exists
  if [ ! -e "$outputfile" ]
  then
    # check if output directory exists
    if [ ! -e "$outputdir/$varyingdir" ]
    then
      mkdir -p "$outputdir/$varyingdir"
    fi
    < /dev/null ffmpeg -i "$file" -acodec alac "$outputfile"
  fi
done < <(find "$inputdir" -name "*.flac")
```

The only modifications necessary for it to work in specific instances would be changing lines 3 and 4 (inputdir= and outputdir=) to the appropriate input and output directories. Assuming the rest of the structure is the common ../"artist"/"album"/"songname.flac"


This is fantastic.  Thank you so much Keith_Helms, pabibe and with the RBI to win the game -> mc4man.

---

### Post by Keith_Helms on 2016-07-23
I'll add a little info on using paths in the script.  Setting inputdir and outputdir to absolute paths instead of relative lets you run the command from any directory.  You can also set them to relative paths and run the script when in the parent directory for that path.  The variables are just "starting points" for processing all flac files below that point.  

The only thing the script expects below the specified paths is one or more additional directory levels.  If you just want to process a single directory containing flac files you could cd to the parent directory and set inputdir to **"./"**.  If you wanted the output .alac files in the same directory as the input .flac files, you could set the two variables to be the same.

---

### Post by mc4man on 2016-07-23
as far as the echo's,  if wanting to log I'd find one showing what ffmpeg did more useful. Many way's, I use 
command 2>&1 | tee log file
or 2>&1 | tee -a   when desiring to append
ex.
flac2alac2 2>&1 | tee -a  ~/encode.log

---

### Post by Bedlore on 2017-01-24
I created a script closely based on this one and came across a handling issue. If a directory name (album or artist) contains a period (full stop) anywhere than the script fails due to been one level lower than it should.  I've not resolved the problem so would love to hear from anyone that fixed this issue.
 - Thanks

---

### Post by Keith_Helms on 2017-01-24
> **Bedlore said:**
> I created a script closely based on this one and came across a handling issue. If a directory name (album or artist) contains a period (full stop) anywhere than the script fails due to been one level lower than it should.  I've not resolved the problem so would love to hear from anyone that fixed this issue.
 - Thanks

Try adding a couple of tweaks to handle paths with special characters in them better.  The 2 lines changed delimit file names with a null character instead of whitespace which should solve your period problem.

```
#!/bin/bash

inputdir="/home/storage/music/lossless/"
outputdir="/home/storage/music/compressed/"
while IFS= read **-r -d $'\0'** file ; do
  song=`basename "$file"`
  dir=`dirname "$file"`
  varyingdir=${dir:${#inputdir}}
  songnotype=${song:0:${#song}-4}
  outputfile="${outputdir}${varyingdir}/${songnotype}m4a"
  echo "file: $file" >> ~/flactoalac.log
  echo "song: $song" >> ~/flactoalac.log
  echo "dir: $dir" >> ~/flactoalac.log
  echo "varyingdir: $varyingdir" >> ~/flactoalac.log
  echo "outputfile: $outputfile" >> ~/flactoalac.log
  # check if output file already exists
  if [ ! -e "$outputfile" ]
  then
    # check if output directory exists
    if [ ! -e "$outputdir/$varyingdir" ]
    then
      mkdir -p "$outputdir/$varyingdir"
    fi
    < /dev/null ffmpeg -i "$file" -acodec alac "$outputfile"
  fi
done < <(find "$inputdir" -name "*.flac" **-print0**)


```

---

### Post by Bedlore on 2017-01-24
Hi Keith

Thanks for you input, it didn't resolve my issues though which I'm starting to think are not just related to periods but also non ascii characters.  This is my script, perhaps others can use bits of it.   As you'll see my script is less about the conversion as I do this upstream of the script, rather it performs some validation, copy and consolidation of albums.  Specifically, its designed to work with albums found in /mnt/Audio/Pre-Staging/ and then copy them to /mnt/Audio/Lossless/, make some minor tweaks them move them to /mnt/Staging/. I know its a bit convoluted but there is some method in my madness.

 I also realise its a bit of a mess, I'm not that good at scripting so if you can suggest improvements I would be most appreciative.  But the main issue is still the period and special character handling.  Here is a specific example; assume I have this album here "/mnt/Audio/Pre-Staging/Björk/Vespertine 5.1/01 Hidden Place.flac".  I will encounter this error: cp: omitting directory '/mnt/Audio/Pre-Staging/Björk/Vespertine 5.1' but if I rename the album to cp: omitting directory Vespertine 5_1 it will work.

```

#!/bin/bash
set -o errexit
set -u

echo "---= Running from within a screen session is highly recommended =---"
echo "Please type yes to continue"
read answer

if [ $answer = 'yes' ]
   then echo "Okay, lets roll!"
    rm /mnt/Audio/PushToLive.log
    touch /mnt/Audio/PushToLive.log
    logfile="/mnt/Audio/PushToLive.log"
    rm /mnt/Audio/NewAlbums.log
    touch /mnt/Audio/NewAlbums.log
    newalbums="/mnt/Audio/NewAlbums.log"
    inputdir="/mnt/Audio/Pre-Staging/"
    outputdir="/mnt/Audio/Lossless/"
    stagingdir="/mnt/Staging/"
    copystatus=good
    shopt -s nocasematch

    while IFS= read -r -d $'\0' file ; do
      song=$(basename "$file");
      dir=$(dirname "$file");
      varyingdir=${dir:${#inputdir}};
      songnotype=${song:0:${#song}};
      outputfile="${outputdir}${varyingdir}/${songnotype}";
      accuripcount="$varyingdir";

      # Run a trackverify over each album and write and record the results into the album directory
      if [ ! -e "$dir/AccuripResult.log" ] ; then
        { trackverify -j 3 -R "$dir/"  || true ; } > "$dir/AccuripResult.log"
      fi

      # Build a listing of new albums
      if grep "$varyingdir" $newalbums
      then
          echo "Already listed in the NewAblums log"
        else
          echo "Album: $varyingdir" >> $newalbums
      fi

      # check if artist already exists in the Lossless directory
      # (reminder.. this needs improving a lot, it needs to detect closely named files,
      #  or even just the first two numerals (track number) in the same directory would be better.
      # similarly existing artist name detection in both Lossless and Pre-Staging)
      if [ -e "$outputfile" ] ; then
          echo "File already existed: $file"
          echo "File already existed: $file" >> $logfile
      else
          # check if album already exists, if not create the directories
          if [ ! -e "$outputdir/$varyingdir" ] ; then
              mkdir -p "$outputdir/$varyingdir"
          fi

          # move the albums
          < /dev/null cp -n "$file" "$outputfile" && (exit 0) || (c=$?; (exit $c))

          # Check if the copy succeeded and if so remove some specific SORT meta tags
          if [ $? == 0 ] && [ ${file: -5} == ".flac" ] ; then
              < /dev/null lltag --quiet --quiet --quiet --yes -T --tag ARTISTSORT= --tag ALBUMARTISTSORT= "$file"
          elif [ ${file: -5} == ".flac" ] ; then
              echo "Something went wrong when copying: $file"
              echo "Something went wrong when copying: $file" >> $logfile
              copystatus=bad
          fi
    fi
    done < <(find "$inputdir" -name "*.*" -print0)

    if [ $copystatus == good ] ; then
        echo "Copy is reported as $copystatus, continuing..."

        # (reminder: this mv really needs improving, it fails if the artist already exists in Staging even if the album does not!)
        mv "$inputdir"* "$stagingdir" && (echo "Moved to Staging OK"; exit 0) || (c=$?; echo "Something went wrong while moving to STAGING!"; (exit $c))
            if [ $? == 0 ] ; then
                echo "All files moved successfully to Staging"
                # (Reminder: add GB du -sh waiting in Staging to outgoing email)
                mail -s "New Albums - $(date '+%e %b %Y')" me@here.com < $newalbums
            fi
    else
        echo "The copy status was $copystatus, shutting down - please inspect manually"
        break
    fi

elif [ $answer = 'no' ] ; then
    echo "Exiting now"
    else echo "No comprehendo, existing"
fi

```

---

### Post by Keith_Helms on 2017-01-25
I believe your problem is this line
```
done < <(find "$inputdir" -name "*.*" -print0)
```

Your script assumes what is coming back from the find command is the path down to a song, but -name "*.*" will also return a directory name containing a period.  For example you are assuming you will always get back something like
**/mnt/Audio/Pre-Staging/Björk/Vespertine 5.1/01 Hidden Place.flac**
but the find command as coded will also return
**/mnt/Audio/Pre-Staging/Björk/Vespertine 5.1**
which will not work with the rest of the logic in the loop.

I'd change the find command to either explicitly look for flac files
```
-name "*.flac"
```
Or, you can get fancy and look for any in a list of audio file types
```
-regextype sed -regex ".*\.\(mp3\|flac\|wav\|ogg\|aac\)"
```
Or, just look for regular files and exclude directories
```
-type f
```

---

### Post by Bedlore on 2017-01-25
Brilliant Keith, you were correct, thanks heaps :)

If I need help refining my script further should I start a new thread rather than hijack this one?

---

### Post by vasa1 on 2017-01-25
> **Bedlore said:**
> Brilliant Keith, you were correct, thanks heaps :)

If I need help refining my script further should I start a new thread rather than hijack this one?

Just start a new thread. There's no extra charge :)

---

