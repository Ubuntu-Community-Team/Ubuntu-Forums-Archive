---
title: "word processor file conversion - or utility to modify date and time"
date: 2021-08-08
forum: General Help
---

### Post by Tom_ZeCat on 2021-08-08
I have a bunch of old Word *.doc files that I thought it might be nice to convert to LO Writer *.odt files.  At first, it looked like it would be easy.  LibreOffice has a built-in wizard which will convert *.doc to *.odt.  I ran it, and it worked.  However, it gave all the new files today's date and time.  I had wanted the files to retain their original date and times.  It looks like one of two things could work for me if I can find one of them: 

1. A file conversion utility that lets you keep the original file's date and time.  
2. A file manager utility that lets you change a file's date and time.  

I used to have one such utility back in my Windows days (prior to 2011).  I don't have it anymore and don't remember its name.  But there must be something like it for Linux.  I'm not finding it in the file managers I already have, Dolphin (the Kubuntu default), Krusader, and Double Commander.  If any of these file managers have it, I'm not finding it.  Does such a thing exist?  I strongly prefer a GUI-based utility so that I don't have to type all those file names one by one.  

Of course the other option would be a file converter that retains the original file's date and time.  

Anyone know if one or both of these things exist?

---

### Post by Holger_Gehrke on 2021-08-08
Can't help much, since I never had the need for such a tool. That the converter saves files with the current date is the correct thing to do, the converted files where created just then and usually you don't convert files you don't intend to work on ...

While I don't know of any graphical tool that adjusts the file dates in the way you want, doing it on the command line is not overly complicated:
```

touch -d "$(stat -c %y OldFile)" NewFile

```
If the files are in the same directory and have the same name except for the extension, a simple loop like
```

for oldfile in *doc; do touch -c -d "$(stat -c %y "$oldfile")" "${oldfile%.doc}.odt";done

```
should adjust all of them in one go.

Holger

---

### Post by dragonfly41 on 2021-08-08
If you have Krusader installed then look at Toolbar > Useractions > Manage Useractions to create such a tool.
I have written a bunch of custom Useractions to support workflows.
And I believe that there is a repository of community created Useractions..

---

### Post by HermanAB on 2021-08-09
++ for touch

---

### Post by Impavidus on 2021-08-09
touch can also use the timestamp of one file to apply to another.```
touch -r file.doc file.odt
```

---

