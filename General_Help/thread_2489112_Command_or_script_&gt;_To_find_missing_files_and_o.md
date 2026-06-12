---
title: "Command or script &gt; To find missing files and output results to txt file &gt;"
date: 2023-07-18
forum: General Help
---

### Post by noobtechninja on 2023-07-18
Hi there guys.

I was hoping that you could help me with something please

I have a large media collection, stored on my NAS.
I use OSMC on a RasPi to display it on my TV

Using OSMC it requires an image file, (called - fanart.jpg) to display a background
image for each film in each directory

Most of my films do have this file / background image, however some directories
do not. I have hundreds to thousands of directories that require these images.

The naming structure is as follows -

NAS box -
Films > A > Name of films that begin with A
Films > B > Name of films that begin with B
All the way from A through to Z


What I'd like to do is -

1. Run a command or script that will search through all of my directories
on my NAS (film section) and see if the filename fanart.jpg exits.

2. If it doesn't exist, then output this to 1 text file, that also shows the
location of the directory with the missing filename.

So that I can easily find what I'm missing.


**Questions:**

1. How can I achieve this ?
2. What commands do I need to run in order to do this ?


TIA for any help or advice

---

### Post by TheFu on 2023-07-18
Looking for things that don't exist is hard.
To find fanart.jpg, use
```
$ find /where/the/media/files/are  -type f -iname fanart.jpg
```
Store that output into a file.

Now, get a list of all the directories .... 
```
$ find /where/the/media/files/are  -type d
```
Store that output into a file.

Using your favorite editor, edit the first file and remove "fanart.jpg" from each line.  Now you are left with 2 files. One has all the directories and the other has all the directories where fanart existed.  Perhaps using meld so the two files are side-by-side would show easily which were missing the image you want?

[https://stackoverflow.com/questions/17314523/unix-find-directory-with-missing-file](https://stackoverflow.com/questions/17314523/unix-find-directory-with-missing-file) has the commands.

There are 500 other solutions.  For example, you could create a little perl script that traverses the entire directory tree looking for "fanart.jpg", but if that file isn't located in a directory, create an empty file called "MISSING-fanart".  I think File::Find would be the module. Obviously, if you don't know perl, you'd want to choose a language you do know. Python, Ruby, Go can all do it, if you want to stay away from compiled languages.  Perl has a nice way of saying 
```
command if ( ! -f "$directories/fanart.jpg" );
```
So, if "command" is touch "MISSING-fanart", that would make getting the directory list pretty easy.

Then a command similar to the first 'find' could be used to know which were missing.

An other method would be to just create an empty "MISSING" file in all directories where there should be a fanart.jpg file.  Then create a list of directories with fanart.jpg, replace that with MISSING and feed that list into a **rm** command.  The directories with the MISSING file still there will be the ones without fanart.jpg.  You know, I like this method the best.

A quick test ...
```
mkdir -p A/Abra B/Beta C/Captain D/Deees  # create some test directories to practice inside.
touch D/Deees/fanart.jpg   # Need at least 1 directory with a "fanart.jpg" file
find [ABCD] -type d -exec touch {}/MISSING \;     # Put an empty "MISSING" file in all directories.   
# Oops, we got them in some that shouldn't have them, clean up:
rm [ABCD]/MISSING

```
This is what remains, 
```
$ find [ABCD]
A
A/Abra
A/Abra/MISSING
B
B/Beta
B/Beta/MISSING
C
C/Captain
C/Captain/MISSING
D
D/Deees
D/Deees/MISSING
D/Deees/fanart.jpg
```

Ok, there's just 1 directory with a fanart, all the others have a MISSING.  So, we need make a list of all the fanart.jpg locations, save that to a file, 
```
$ find [ABCD] -type f -iname fanart.jpg
D/Deees/fanart.jpg
```
Edit that file, replace **all** fanart.jpg in the file with MISSING, save it as tmp-file
Now, use **xargs** to feed the file contents into **rm**
```
$ xargs -a tmp-file rm 
$ find [ABCD]
A
A/Abra
A/Abra/MISSING
B
B/Beta
B/Beta/MISSING
C
C/Captain
C/Captain/MISSING
D
D/Deees
D/Deees/fanart.jpg
```
Note that the MISSING file is gone from d/Deees/?  Now you just need to look for directories with MISSING in them.

This last method is full of manual steps, but hopefully, it is easier to understand.  This solution pattern happens all the time, BTW.

---

### Post by Holger_Gehrke on 2023-07-19
And a quick one-liner that follows TheFu's first idea:
```

(find Films/{A..Z} -name 'fanart.jpg' -printf '%h\n'; find Films/{A..Z} -type d)|sort|uniq -u

```
The first 'find' searches for the 'fanart.jpg' files and prints just the directory. The second 'find' finds all the directories under Films/{A..Z}. Both finds are executed in a subshell so they can be piped both together. Sort them and then run uniq to only output the unique lines.

Holger

---

### Post by noobtechninja on 2023-07-19
Hi there @TheFu

Thanks very much for your detailed response

I espcially liked the link to the stack overflow link
(Thank you)

I've taken their script and modified it, and it "mostly" works

Here's my version

```
while read d
do
  [[ -r ${d}/fanart.jpg ]] || echo ${d}
done < <(find . -type d -print) > missing_files_results.txt
```


So this did work on my test dir, however it didn't work (properly) on my NAS and dirs
The reason being is that OSMC uses some basic folder structures for each film in each dir


As an example -

Fims > S > Star Wars Episode 4

Within the dir that contains the film Star Wars there are a couple of other dirs and items =
```
Star Wars Episode 4.mkv
fanart.jpg
folder.jpg
alt_thumbs (dir)
extrafanart (dir)
```

So when I run that command / script, it now shows every single dir (and the sub dirs)
that do not contian the filename - fanart.jpg

This essentially is every single dir on the NAS
So I'm back to square one.


What I need to do next (within the script) is to exclude any dirs with the following names =
alt_thumbs
extrafanart

I tried a couple of things =

```
while read d
do
  [[ -r ${d}/fanart.jpg ] **-type d -alt_thumbs -extrafanart]** || echo ${d}
done < <(find . -type d -print) > missing_files_results.txt
```


However the script then failed wit syntax errors

Do you have any further suggestions please ?

---

### Post by TheFu on 2023-07-19
```
egrep -v
``` will let you specify that only lines without the search regex should be shown/output.

Use explainshell.com to see what commands should do. ... Or just read the manpage.  Trying to do too much in 1 command is beginner mistake.  AFTER you get the commands correct, then you can try to get them into a 1-liner, not before.

---

### Post by MAFoElffen on 2023-07-19
LOL. Saw this early this morning, but had an appointment. Prepared a post,, and see many have similar ideas, as I had... 

Simply change to the base directory of where the other folders are sub-directories of and run this (tested & verified as working on my media server)
```

#!/bin/bash

dirs=$(find . -maxdepth 1 -type d | grep -v '/\.' | sed 's/[\.,\/]//g' | grep -v -e '^[[:space:]]*$' )

PWD=$(pwd)
filename="fanart.jpg"

for dir in ${dirs[@]}
do
   if [[ ! -f "$PWD/$dir/$filename" ]]
   then 
       echo -e "$PWD/$dir" >> ~/dir_list.log
   fi
done 

```

---

### Post by TheFu on 2023-07-19
MAFoElffen, nice script. Even I could understand it!

Because we have multiple rooms and devices where we may playback anything in the media center, while I use OSMC as the player, I don't use the DB it provides anymore.  Having a centralized DB, we use jellyfin here, lets the progress for different users be retained separately regardless of the device(s) used for playback. We often start watching a movie in the family room, but find we are too tired and stop it.  Then move to the bedroom and finish it (or fall asleep) watching it there.

The good news is that Plex, Jellyfin, OSMC, XBMC all follow substantially the same layouts, so if you setup for 1, switching to any other is a non-event, at least from the media storage perspective.

I've never done anything special about fan art, so this specific needs isn't something I've dealt with before.  I do use 1 directory per movie and for TV shows, go with the show_name/S1, S2, S3, S4 and S0 for specials method.

With jellyfin, it is 1 click to ask for all the metadata to be refreshed for any new or updated media files.  It is 3 clicks to flush all extra information and redownload it all.  Jellyfin will transcode media as needed for the client, that's a big deal, since we watch with very different clients, some with limited capabilities/performance. It is nice to have a Ryzen handling the transcoding, if it is needed.

---

### Post by MAFoElffen on 2023-07-19
> **TheFu said:**
> MAFoElffen, nice script. Even I could understand it!
Now you 'are' teasing me. LOL

Point taken. Same with annotated comments to explain what each section of it does.
```

#!/bin/bash
##
## MAF0Elffen, <mafoelffen.ubuntu.com, 2023.07.18
#  Purpose: Find media directories where file 'fanart.jpg' does not exist

## Creates a list array of directories at 1 level below the current directory, using 'find'
#  Uses grep to exclude hidden files (starting with .*).
#  Uses sed to remove "./" from the filename. This may cause blank lines.
#  Uses grep to remove any blank lines.
dirs=$(find . -maxdepth 1 -type d | grep -v '/\.' | sed 's/[\.,\/]//g' | grep -v -e '^[[:space:]]*$' )

PWD=$(pwd)  # Saves the current working directory of where the script was started from.
filename="fanart.jpg"  # The filename to work with.

for dir in ${dirs[@]} # Loop through the list, using a directory from that list of directories to test each, one at a time
do
   if [[ ! -f "$PWD/$dir/$filename" ]]  # If the directory does not contain that file, then work with it. 
   then 
       echo -e "$PWD/$dir" >> ~/dir_list.log  # Write the name of the directory to your log file.
   fi
done


```

---

### Post by The Cog on 2023-07-20
Aw, snap! I liked these, but they don't work it the films have spaces in their names. 
How about:
```
for f in $(ls -d {A..Z}/* 2>/dev/null) ; do [ -e "$f/fanart.jpg" ] || echo Missing: "$f/fanart.jpg" ; done
```
or quick and dirtier:
```
ls $(ls -d {A..Z}/*)/fanart.jpg > /dev/null
```

---

### Post by TheFu on 2023-07-20
There are many reasons NOT to allow spaces or special characters in filenames. This is one example. All media center software will remove '_' characters from their display of information automatically, so just use the "_" character instead of spaces.

```
rename 's/ /_/g' "$@";
```

is one way to rename lots of files, quickly.

---

