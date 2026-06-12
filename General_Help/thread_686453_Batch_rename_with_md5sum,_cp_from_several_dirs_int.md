---
title: "Batch rename with md5sum, cp from several dirs into one (+learning shell commands)"
date: 2008-02-03
forum: General Help
---

### Post by migla on 2008-02-03
How do I copy files from several dirs to one dir (not preserving path) and add the md5sum (or equivalent) of each file to each filename?

[Edit:] I [posted this on linuxquestions]("http://www.linuxquestions.org/questions/linux-newbie-8/append-md5sum-or-similar-to-filename-batch-copy-from-multiple-directories-to-one-618380/") as well a few hours after I posted here and now that seems an uncool thing to have done, since I might make goodhearted people do unnecessary work for me. [/Edit]

Actual use case:

> I have lots of photos on 2 computers, most of the files being on both, but possibly under different directory structures and some filenames possibly being duplicate for different photos.

If I reset my cameras counter or use another camera of the same brand, I wouldn't need to take 10k photos in a day for duplicate names to appear (also assuming here I put the photos in subfolders named with the date) .

I want to get organized and start syncing, but first I want to make sure all photos have unique filenames and can be in one big fat directory.

So far, I think using the find command could be part of the operation. This will find recursively all the relevant files in my home dir (if that's where I type it) : ```
find . -type f -name \DSCN*
```

(Edit: "DSCN" is what the filenames of all of my photos begin with)

Later on, I might want to ask about rsync, since I don't really get the syntax of man pages. (I'll look into understanding man pages in the meantime. As the old saying goes: "Teach a fish to man and they will use the shell for a lifetime...")

---

### Post by noynac on 2008-02-03
> **migla said:**
> How do I copy files from several dirs to one dir (not preserving path) and add the md5sum (or equivalent) of each file to each filename?...
There was an earlier thread on copying files from multiple directories to one directory. The link is:

[http://ubuntuforums.org/showthread.php?t=672668&highlight=find+jpg+exec](http://ubuntuforums.org/showthread.php?t=672668&highlight=find+jpg+exec)

The basic command is:

find /SourceDirectory -name '*.ext' -type f -exec cp '{}' /DestinationDirectory ';'

You have to insert the actual names of the source and destination directories, and the file extension (if needed).

I am not familiar with md5sum and can't be of help in that respect. To avoid duplicate file names with digital photos, I use a file name that contains the date and time (including seconds) that the photo was taken as extracted from the exif data. I use the exiv2 commandline utility for this purpose as follows:

exiv2 rename -r "%m-%d-%y@%H:%M:%S " *.*

As an aside, some people have recommended the utility called Phatch to move and rename files. I haven't used this program, but it might be worth a look.

---

### Post by migla on 2008-02-03
Thanks! :)

Renaming with exif-data would make more sense than adding an md5sum. I'll soon try this out. You probably solved this for me. 

If someone wants to explain a procedure for doing something to each file (such as calculating md5sum) and then putting the outcome in the filename, that would still be interesting academically, though.

[Edit:] And if someone would know how to preserve the cameras initial filename (which I don't think this command will do) and append the date and time to that with an exiv2 command, that would be very cool too, in case I ever have two cameras and take a picture at the same second... ;) Well, that's not fundamentally important. Thanks again noynac!

---

### Post by noynac on 2008-02-03
> **migla said:**
> Thanks! :)...
[Edit:] And if someone would know how to preserve the cameras initial filename (which I don't think this command will do) and append the date and time to that with an exiv2 command, that would be very cool too, in case I ever have two cameras and take a picture at the same second... ;) Well, that's not fundamentally important. Thanks again noynac!

Your welcome! 

The exiv2 manual page contains the following example:

exiv2 -r’:basename:_%Y%m’ rename img_1234.jpg
Renames img_1234.jpg to img_1234_200511.jpg

I've never used the basename option, but perhaps it will do what you want.

---

### Post by migla on 2008-02-03
Yes, I'll look into that basename thing. I'll possibly also need to incorporate the filtering with the find and cp commands, so that I can run it from the base of my home directory... ... hm... Or maybe I can include filtering of that sort in the exiv2 command with img_* (or DSCN* in my case).

---

### Post by peitschie on 2008-02-03
md5 sums are actually ridiculously easy as well.  There is a command called 'md5deep' ([http://md5deep.sourceforge.net/](http://md5deep.sourceforge.net/)) that can do everything you're asking for ;)

You can make it run through the directories and do one of several things:
[LIST=1]
[*]Make a list of files & hashes currently in the system
[*]Find files that are not currently in a hash list
[*]Find files that ARE currently in a hash list
[/LIST]

So the basic operation would be:
[LIST=1]
[*]Initial md5deep in each drive stored in a file on the base directory for each drive
[*]To transfer from one to the other you would run the md5deep command to find any files on the source drive that don't have a hash in the md5deep file on the destination drive (this outputs a list of filenames)
[*]Use rsync which supports copying only files in a relative file list
[*]Update the hash lists on both drives with any new additions (this is a supported command by md5deep as well ;))
[/LIST]

This would be 2-3 scripts tops... all currently supported tools...

The EXIF-idea sounds good too however, I'm just giving this as an alternative that can be applied to more than just pictures :)

---

### Post by migla on 2008-02-03
> **peitschie said:**
> md5 sums are actually ridiculously easy as well.  There is a command called 'md5deep'

Cool. Thanks! I was hoping someone would still comment on the md5sum thing. Learning new things is fun :)

I've just done the EXIF thing...

I ran the following command:  
```
find . -type f -name \DSCN* -exec exiv2 -r':basename:_%m-%d-%y@%H:%M:%S' rename {} \;

```...and now all my pictures have a name similar to "DSCN1253_05-07-06@12:22:34.JPG"
I should have thought about what order I wanted the date displayed first, since I'd preferred yymmdd, but that's ok. It did also tell me "Warning: Makernote: Pointer to next IFD is out of bounds; ignored." about a few hundred times. Whatever that means... 

But anyway, problem solved. Now I'll just need to use find with the cp command:
```
find . -type f -name \DSCN* -exec cp {} /home/username/bigfatphotodir/ \;
```
...to move all into one dir. But I'll do that tomorrow. First I'll make sure everything really is allright and also test it first on some testfiles.

---

