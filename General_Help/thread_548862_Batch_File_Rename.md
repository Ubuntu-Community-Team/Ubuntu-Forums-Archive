---
title: "Batch File Rename?"
date: 2007-09-11
forum: General Help
---

### Post by Dylnuge on 2007-09-11
Hi,

I have a simple problem, which hopefully has a simple solution. I have a bunch of files in a folder which all start with the same thing (or close to the same thing-case varies, but it is not a huge deal if I have to do this twice).

Anyway, I want to remove the common starting name. For example, say every file starts with File, and I want to rename all files starting with File to their current name without the File intro-that is, FileThisdoc.info would becoem Thisdoc.info, and so on.

There are files in the folder that do not start with File, so I need a command which can ignore these, while removing the File beginning on the others. In addition, some of the files start with file instead of File. If I need two commands for this, so be it.

Thanks,
Dylan

---

### Post by overkillm on 2007-09-11
KRename is an awesome app that allows you to do the kind of batch renaming you're talking about, and can also rename based on regular expressions.  It's a KDE app but I think it should still work if you're using GNOME, most KDE apps seem to, and vice versa.  It's in the repos, check it out.  :)

Now, if you're wanting to do this in something like a shell script, I wouldn't be able to help you too much.  I'm only just learning shell scripting myself.

---

### Post by HermanAB on 2007-09-11
Hmm, read up on the 'find' command.  Find can search recursively and execute a command when it finds a match.  Some Googling for your problem will yield many examples.

---

### Post by mrxinu on 2007-09-11
First match on a google search for "batch rename".  For the first example, instead of removing the suffix, you could remove the 'File' portion.

[http://lab.artlung.com/unix-batch-file-rename/](http://lab.artlung.com/unix-batch-file-rename/)

---

### Post by Dylnuge on 2007-09-12
Thanks mrxinu! Krename deleted the files I tested it on-Thank god I tested first, so I used mrxinu.

---

### Post by arsenic23 on 2007-09-12
Ok, lets say the files look like this:
```
pie0awsome
pie0pie
pie0noodles
```

If you want to remove the 'pie0' from the front you would just use the rename command like so:
```
rename 's/pie0//' pie0*
```

That will look for all files that match pie0* and replace pie0 with nothing.  Likewise if you wanted to replace pie0 with 01 you would run:
```
rename 's/pie0/01/' pie0*
```

---

### Post by Oki on 2007-09-12
Install xfce filemanager called Thunar(you will find it in Synaptic). Also check the plugin called Thunar renamer. It works as a dream, and can do all what you said, with a nice GUI, and has a lots of options.

---

### Post by Dylnuge on 2007-09-13
Thanks Oki. I also tried PCMan File Manager (which someone recommended to me in place of Thunar) and like both.

KRename did not delete my files after all! My files had been named File.name.extension, and Krename did what I asked it to-removed the "File," leaving the file to be called .name.extension. Linux did what it was suposed to do with files beginning with dot-hid them. All I had to do to fix it was unhide the files by removing the leading .

---

