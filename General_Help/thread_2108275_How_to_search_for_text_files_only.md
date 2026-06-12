---
title: "How to search for text files only ?"
date: 2013-01-24
forum: General Help
---

### Post by cogset on 2013-01-24
I've found out this is not as easy as I thought at first,on the other OS we  know,all text files usually end with the .txt extension,which makes searching  for them quite straightforward-no such thing on Linux,so how can I  search for text files in a directory where they may be (and actually  are) intermixed with all kinds of other files ? Typically (despite using Tomboy as well) I take lots of unorganized notes as short text  files,which then  end up somewhere in my home directory,then at some  point I'd want to grep for a search term or string among all these  files,but there's all sorts of other files in between,so a simple  command the likes of **find ~ -type f |grep [string]** won't cut  it,obviously ;)

---

### Post by Adam_GUI on 2013-01-24
Catfish is a great GUI tool for searching local files.
It's in the repos.  Search Synaptic or Software Center or "sudo apt-get install catfish".

Set search folder to /home/<Your_User_Name_Here>
Search for *.foo
All file types "Foo" will show up in Catfish's search results.

It also has a filter for file types.  If you want just text files for a string, say, "Resume."  All related text type files will appear in the field.

Also, create a directory for notes!  /home/USER/Documents/NOTES would solve a lot of your headache and help narrow what you're searching for.
You can change Tomboy's default save directory under Preferences > Synchronization.

Unless you're asking for a way to search a text string within the body of a set of text files.  It's unclear what you're really asking for.

---

### Post by slickymaster on 2013-01-24
```
find . -exec sh -c "file -b --mime-type {} | grep -q '^text/'" \; -print
```

---

### Post by prodigy_ on 2013-01-24
> **cogset said:**
> on the other OS we  know,all text files end with the .txt extension
Unfortunately that's not true. Extension is a convenience tool, it doesn't magically define file type. It can be deliberately misleading or even completely absent.

---

### Post by cogset on 2013-01-25
Thanks folks for all the insights,not least the simple advice of creating a dedicated directory just for notes:I'm now giving Catfish a try,although the string suggested above 
```
find . -exec sh -c "file -b --mime-type {} | grep -q '^text/'" \; -print
```is probably what I was after,if only I could understand what it actually does in detail ;).
I also probably didn't explain myself very well,so I'll try to do better this time-the typical scenario would be like that:I have an habit of taking lots of short notes as text files scattered around my home directory (/home itself,Documents,Desktop and some subdirectories-I know,that's not very tidy,paradoxically I do this in the effort of avoiding to  clutter Tomboy with possibly unworthy stuff),then at some point remember that one of those notes was about,say,"firefox bookmarks",now I'd like to grep for this exact string amongst  *all*  text files in my entire home directory,and that's the hard part,as there's no extension identifying them as text files.

---

### Post by Vaphell on 2013-01-25
```
find . **-exec sh -c "file -b --mime-type {} | grep -q '^text/'" \;** *-print*
```
=
```
find <current_dir> **(get mime of the file and check if 'text/' is in it)** *-print file*
```

bold part is responsible for checking mimetype
*-exec* is used to embed external commands in *find*, sh -c opens a subshell where *file -b --mimetype {}* is executed ({} is a placeholder for the currently processed filename)
```
$ file -b --mime-type sample.txt
text/plain
$ file -b --mime-type test.c
text/x-c

```
that output is passed to *grep* to figure out if the phrase **text/** appears in it at the very beginning. Grep ends with exit code of 0 (success) or 1 (failure). *-print* part that prints out the current {} depends on that exit code: success = execute, failure = skip. In short the whole *-exec sh -c* acts here as a condition controlling the *-print* part

---

### Post by dragonfly41 on 2013-01-25
> now I'd like to grep for this exact string amongst  *all*  text files in my entire home directory,and that's the hard part

If it is string matching you want throughout *all* text files then I would recommend trying [COLOR=Navy]Recoll[/COLOR] package which is found in Ubuntu Software Centre.   

First it has to index all your files.

---

### Post by elliotn on 2013-01-25
I just do```
locate *.txt
```

---

### Post by dragonfly41 on 2013-01-25
that doesn't find strings within *.txt

---

### Post by slickymaster on 2013-01-29
> **Vaphell said:**
> ```
find . **-exec sh -c "file -b --mime-type {} | grep -q '^text/'" \;** *-print*
```
=
```
find <current_dir> **(get mime of the file and check if 'text/' is in it)** *-print file*
```

bold part is responsible for checking mimetype
*-exec* is used to embed external commands in *find*, sh -c opens a subshell where *file -b --mimetype {}* is executed ({} is a placeholder for the currently processed filename)
```
$ file -b --mime-type sample.txt
text/plain
$ file -b --mime-type test.c
text/x-c

```
that output is passed to *grep* to figure out if the phrase **text/** appears in it at the very beginning. Grep ends with exit code of 0 (success) or 1 (failure). *-print* part that prints out the current {} depends on that exit code: success = execute, failure = skip. In short the whole *-exec sh -c* acts here as a condition controlling the *-print* part

Congratulations on a clear, succinct and perfect explanation.

---

### Post by cogset on 2013-01-29
Indeed ;),thank you very much for that explanation.

---

