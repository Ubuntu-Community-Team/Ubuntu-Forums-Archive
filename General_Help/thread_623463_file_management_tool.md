---
title: "file management tool"
date: 2007-11-25
forum: General Help
---

### Post by kpictjl on 2007-11-25
Can anyone recommend a tool to help me organize the hodge podge of files I have?  I inherited a hard drive from a family member and it has about 8 GB of pictures, pdfs, documents all over the place in all sorts of different folders.  There are a ton of duplicates but lots of really good old stuff that I want to keep.  It's like she took all here files and stirred 'em up ... if feels like separating the chocolate from the milk.

I'm sure a nifty shell script using "find" would help.  I don't want something like Picasa just yet, I want to get all the files into real folders and get rid of duplicates first.

So, any tool or just advice is appreciated.

Ubuntu 7.10

---

### Post by kpictjl on 2007-11-26
I'd be happy with a shell script that took all files and put them into folders based on file type.

---

### Post by AlanRogers on 2007-11-26
You could do it yourself, if you're prepared to use the terminal; [ALT]+[F2], type 'gnome-terminal', then [RETURN].
 
In the terminal window, change to the new hard drive```
cd /path/to/hard/drive
```and repeat the following two lines as often as necessary, where *{EXT}* is the file extension```
mkdir *{EXT}*Files
mv *.*{EXT} {EXT}*Files
```
Then you'll have folder like JPGFiles, DOCFiles, PDFFiles, MP3Files, etc for you to sift through at leisure.

---

### Post by HermanAB on 2007-11-26
Read up on the 'find' command.  It can recurse directories while calling a sub command.  So you can use that with name globs and move schtuff around.

Like this ogg to mp3 conversion example:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

Basically, 'find' is the reason why Bash doesn't do loops.

Cheers,

Herman

---

### Post by kpictjl on 2007-11-26
Thanks, this will do the trick at the most basic level...

```

find /home/shared/test/junk -name \*.jpg -print -exec mv {} /home/shared/test/jpgs/ \
```;

I'll have to figure out now how to test for duplicates.  I'm thinking I'll try to append "dup" at the end of all duplicated file names.

---

### Post by nick_h on 2007-11-26
> **kpictjl said:**
> I'll have to figure out now how to test for duplicates.  I'm thinking I'll try to append "dup" at the end of all duplicated file names.
Use your find command with a shell script taking the filename as a parameter.  Have a look at the manual page for the *test* command for how to check if the file already exists in your destination directory.

---

### Post by kpictjl on 2007-11-26
The rub is that many of my files have the same name but different content.  I need something that will actually hash the file to determine i the content is duplicative prior to deleting. 

 Google picasa forums say it had an experimental utilily to delete duplicates but I can't find it.

---

### Post by kpictjl on 2007-11-26
fslint looks promising.   Anybody have any experience with it?
[http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)

---

### Post by nix4me on 2007-11-26
Use the gui search tool in the places menu.  Search by extension:  *.avi or *.pdf or whatever.  Then just drag the files from the search result into a folder in your home dir.

Thats the easiest way i can think of.

nix4me

---

### Post by kpictjl on 2007-11-26
> **nix4me said:**
> Use the gui search tool in the places menu.  Search by extension:  *.avi or *.pdf or whatever.  Then just drag the files from the search result into a folder in your home dir.
nix4me
This won't handle duplicate file names will it?

---

