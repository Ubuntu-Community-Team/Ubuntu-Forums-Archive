---
title: "I need a file name changing script after ipod converted"
date: 2007-09-02
forum: General Help
---

### Post by CameronCalver on 2007-09-02
Hello i had about 4500 songs on my ipod right and i backed all the songs up on linux by just copying the directory into a folder and the file structure was like
music/ f1 and /f2 and /f3 ... up to like f49 and inside each there was like 100 or so songs and all the song names were like  
```
xbcs.m4a yqhs.m4a
```  just random 4 digit codes and then .m4a  so i got a converting script to convert them to .mp3. 
When i use these songs with things like amarok, rythmbox they have the right tags like name album etc but that is useless if i need to send them to people or burn them to a cd because i don't no which song is which.
So can someone help me would there be a simple filename renaming script that gets the artist-song name from the tag and writes it to the filename.
Thanks for your help
,Cameron

---

### Post by lloyd_b on 2007-09-02
> **CameronCalver said:**
> Hello i had about 4500 songs on my ipod right and i backed all the songs up on linux by just copying the directory into a folder and the file structure was like
music/ f1 and /f2 and /f3 ... up to like f49 and inside each there was like 100 or so songs and all the song names were like  
```
xbcs.m4a yqhs.m4a
```  just random 4 digit codes and then .m4a  so i got a converting script to convert them to .mp3. 
When i use these songs with things like amarok, rythmbox they have the right tags like name album etc but that is useless if i need to send them to people or burn them to a cd because i don't no which song is which.
So can someone help me would there be a simple filename renaming script that gets the artist-song name from the tag and writes it to the filename.
Thanks for your help
,Cameron
 
You'll need to install the package "mp3info" in order for this to work
```
sudo apt-get install mp3info
```
in a terminal window, or use Synaptic/Adept/whatever program to install it

Here's the script.  Run it while in the top-level directory for your music.  It will rename all mp3 files in that directory or in any subdirectory to "Artist-Title.mp3" (converting any spaces to underscores).
```
#!/bin/bash

# Get a list of mp3 files
FILES=`find . -name *.mp3 -print`

# Loop through the list
for CURFILE in $FILES; do
     # Pull Artist and Title from the ID3 tags, separating them with a "|" character
     ID3INFO=`mp3info -p "%a|%t" $CURFILE`

     # Convert any spaces to underscores
     ID3INFO=`echo $ID3INFO | tr ' ' '_'`

     # Pull out the artist's name
     ARTIST=`echo $ID3INFO | cut -d '|' -f 1`

     # Pull out the song title
     TITLE=`echo $ID3INFO | cut -d '|' -f 2`

     # Identify which directory the file is in
     DNAME=`dirname $CURFILE`

     # Build the new file name, with full path
     NEWNAME="$DNAME/$ARTIST-$TITLE.mp3"

     # Rename the file
     mv "$CURFILE" "$NEWNAME"

done
```

Note: I haven't actually tested the script.  Your mileage may vary...

Lloyd B.

---

### Post by CameronCalver on 2007-09-02
Heya thanks for quick reply i got this
```
cameron@calver:~/music&video/music/ipod$ ./mp3-naming
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]

```
to get this right .... /music/ipod has all the music in it and i put mp3-naming in /music/ipod that right ? so what next to get it to work?

---

### Post by cwaldbieser on 2007-09-02
```
#!/bin/bash
# Get a list of mp3 files
FILES=`find . -name *.mp3 -print`

```

I think this line needs the *.mp3 pattern to be quoted, or else the shell will try to expand it (you want the find command to interpret the pattern).

---

### Post by lloyd_b on 2007-09-02
> **CameronCalver said:**
> Heya thanks for quick reply i got this
```
cameron@calver:~/music&video/music/ipod$ ./mp3-naming
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]

```
to get this right .... /music/ipod has all the music in it and i put mp3-naming in /music/ipod that right ? so what next to get it to work?

Hmmm.  The above poster has a point - try changing the "FILES=..." line to:
```
**[SIZE="3"]FILES=`find . -name "*.mp3" -print`[/SIZE]**
```
The original works fine, as long as there are no mp3 files in the current directory.  But if there *are* any mp3 files in the current directory, then it can go wacky as a result of shell expansion.

Other than that, the only thing I can think of that would cause that particular error would be a typo of some sort on that line (that's why in the example above I expanded and bolded the text - to make it more readable).

If you still have that same problem after that, could you run that "find..." command on the command line, and post the results?

Lloyd B.

---

### Post by soxs on 2007-09-02
You could simply use floola and extract them from your iPod to your sdx/hdx, it should convert them aswell (not 100% sure)... [www.floola.com](www.floola.com) (Note: I do all my iPod stuff with floola)

---

### Post by CameronCalver on 2007-09-04
Um ok it did these ones
```
tat `MIXES!!/CQEU.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory
Error opening MP3: MIXES!!/IHDK.mp3: No such file or directory
mv: cannot stat `MIXES!!/IHDK.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory
Error opening MP3: MIXES!!/ZVVM.mp3: No such file or directory
mv: cannot stat `MIXES!!/ZVVM.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory
Error opening MP3: MIXES!!/MTQQ.mp3: No such file or directory
mv: cannot stat `MIXES!!/MTQQ.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory

```

its looking for them in ./music&video/music/MORE they are in 
cameron@calver:~$ '/home/cameron/music&video/music/ipod/'

---

### Post by lloyd_b on 2007-09-04
> **CameronCalver said:**
> Um ok it did these ones
```
tat `MIXES!!/CQEU.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory
Error opening MP3: MIXES!!/IHDK.mp3: No such file or directory
mv: cannot stat `MIXES!!/IHDK.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory
Error opening MP3: MIXES!!/ZVVM.mp3: No such file or directory
mv: cannot stat `MIXES!!/ZVVM.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory
Error opening MP3: MIXES!!/MTQQ.mp3: No such file or directory
mv: cannot stat `MIXES!!/MTQQ.mp3': No such file or directory
Error opening MP3: ./music&video/music/MORE: No such file or directory
mv: cannot stat `./music&video/music/MORE': No such file or directory

```

its looking for them in ./music&video/music/MORE they are in 
cameron@calver:~$ '/home/cameron/music&video/music/ipod/'

Take a closer look at your directories.  You apparently have a directory named "/home/cameron/music&video/music/MORE MIXES!!", which does contain some mp3 files.  The problem is that the space in that directory name causes the script's looping mechanism to go flaky.

I know of one way to compensate for this.  Add a line, right after the "#!/bin/bash":
```
IFS="|""
```
(Note: "|" is the "pipe symbol", <shift><backslash> on US keyboards)

Then, modify the "FILES=" line:
```
FILES=`find . -name "*.mp3" -printf "%p|"`
```

This will prevent that problem, unless one of your files or directories has that pipe symbol as part of it's name...

Lloyd B.

---

### Post by CameronCalver on 2007-09-05
yeh thanks everyone that helped me all is good 

[COLOR="Red"]({Problem Solved })[/COLOR]

---

