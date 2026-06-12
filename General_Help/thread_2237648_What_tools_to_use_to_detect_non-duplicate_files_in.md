---
title: "What tools to use to detect non-duplicate files in bash script"
date: 2014-08-03
forum: General Help
---

### Post by CaptainMark on 2014-08-03
I want to write a small script that will check each photo in my Dropbox directory and copy it to my hard drive only if it is a new photo but I don't know what tools to use to do it.
I need something that would do the opposite of fdupes and check if any photos in ~/Dropbox/shared_photos do NOT already exist in ~/Pictures and copy them over if needed.

It's a shared directory with thousands of images including my own, I want to be able to automatically (on a cronjob) copy out everyone else's photos but obviously I don't need to copy my own photos.

(Note, I know I could just try and copy them all and allow the ones that I already have to silently fail to copy but with this many images that would be a massive waste of cpu cycles every time the script and generally this would just be shoddy coding.)

Any tips would be appreciated

Regards
Mark

---

### Post by sudodus on 2014-08-03
[I][B]- Do you expect that your files are in the same positions in the directory trees of dropbox and your own file system?
[/B][/I]
This is easily done with ***rsync*** (if rsync works with dropbox)

```
rsync -Havun dropbox/pictures/ your/pictures
```

and when you see that it looks OK, run the real command line without the option n (dry run).

 From ```
man rsync
```

```
       -u, --update
              This forces rsync to skip any files which exist on the destination and have  a  modified
              time that is newer than the source file.  (If an existing destination file has a modifi&#8208;
              cation time equal to the source file&#8217;s, it will be updated if the sizes are different.)

              Note that this does not affect the copying of symlinks or other special files.  Also,  a
              difference  of  file  format  between the sender and receiver is always considered to be
              important enough for an update, no matter what date is on the objects.  In other  words,
              if the source has a directory where the destination has a file, the transfer would occur
              regardless of the timestamps.

              This option is a transfer rule, not an exclude, so it doesn&#8217;t affect the data that  goes
              into  the  file-lists,  and  thus it doesn&#8217;t affect deletions.  It just limits the files
              that the receiver requests to be transferred.

```

[I][B]- Or do you want to check for duplicates wherever they might be?
[/B][/I]
This is harder and means you have to check recursively for each file  through your file system if it matches with your dropbox file.

---

### Post by CaptainMark on 2014-08-06
Yeah I should have explained, I wanted to try and formulate a list because the directory structure is different so it's not a simple copy command I want to use on all the new photos, it involves using jhead to ascertain each photos time stamp and sort them in the structure ~/Pictures/{year}/{month}/{date&time}.jpg so what I really needed was tools to determine which photos are not already in ~/Pictures regardless of the rest of the path name and use the list as arguments for a 'while read' loop (or similar) in the script.

Regards
Mark Skinner

---

### Post by sudodus on 2014-08-06
Yes, this is harder. I don't know such a tool, but it should be possible to make a shell-script. If jhead gives you enough information, then make a list with that information of all files in your computer, and use that list versus each file in dropbox.

If jhead is not enough (does not work with for example png files), md5sum should be enough. How much data is it? Let's say each file is 3 MB and you have 3000 files, that means 9 GB, which is no more than around nine Ubuntu desktop iso files, which can be scanned with md5sum is a reasonable time. If you have ten times that amount of data, md5sum might not be attractive for all the files, but if only a small fraction of the files need md5sum, it would be OK.

---

### Post by vasa1 on 2014-08-06
> **sudodus said:**
> ...
This is easily done with ***rsync*** (if rsync works with dropbox)
...
Could you explain the "*if rsync works with dropbox*" part? What do you mean by that?

---

### Post by sudodus on 2014-08-06
I have a dropbox account, but I have not installed the software to integrate it into the file system. I only use the web browser interface. I don't know if a command line tool like rsync can connect to dropbox. If you know, please tell us :-)

---

