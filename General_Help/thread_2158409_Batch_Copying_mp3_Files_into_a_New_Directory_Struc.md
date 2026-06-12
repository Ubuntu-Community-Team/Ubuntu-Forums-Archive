---
title: "Batch Copying mp3 Files into a New Directory Structure"
date: 2013-06-28
forum: General Help
---

### Post by Iggy64 on 2013-06-28
I browsed the various forums, and could not decide where this question belongs.  So I'm putting it under "General Help."  If it should be elsewhere, I hope the moderator will forgive me and move it appropriately.  Thank you.

I have about 4,000 mp3 files on a USB drive.  Each one is well tagged (ID3v2) and the filenames are all in the format: Title ~ Artist.mp3.  Currently, they are divided into about 130 folders, numbered 1 through 130. (It's a long story how they got that way.)  Within each of these folders, the tracks are grouped by album (in subfolders).  So the current structure is:

/mp3/foldernumber/albumname/title ~ artist.mp3


I want to copy (not move) these files to my internal hard drive.  I could simply copy the existing structure, but it would be nice if I could copy them into a new directory structure, arranged like this:

/mp3/artist/album/title ~ artist.mp3

I think I might be able to pull this off by installing mp3tag under WINE, then somehow using the filename-to-path converter.  But I'd probably need some help with that, as I know very little about coding.

I'm wondering if there is a way to manage this task through the terminal in Linux, of through some other means.  Perhaps someone has already developed a similar tool for re-organizing folders.

Just thought I'd check before I simply copy the whole mp3 collection with the existing directory structure.

---

### Post by papibe on 2013-06-28
Hi Iggy64.

I would start by copying the data to your hard drive. You can use either the GUI to copy the files, or the command line. I'd recommend using the command line, and use rsync:
```
rsync -av /path/to/source /path/to/destination/
```
Then when it's there, you can use several GUI tools to rename files and directories. Take a look at **GPRename** and **pyRenamer**. Both are available on the Software Center.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Iggy64 on 2013-06-28
Thanks, papibe.

Yes, if I decide to do the straight copy from one disk to the other, I figured I'd use rsync, since I've had good luck with that before.  Unfortunately, I would need more than _renaming_ of the directories.  I would need totally new combinations of which files go in which directories.  That is, on the target drive, I would like to first group by artist, then by album.  This is different from the source drive, where they are grouped by a folder serial number, then by album.  

Like I said, I might be able to do that by mp3tag, if it runs completely enough under WINE.  Otherwise, I'd need help from someone who knows how to write some command-line code in Linux, to do some find + copy magic.

I appreciate your taking time to help.

---

### Post by Vaphell on 2013-06-29
are 1-130 dirs the only things in /mp3?

```
#!/bin/bash

src=$HOME/temporary
dest=$HOME/mp3

# $src/number/album/title ~ artist.mp3
for f in "$src"/*/*/*.mp3
do
  printf "$(( ++i )): "
  artist=${f%.mp3}; artist=${artist##*\~ }   # extract artist from filename
  album=${f%/*.mp3}; album=${album##*/}      # extract album from path
  mkdir -p "$dest/$artist/$album"            # create dest dir for file (cp/mv requires existing target dir)
  **echo** mv -v "$f" "$dest/$artist/$album"     # cp if copying original data, mv if sorting files dumped to internal hdd
done
```

copy files first to a temporary location and then try the script above (set proper paths), which should sort files how you want
In its current form the script should print a bunch of **mv -v <file> <dest_dir>** (echo) so you can check if everything is ok, if you like what you see remove echo to actually execute mv's to put files in proper places.
You can use the script to copy data from the original location right off the bat, your choice (but then you need **cp** not **mv**)

---

### Post by vanadium on 2013-06-29
Under Ubuntu, Easytag can automatically move your mp3 files to a directory structure based on the tags. Easytag is available in the software center. After selecting the root directory of your music files, you will need to run the "Rename Files and Directory" scanner and supply a correct template. One of the build-in defaults is "%n - %a - %t", but you can supply entire path names, e.g.
"/media/Iggy64/Music/mp3/%a/%b/%t ~ %a" (here, /media/Iggy64/Music would be the mount point of your USB drive containing the music).

---

### Post by Iggy64 on 2013-06-29
Thank you, Vaphell, for the code (and the commenting!).  I really have to try this out this afternoon.  I'm sort of a noob to Linux, and I've never done much scripting in my life.  So this will be a good education for me.  It was nice of you to make time to spell it out for me.  Much obliged.

And a thank-you to Vanadium for the idea about Easytag.  I have used mp3tag (when I was a Windows person), and have started exploring Puddletag, which was evidently inspired by mp3tag.  I'd have to look at it more closely to see if it could do this task.  But since you know that Easytag will do the job, I'll have to check it out.  I really appreciated the suggestion.

I'll bet both of these suggestions are great ideas; now we'll see if I can use them properly without screwing up.  I'm sure to learn some useful tools by trying.  Thanks, again, to both of you.

---

### Post by Vaphell on 2013-06-29
no problem :-)
i strongly encourage to learn a bit of shell scripting.That's how you become the true master of your own computer, it's like a whole new world of possibilities opening for you ;-) You stop depending on 3rd party programs to do relatively trivial tasks anymore. It might look a bit scary but it's not rocket science, really.

---

### Post by Iggy64 on 2013-06-30
Well, I really enjoy learning new things.  I did some scripting years ago, but nothing serious.  I guess I know the general principles.  But I don't know the Linux landscape very well, so there's a lot to learn.  If you know of any on-line tutorials that you yourself think are great places to start, I'd be interested.

Thanks, again.

---

### Post by Vaphell on 2013-06-30
you might find this recent thread informative

[http://ubuntuforums.org/showthread.php?t=2158026](http://ubuntuforums.org/showthread.php?t=2158026)

---

### Post by Iggy64 on 2013-07-02
Thank you!  I have already begun studying it.  As you said, it would be a great asset to be able to do a little scripting.

---

