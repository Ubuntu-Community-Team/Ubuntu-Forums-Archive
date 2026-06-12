---
title: "Help with ls from the command line"
date: 2006-11-25
forum: General Help
---

### Post by digilink on 2006-11-25
I have a very frustrating problem that I can't seem to get around, and it's probably a serious PEBKAC lol. 

I have made an iTunes backup folder on a seperate harddrive in my computer and I want to seperate the MP3's from the encrypted iTunes songs. They are all arranged by artist in their own directory, but I don't know which songs are encrypted and which ones aren't.

I tried the following:
```

sbrown@onyxia:~/backups/My Documents/My Music/iTunes$ ls -R *.mp3
ls: *.mp3: No such file or directory

```

If I do ls -R by itself and then grep for .mp3 I can see my files, as well as grepping for .m4p which are the encrypted files. 

There has got to be an easier way to do this before resorting to building a shell script, as I think I am missing something here. Again could be a PEBKAC ;)

How could I easily copy all of my MP3's to another directory and do the same for the encrypted files?

---

### Post by kosmic on 2006-11-25
ok, maybe it is not the best solution but why don't you do this

create a folder, (ex.: mp3folder)

and the go the the folder where you have your .mp3 files and the itunes encrypted files and do :

cp -R *.mp3 /home/mp3folder/


Ps.: Also if you want to list only Mp3 files do " ls  -l *.mp3"

EDIT.: If the mp3 files  are inside folders you have to use the -R option (recursively)

---

### Post by Arisna on 2006-11-25
```
find . -iname "*.mp3" -exec cp '{}' ~/mp3s \;
```

This will find all files that end in ".mp3" and copy each to a folder called "mp3s" under your home directory.  You will have to create the "mp3s" directory before running this command.  You can modify this command to look for the iTunes file extension and copy those files to a different directory.

---

### Post by digilink on 2006-11-25
This seems to have taken care of it! Thanks to both for replying, I even learned a thing or two! 

Thanks again......

---

