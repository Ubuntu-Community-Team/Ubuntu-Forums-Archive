---
title: "Recover deleted folders and their contents"
date: 2013-05-04
forum: General Help
---

### Post by Paddy Landau on 2013-05-04
I know this has probably been asked before, but my head is spinning a bit and I need some gentle guidance&#8230;

I have a partition formatted as ext4.

[LIST=1]
[*]I mounted the partition. 
[*]I accidentally deleted three or four folders from the root of the partition. 
[*]I did nothing else whatsoever on the partition (no creating files, no editing, nothing). 
[*]I dismounted the partition. 
[/LIST]
 Then I repeated this process on my backup partition, so the backups are also gone!

(Slaps head in frustration and cries out, "Doh!" This will teach me not to do backup work after I have taken my meds! :eek:)

How can I recover those folders and their contents?

---

### Post by Bashing-om on 2013-05-04
Paddy; Hi !

I am aware of this that "might" get your files back. Might be to your good to spend the time and effort in the research and see if you think it is doable from ubuntu.
[http://linux.sys-con.com/node/117909?page=0,0](http://linux.sys-con.com/node/117909?page=0,0)

I would say luck to ya -- but it is mental effort that rewards.

---

### Post by cortman on 2013-05-04
Hey Paddy;

Guess you used rm to delete? (in other words, it's not as simple as checking Root's "trash"?)
Testdisk may be your best option.

---

### Post by NM5TF on 2013-05-04
take a look at testdisk...it may be what you need....go here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Stonecold1995 on 2013-05-04
Yeah, I'd go with testdisk as well.  But be warned, it's hard, if not impossible, to completely recover files from an ext4 filesystem.  Once I accidentally deleted everything in /home and tried using testdisk/photorec to recover the files...  I got a few files, but no filenames, directories, etc.  Just randomly named files and corrupt files.  So I wouldn't get my hopes up on recovering everything back to the way it was.

---

### Post by Paddy Landau on 2013-05-05
Thank you for all of your responses. Yes, it was a rm command — well, actually done with rsync.

I'm about to try Test Disk, which I see is available on the standard repositories.

Wish me luck. I'll post my results.

---

### Post by Paddy Landau on 2013-05-05
My results, unfortunately, are a big fat zero.

Test Disk finds the deleted folders without any problem, but reports each folder as being completely empty.

So, that means that I cannot restore the files.

Unless you have any clever suggestions, I shall have to live with their loss. Thank heavens my critical files are all backed up in the "cloud". These files are inconvenient to lose, but not devastating.

---

### Post by Stonecold1995 on 2013-05-06
When you used TestDisk, the drive was mounted read-only, right?  If it's mounted read-write then that can overwrite some of the deleted data you want to recover.

Also here's a suggestion.  Before you start using the drive again, back up the whole partition to another drive (which can fit it of course).
```
sudo dd if=/dev/sdb1 of=/media/backup/sdb1.img # assuming sdb1 is the partition which you accidentally deleted files from
```

That way, if you ever in the future find a way to recover deleted files, you still have the drive image to work on.  Low-level copying utilities like dd copy everything exactly as it is present on the disk, independent of the state of the filesystem (unlike commands like cp).  This includes copying deleted files, corrupt date, filesystem errors, etc.

Also did you try PhotoRec, or is that done automatically by TestDisk.  TestDisk, if I remember correctly, is used for fixing corrupt partitions with damaged filesystems, etc, whereas PhotoRec is desiged to recover deleted files on a working filesystem.

---

### Post by Paddy Landau on 2013-05-06
> **Stonecold1995 said:**
> Also did you try PhotoRec, or is that done automatically by TestDisk.  TestDisk, if I remember correctly, is used for fixing corrupt partitions with damaged filesystems, etc, whereas PhotoRec is desiged to recover deleted files on a working filesystem.
Thank you for that clarification; I was unaware of it. No, TestDisk does not run PhotoRec. TestDisk took mere seconds to run.

I am busy running PhotoRec now, which (it says) has over three hours to go. I'll post back once it has completed.

** Edit:** Well, it's 1¾ hours later and it says it still has 4 hours to go. I'll wait patiently :-\"

---

### Post by The Cog on 2013-05-06
PhotoRec creates lots of numbered folders, with lots of numbered files in each folder. No file or folder names - just sequential numbers. It will find many thousands of gif images from your browser cache. Sorting through the recovered files is a nightmare. If you are just looking for a few important documents, you could be thinking about  what file contents you could search for while photorec is working. Good luck.

---

### Post by Paddy Landau on 2013-05-06
> **The Cog said:**
> Sorting through the recovered files is a nightmare. If you are just looking for a few important documents, you could be thinking about  what file contents you could search for while photorec is working.
I see what you mean: I already have 25,000 files recovered; which is strange, as I had nowhere near that number stored, and certainly not the 64Gb it has so far claimed to have recovered. Bizarrely, many of them are CAB, DLL and EXE files — even though I have never stored any Windows files on this ext4 system!

I shall trawl through the results using as much automation as I know; I guess the **[FONT=lucida console]file[/FONT]** and **[FONT=lucida console]strings[/FONT]** commands will come in useful. Do you have recommendations for any other commands to narrow down my searches?

---

### Post by Paddy Landau on 2013-05-06
PhotoRec finally finished.

It has produced thousands of files, many of which have contents that I do not recognise; and many of which are fragments of larger files.

For me to go through this lot, delete the garbage, and reconstruct the remainder, will take too much of my time.

Alas, I shall have to consider this whole exercise as a loss — but to take it as a lesson not to do any computer work after I have taken my medication. :(

Thanks for your time in trying to help me.

---

### Post by Stonecold1995 on 2013-05-08
> **Paddy Landau said:**
> PhotoRec finally finished.

It has produced thousands of files, many of which have contents that I do not recognise; and many of which are fragments of larger files.

For me to go through this lot, delete the garbage, and reconstruct the remainder, will take too much of my time.

Alas, I shall have to consider this whole exercise as a loss — but to take it as a lesson not to do any computer work after I have taken my medication. :(

Thanks for your time in trying to help me.
I suggest you back up the files somewhere in case you need to find something again.

If there is a certain string you need to find you can use grep to search for it.
```
grep -r "My Essay" /path/to/recoved/files
```

---

### Post by Paddy Landau on 2013-05-08
> **Stonecold1995 said:**
> I suggest you back up the files somewhere in case you need to find something again.
I discovered that PhotoRec allows you to restore selectively (e.g. Open Documents, photographs, etc.). So, I reran it, excluding almost everything and including only those items that I could possibly want. It restored almost 1,000 items; presumably many of them fragments and many of them unwanted. This is probably manageable if I trawl through it over the next couple of weeks.

> **Stonecold1995 said:**
> If there is a certain string you need to find you can use grep to search for it.
Thanks; unfortunately, I cannot remember everything that I lost, or at least what specific wording might have been used. I'll have to go through each item manually.

Thank you again for your help.

---

### Post by Bashing-om on 2013-05-08
Paddy;
I ran across this tutorial that might give you some ideas for other options:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I feel for you

---

### Post by Paddy Landau on 2013-05-08
> **Bashing-om said:**
> [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Thank you. I shall go over that carefully tomorrow.

---

### Post by Stonecold1995 on 2013-05-11
> **Paddy Landau said:**
> Thanks; unfortunately, I cannot remember everything that I lost, or at least what specific wording might have been used. I'll have to go through each item manually.
You don't need to remember specific wording.  You can use grep with -i to be case insensitive, or run it with an OR operator (e.g. "grep -E 'string1|string2'" will search for EITHER string1 OR string2).  You can also use agrep (approxmimate grep), which will find SIMILAR words to what you enter.

---

