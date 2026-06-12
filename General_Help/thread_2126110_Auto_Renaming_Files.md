---
title: "Auto Renaming Files"
date: 2013-03-16
forum: General Help
---

### Post by Jonny87 on 2013-03-16
I have just used TestDisk/PhotoRec to Recover some lost files. however they all have meaningless names (e.g. f145686.odt). 

What I want to know is, is there some sort of command or script or software that scan the files looking for some sort of title or header and use that to rename them to restore some meaning to them all save a very tedious task?

If not perhaps someone reading this has the know how to create such a thing. I'm sure I'm not the only one that would find this useful.

---

### Post by Stonecold1995 on 2013-03-16
I had the same exact problem when I accidentally rm -rf ~/'ed my whole computer.  Unfortunately, ext2/3/4 erases the filename at deletion, so even with the correct software there is no way to get the files' original names back.

The software you used DOES use the header of the file to try and detect it's file type (e.g.[COLOR=#000000] f145686.odt is most likely a OpenOffice document, I think).  Without extremely advanced (and expensive) FBI/NSA-style recovery, there's no way to recover the names using software.  You're only hope is if you have a backup somewhere.[/COLOR]

---

### Post by Jonny87 on 2013-03-16
LOL it was my backup (of two laptops) they were just about to be restored. My wife plugged the external drive into the TV not knowing that TV was going to format it. :frown:

Managed to recover most if not all of the Photo and Home Video (the most important stuff).

Was a NTFS Drive (TV formatted it to XFS) to by the way.

---

### Post by coffeecat on 2013-03-16
Have a look at krename. It has a number of plugins that can be used to batch rename files into something more usable. You might find the jpeg/tiff exif plugin useful for adding exif metadata to filenames of photos, and taglib for tag metadata of mp3 files.

---

### Post by Impavidus on 2013-03-16
It may be possible for most file types to get some information that is usable as a file name. You would need separate code for each file type, so that would be a script that determines the file type for each file and then calls some tool to extract a title from the header of that file type, and then uses that title to rename the file. Image formats often store some metadata in the file, which may contain a caption, from pdf and libreoffice writer documents you may be able to extract the title, titles of mp3 files are usually recoverable too. I don't thing there's a solution for all types at the same time, and for text files it will certainly not work.

---

### Post by sudodus on 2013-03-16
> **coffeecat said:**
> Have a look at krename. It has a number of plugins that can be used to batch rename files into something more usable. You might find the jpeg/tiff exif plugin useful for adding exif metadata to filenames of photos, and taglib for tag metadata of mp3 files.
Some file types have embedded information that might contain suitable information for renaming. See this link

[[COLOR=#ff0000]http://www.cgsecurity.org/wiki/After_Using_PhotoRec[/COLOR]]("http://www.cgsecurity.org/wiki/After_Using_PhotoRec")

---

### Post by Jonny87 on 2013-03-16
Thanks for the input everyone, I will try the suggest options and get back to you all with how I go on.

---

### Post by varunendra on 2013-03-17
> **Jonny87 said:**
> Thanks for the input everyone, I will try the suggest options and get back to you all with how I go on.

Instead of dealing with recovered files, try the 'P' key option in testdisk after deeper search (if you haven't already overwritten the drive). It lists the files found on a detected (earlier) filesystem for confirmation purpose, but also gives an option to individually copy them, including recursive copy of directories.

Unless you have overwritten the data area, it may detect the previously existing NTFS partition on it after "Deeper search". If found, you can either restore the partition itself or recover individual files/folders from it.

---

### Post by Jonny87 on 2013-03-17
> **varunendra said:**
> Instead of dealing with recovered files, try the 'P' key option in testdisk after deeper search (if you haven't already overwritten the drive). It lists the files found on a detected (earlier) filesystem for confirmation purpose, but also gives an option to individually copy them, including recursive copy of directories.

Unless you have overwritten the data area, it may detect the previously existing NTFS partition on it after "Deeper search". If found, you can either restore the partition itself or recover individual files/folders from it.

Oh OK that's good to know. I have unfortunately over written the drive just last night as I was confident that I had already recovered all that I was going to be able to recover. And it appeared that the Photos were there, but I wish I had known this before. I'll keep it mind next time. Thanks.

---

