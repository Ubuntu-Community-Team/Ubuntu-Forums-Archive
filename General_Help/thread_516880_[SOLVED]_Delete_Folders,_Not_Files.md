---
title: "[SOLVED] Delete Folders, Not Files"
date: 2007-08-03
forum: General Help
---

### Post by lightnb on 2007-08-03
Is there an easy way to delete all the folders in a certain directory, but not the files at any level within those folders?

ie. take all the files under a directory and extract them, then remove the folders?

I have a music library that's an absolute mess, and I would like to pull all files into one top level folder and delete all subfolders.

---

### Post by scrooge_74 on 2007-08-03
first copy the files out then delete the folders

you can do it from Nautilus or from the command line 

you can type cp /folder_name/*.mp3 /home/user/new_destination/

then when you are sure you move everything you can just rm -r /home/user_name/your_music_folder

just be carefull not to delete any other folders :)

---

### Post by nick_h on 2007-08-03
I also suggest that you create a new directory and copy all the files into it first.  Then you can delete the old directory structure when you are ready.  Take a backup first.

find with the -exec option is useful for such a copy, for example:
```
find ~/old_dir -type f -exec cp '{}' ~/new_dir \;
```

---

### Post by lightnb on 2007-08-03
Thanks.... I'm having some difficulty though, probably due to spaces in folder names.
 
What's the correct way to deal with that?

I've tried:
"/path/with spaces/*.*"
"/path/with spaces/"*.*
'/path/with spaces/'*.*
`/path/with spaces/*.*`

and other variations with no luck. it says: "cp: cannot stat".

---

### Post by avik on 2007-08-03
You escape spaces with a backslash:

```
"/path/with\ spaces/*.*"
```

---

### Post by aysiu on 2007-08-03
I would do a search through the GUI and highlight all the search results, and cut and paste them into a new folder, delete all the folders and rename the new folder.

---

### Post by machoo02 on 2007-08-03
I would do a recursive copy of your folder that contains all of the .mp3 files
```
cp -r /path/to/oldmusicdirectory/toplevel/*.mp3 /new/music/directory
rm -r /path/to/oldmusicdirectory/toplevel
```

---

### Post by lightnb on 2007-08-04
The adventure continues....

Thanks everyone. I'm trying the last option:

cp -r /files/TrueFiles/Temp\ Music\ and\ Pictures/iTunes\ Music/*.*  /files/TrueFiles/Temp\ Music\ and\ Pictures/iTunes\ Music/

And getting the error: "cp: [file-path and name] are the same file"

I'm guessing I have different copies of a file with the same name... Is there an intelligent way to skip or delete these files? Can it look at the actual data and see if the files are identical (and not just identical names) and delete true duplicates?

---

### Post by aysiu on 2007-08-04
Try my method then.

---

### Post by lightnb on 2007-08-04
> **aysiu said:**
> Try my method then.

Is there any way to 'cut' from the search results? It only gives me 'copy' and 'delete' as options...

---

### Post by lightnb on 2007-08-06
The closest I've gotten so far is:

> mv /files/TrueFiles/TempMusicandPictures/iTunesMusic/* /mus/AUDIO/All/

I've read through the man pages for mv, but couldn't find an option to ignore/exclude folders.

---

### Post by aysiu on 2007-08-06
> **lightnb said:**
> Is there any way to 'cut' from the search results? It only gives me 'copy' and 'delete' as options...
There should be a way to cut. I've done it in the past. Have you tried Control-X?

If not, you can copy the first half, delete the first half, copy the second half, and then delete the second half.

Or, if you're really hard-up for hard drive space, you can divvy it up into fifths instead of halves.

---

### Post by lightnb on 2007-08-06
Ok- Figured it out...

Apparently, "K Menu > Find Files/Folders" only allows copy and delete, whereas "Konqueror > CTRL + F " allows all options that Konqueror can perform.

I guess it's another one of those Linux inconsistencies that show up from time to time... (Still better than Microshaft though)

Thanks for your help! :)

---

### Post by aysiu on 2007-08-06
> **lightnb said:**
> Ok- Figured it out...

Apparently, "K Menu > Find Files/Folders" only allows copy and delete, whereas "Konqueror > CTRL + F " allows all options that Konqueror can perform.

I guess it's another one of those Linux inconsistencies that show up from time to time... (Still better than Microshaft though)

Thanks for your help! :)
That's great that you figured it out.

Perhaps you should file a bug report on this inconsistency, though:
[http://bugs.kde.org/](http://bugs.kde.org/)

---

