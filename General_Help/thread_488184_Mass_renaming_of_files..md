---
title: "Mass renaming of files."
date: 2007-06-29
forum: General Help
---

### Post by Washington Irving on 2007-06-29
I want to make a partition which contains some backed up files. Some of these files are mp3s, some of which have special characters in their filenames (i.e. some bounus tracks have the suffix [*]). I figured that the best type of partition was FAT32 but these files won't copy.

Does anyone know how to rename them easily? Ideally so that the special characters are replaced with a "-" or "_". I looked at some other threads and it seems that it can be done easily using the commandline but I couldn;t figure out exactly how.

Thanks.

---

### Post by jwh400 on 2007-06-29
There is an app called Thunar that is in your repositories. 
You can also archive files with odd characters in their filenames. Once you have them in an rar they can be moved or copied where you like.

---

### Post by Washington Irving on 2007-06-30
Thanks. How would i go about renaming them with Thunar. it seems as if I would have to add each file individually. Is there a way i can just specify a folder and it will rename all files in it and its subfolders?

---

### Post by scroll12 on 2007-06-30
another one is Purrr.

stil trying to find out how to add Folders
------------------
oh, it's fairly simple, just Drag/Drop the folder into Purrr

---

### Post by frodon on 2007-06-30
You can try to do all in one command, it would make something like :
```
rename s/ /_/ `find /your_partition_path -type f`
```the find command list all your files and the regular expression used with the rename command replace blank character by "_" character, then what you need is a regular expression to match your special characters.

---

### Post by Washington Irving on 2007-06-30
Thanks but I don't think Purrr can do exactly what i'm looking for. I basically want to be able to rename all files in a folder and its subfolders which have characters such as asterisks, question marks and so on by replacing these characters with hyphens. It looks like Purrr will just rename the folder and not it's contents and also as far as I can see the only options for renaming are adding a prefix or suffix whereas i'm looking for a "find and replace" kind of thing.

EDIT: Ah, I didn't see your post frodon. i'll try that now.

---

### Post by Washington Irving on 2007-06-30
Hmmm. That didn't work either: ```
adam@adam-desktop:~$ rename s/?/-/ `find /home/adam/Buffer -type f`
bash: /usr/bin/rename: Argument list too long

```

Is this because there are too many files to rename at once. There are loads of files in that directory but  I need to do it on two other folders as well which have more files.:(

---

### Post by jwh400 on 2007-06-30
I'm not sure about Thunar's ability to rename subdirectories but with it's meta tag plug-in you can do a batch renaming of all music files in a directory based on their meta tag info.

[http://thunar.xfce.org/plugins.html#thunar-sbr](http://thunar.xfce.org/plugins.html#thunar-sbr)

---

### Post by frodon on 2007-06-30
> **Washington Irving said:**
> Hmmm. That didn't work either: ```
adam@adam-desktop:~$ rename s/?/-/ `find /home/adam/Buffer -type f`
bash: /usr/bin/rename: Argument list too long

```

Is this because there are too many files to rename at once. There are loads of files in that directory but  I need to do it on two other folders as well which have more files.:(I didn't know about the limit for the rename command regarding the number of files to rename.
Anyway you can try with with several step, performing the command on smaller directories.

---

### Post by robertc36 on 2007-06-30
Thunars bulk rename has a  seperate entry on apps/accessories sexily titled Bulk Rename

---

### Post by Washington Irving on 2007-06-30
Thanks for all your input. In the end I remembered that EasyTag has an option to remove special characters and so I just used that on all my mp3s.

Cheers anyway though.

---

### Post by frodon on 2007-07-01
> **Washington Irving said:**
> Thanks for all your input. In the end I remembered that EasyTag has an option to remove special characters and so I just used that on all my mp3s.

Cheers anyway though.Thanks for sharing, i have easy tag as well and never thought to use it for this purpose, good finding this is good to know and really useful :KS

---

### Post by phirestalker on 2007-10-17
> **Washington Irving said:**
> Thanks for all your input. In the end I remembered that EasyTag has an option to remove special characters and so I just used that on all my mp3s.

Cheers anyway though.

if however you needed to rename folders and files of any type you could use

```
find full-path-to-parent-folder -iname "*" -exec rename -v 's/\:|\*|\?|\"//g' "{}" \;
```

also this one will just remove the offending characters which I like better than using _ only because a file names bob_s poem doesn't make as much sense as bobs poem if you happen to be removing ' although I don't recall running into a file system where this was necessary :confused: 

oh and the problem someone here had with the rename /?/_/ command is because ? is used as a wildcard so to keep this from happening one has to rename /\?/_/ hope this helps someone :)

PS. unfortunately the find command stats all files before it starts so this will need many passes since it is also renaming directories. if anyone knows a way around this limitation of the find command let me know

---

### Post by mojoman on 2007-10-17
Thunars mass rename, called bulk rename, can be started from the terminal as well

```
thunar -B
```

It's good. I like it. 

If you want something like it but that's on steroids as well, check out GPRename. A lot more options, a lot more powerful. I love it. Only downside is that I don't think it's in the Feisty repositories. Might be in Gutsy though. I got it installed on my Debian Lenny partition and know for a fact that it's available for Lenny and Sid. 

Otherwise you can compile it from source which is available at [_sourceforge_]("http://gprename.sourceforge.net/")

/mojoman

---

