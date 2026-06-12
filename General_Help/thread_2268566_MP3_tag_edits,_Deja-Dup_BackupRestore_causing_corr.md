---
title: "MP3 tag edits, Deja-Dup Backup/Restore causing corrupted folders"
date: 2015-03-09
forum: General Help
---

### Post by pmi2 on 2015-03-09
I should start by saying that I am more familiar with tar, most of the files I care about are backed up using Archive Manager, and therefore I did NOT lose anything significant in this process except a few MP3 tag edits, because all of the files affected were backed up using other means earlier.  If this had not been the case, re-ripping the discs would be the only recourse.

After editing some .mp3 tags in my various music folders over several days, I noticed some corrupted music folders and odd or missing files.  I have finally traced this to

a) the use of Deja-Dup Backup/restore from Deja-Dup archives,

b) Folders or track names with non-English language names,

and

c) using revert/restore in the file manager

I also finally got a consistent and repeatable fault, "Restore Failed" on a track with the following name:

> 08 - La canción de Sofia.mp3

No real idea what this means, but here is the error:
> Failed with an unknown error.
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module> with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir fn()
  File "/usr/bin/duplicity", line 1337, in main do_backup(action)
  File "/usr/bin/duplicity", line 1422, in do_backup restore(col_stats)
  File "/usr/bin/duplicity", line 700, in restore % (globals.restore_dir,),
UnicodeDecodeError: 'ascii' codec can't decode byte 0xf3 in position 95: ordinal not in range(128)

The rest of the corrupted files or directories did not necessarily produce an error, but my guess is that the issue is similar, because ALL are connected to a track or folder name with something other than the basic 26 letters of the English alphabet...

In some music folders, the end result seems to be that the edited file is deleted, and an empty file is created, for example:

> 08 - La canci&#65533;n de Sofia.mp3 (invalid encoding)

Again, nothing has been lost, except a few late night tag edits, so for now I have stopped using Deja-Dup and editing .mp3 files under Ubuntu, but it is something I would like to be able to do...., therefore - help!

---

### Post by Vaphell on 2015-03-09
[https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1286845](https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1286845)

sounds like this. A quick glance of this one and a few similar bug reports tells me it's a lame error caused by a relatively unimportant functionality of printing to log files set to ascii, that crashes the whole prog in the middle of the operation, leaving a corrupted file. Which version do you have?

That said, just in case you switch between windows and linux and work with these files, be warned that the representation of fancy characters in linux utf8 and whatever the codepage windows uses is going to be different and a source of pain.

---

### Post by pmi2 on 2015-03-10
I have the version that installed with ubuntu 14.04, and I have not tried to update to anything beyond what is in the repository.  In Software Center it is version "deja-dup 30.0-0ubuntu4."

If a bug, hard to believe it would not be addressed a year after the report.  I can't be the only person with Spanish, French, or Portugese language CDs.

A restore of the complete directory tree returns the files and folders to their original condition and file names, but not if individual files or directories are restored from the file manager.  Archive manager also does not seem to have a problem with the same names.  The error does not always show up.  Sometimes the operation fails with no feedback.

The problems affect folders with files I ripped recently after the ubuntu installation, as well as those transferred from Windows 7, so it is not caused by transferred files, but thanks for the warning.

---

### Post by Vaphell on 2015-03-10
I agree that the bug of this kind is pretty much inexcusable as dealing with encodings is a must in any modern program targeted at the masses. That said, there are thousands upon thousands of packages in the repos and after the feature freeze right before the release it's slow if not impossible to get a non-security related non-critical bugfix in program X.
You could try searching for dejadup PPA if it exists, there should be a newer version that might have the bug fixed.



As for win vs lin problem with filenames, it's not like anything is going to crash hard because of that (though some things might if they suck), but depending on which encoding is used, in one system or another you might be seeing garbage (eg that diamond placeholder or some funky chars). Just saying :)

```
$ touch 'test &#261;&#281;&#322;&#324;&#347;ó&#263;'
$ ls 'test '*
test &#261;&#281;&#322;&#324;&#347;ó&#263;
$ convmv --notest -f utf8 -t cp1250 'test '*          # convert filename from utf8 to windows cp1250 (central european)
mv "./test &#261;&#281;&#322;&#324;&#347;ó&#263;"	"./test &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;"
Ready!
$ ls 'test '*
test ???????                      # now the file has a garbage representation in linux set to utf8
```

---

### Post by pmi2 on 2015-03-10
I do see what you mean now, and that makes sense, thanks.  So I may be observing two overlapping problems.  

However, some restored .mp3 files do not only have corrupted file names, the files are empty, or gone altogether.

  This morning I did this test:

1) Create a dummy file called "Déjà Dup.test" in one of my folders. 
    ... note the standard French accent marks on the "e" and "a" in the file name!!!
2) Backup my Home directory with Deja-Dup Backup
3) Edit the dummy file, make arbitrary change, and save
4) Click on "Revert to Previous Version..." in Files
5) Select the backup to restore from, click "Forward" and "Restore"

End result, the file is _gone_, deleted from the folder with no error message or hint that something went wrong.  

AFAIK, this is repeatable, and not dependent on my ripped music folders.  

A backup program that deletes files with its own name during restore.... :shock:
Hiding the evidence? :D

Maybe I will try a German "umlaut" next, at least I can pronounce that (well, almost)

---

### Post by Vaphell on 2015-03-10
heh, when i googled about the issue i thought the same.
*How is that possible, the program has accents in its very name yet it would fail so hard working with it >_< lame, lame, lame.*

i'd check the PPA version, if it doesn't work i'd just drop using the program entirely and look for alternatives. Losing data especially in such a trivial case is not acceptable.

---

### Post by pmi2 on 2015-03-10
I'll try later today or tomorrow. (Its working hours here now).  I've tried to be conservative with adding PPAs, since I screwed my first installation of 14.04 by doing that a bit too indiscriminately. Live and learn (chuckle). 

My music is backed up in a plain old tar archives, so going back to that is no big deal for me.  however, you can easily see how one could corrupt an entire directory tree of folders, tracks, playlists etc. by a few cycles of incremental backup and restore using this software.

Not everyone can afford to keep multiple off-line archives on backup drives.  once you start deleting the old backups, the result is potentially heartbreaking for someone with a large CD collection on his machine.  An unexplained error like my first example, is annoying.  Lost files like in my second example, is a bigger problem.  I've seen two of those after a dozen edits, and some are not repeatable.

Another example I noticed earlier, a track called "Three's Company" is not restore/recoverable.  Rename it to "Threes Company" (without the apostrope), and resore works fine.  No fancy French or Portugese alphabet in this track name.

---

### Post by Vaphell on 2015-03-10
> Another example I noticed earlier, a track called "Three's Company" is not restore/recoverable. Rename it to "Threes Company" (without the apostrope), and resore works fine. No fancy French or Portugese alphabet in this track name. 

Now that is ridiculous. Is that a plain single quote found in ASCII?

---

### Post by pmi2 on 2015-03-10
> **Vaphell said:**
> Now that is ridiculous. Is that a plain single quote found in ASCII?Yes it is.  

To be 100% acurate, it is "James Lee Stanley - Three's The Charm", the name of an album, and also the default name of the automatically produced playlist file, which can be found in the folder after ripping the CD.  Both the folder name and the file name cause problems.  No other file systems involved, just the default ubuntu installed itself.

(I used "Three's Company" when I tested just to be funny, b/c it is the name of a TV show, and to avoid confusing myself.)

---

### Post by Vaphell on 2015-03-10
you should file a bug, without users pestering the devs, their motivation to be swift in fixing stuff is lowered ;-)

---

### Post by pmi2 on 2015-03-11
> **Vaphell said:**
> heh, when i googled about the issue i thought the same.
*How is that possible, the program has accents in its very name yet it would fail so hard working with it >_< lame, lame, lame.*

i'd check the PPA version, if it doesn't work i'd just drop using the program entirely and look for alternatives. Losing data especially in such a trivial case is not acceptable.Thanks for your help.

I could only find one package in the PPA, dated (2013-10-10), with the same version number. 
 The PPA looks unmaintained, since at least September 2014 (shrug).

Deja-Dup is a front end for Duplicity, so one can use it from the terminal, but there are probably better options.  

I am inclined to try Back In Time, if for no other reason than it has better support from other users.

Archive Manager and plain old tar for critical backups 
(not that I have much "critical" data on this install, LOL)

---

