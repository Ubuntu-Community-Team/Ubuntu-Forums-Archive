---
title: "Command-Line to Copy Files with Same Name"
date: 2018-03-21
forum: General Help
---

### Post by manikinxvx on 2018-03-21
Posting this here, as I did not find a sub-category of the forums specific to command line; I apologize if I overlooked it and am thus posting in the wrong spot.

Using the following, I am working on a way to find all mp3 files that are located in sub-directories on one drive and copy them to a singular directory on another drive. Given that sometimes different bands will use the same title for songs as other bands, I am appending files with the same name with a number. However, this presents a problem if I ever want to simply re-run this to move multiple files without appending existing files with another number.

What I need to do in here, presumably between find and mv, is to compare the byte-size of the files in "(from)" with those of the same name in "(to)" and copy only the ones that have different sizes if their names are the same. Although... I realize that I have actually created a problem with comparing the file names; the ones in the "(from)" directory don't have the appended numbers, while the ones in the "(to)" directory do have them and I would also need to account for this when doing any comparison.

Maybe I'm going about this in the wrong manner to accomplish my goal. Anyone have any ideas or a better way to do it?

```
find (from) -type f -iname "*.mp3" -exec mv --backup=numbered -t (to) {} +
```

---

### Post by vanadium on 2018-03-22
>  Maybe I'm going about this in the wrong manner to accomplish my goal. Anyone have any ideas or a better way to do it?
Probably you are. But more important, your goal is not quite clear. What do you want to accomplish? Is this a backup?

---

### Post by manikinxvx on 2018-03-22
Essentially, yes, it is a backup... but with no directories/sub directories; just all of the files in one folder with no overwrite nor duplicating existing files.
This is starting to seem improbable every time I even explain it to myself.

---

### Post by manikinxvx on 2018-04-05
OK, I have dramatically changed direction for renaming these files. My  intention now is to change the name each file using its last  modification date. 
I have a feeling that jhead will work this. However, I am stumped about inserting it into my previous code.
I think I want to use ```
jhead -autorot -nf%y%z%H%i%s%u *.mp3
``` to create the file  names (example: 18365245959000000.mp3) and put it into the specified directory... but I am simply stumped if  I can put this into my previous attempt or if I have to totally rewrite  it.

(Too often my ideas surpass my skills)

---

### Post by manikinxvx on 2018-04-05
... and I obviously would be removing this argument:
```
 --backup=numbered -t 
```

---

### Post by vanadium on 2018-04-05
Your command may need to look like:
```

find <sourcedir> -type f -iname "*.mp3" -exec mv --backup=numbered "{}" <destinationdir> \;

```
Linux can do what you want. I am not clear though, on what the added value of your approach is compared to a backup where you replicate the entire directory structure of the original. The latter can easily and incrementally be done with rsync.

---

### Post by HermanAB on 2018-04-05
You can also use a deduplication utility to find and hard link  identical files and save a ton of disk space.

For dedup, you can use fslint or a utility called... hmmm... wait for it... drum roll... hardlink.

---

### Post by manikinxvx on 2018-04-05
vanadium, your response doesn't read the modification date from each file and use that info to configure the new name for each file when it is put into the new location. That's pretty much my only current dilemma. 
I no longer want/desire it to append the file name, but do want it to :::not paste(move)::: files that have the exact modification info used to create a new file name. So... I also need it to compare modification dates.
UGGGH!

I definitely appreciate all responses to this struggle.

---

### Post by vanadium on 2018-04-05
Well, I was just continuing on what you provided. rsync -av <source> <destination> will preserve anything, and thus constitute the most reliable backup copy if that is what you want. In other words, the goal of what you really want to achieve and why remains unclear to me.

---

### Post by HermanAB on 2018-04-05
There is a batch utility called Phatch, that provides a fun way to do what you need.

There are also various batch rename functions, one of which comes with the Thunar file browser.

---

