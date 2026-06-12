---
title: "[SOLVED] A useful search tool?"
date: 2008-04-27
forum: General Help
---

### Post by WitchCraft on 2008-04-27
I wanted to know if there is any useful search tool that i can install that is like the little Microsoft Search tools where you can search a directory (and all its subdirectories) for a filename, or a file's content, and if content is found, lists' the file only once ?

I know i can use locate and find, and grep, but they aren't quite what I am looking for...

It would also be nice if that tools integrates a search option in the context menu in nautilus.

And with Google desktop search, i can, AFAIK, not search for filenames...

---

### Post by olskar on 2008-04-27
Tried the search that is in you placesmenu?

---

### Post by mali2297 on 2008-04-27
[Catfish?]("http://software.twotoasts.de/?page=catfish")

---

### Post by WitchCraft on 2008-04-27
> **olskar said:**
> 
Tried the search that is in you placesmenu?


You mean this blue one top-right in the toolbar of nautilus?
Yes, but it doesn't work for me...
If I for example go in the root folder of a larger software project, and search for clientActive_t and hit enter, it doesn't return anything, neither does it for a filename...

---

### Post by ghost_ryder35 on 2008-04-27
This one is nice looking for commands or binaries, man pages
```

whereis

```

---

### Post by WitchCraft on 2008-04-27
> **mali2297 said:**
> [Catfish?]("http://software.twotoasts.de/?page=catfish")

I installed catfish, but it doesn't find anything, neither...

---

### Post by mali2297 on 2008-04-27
> **WitchCraft said:**
> I installed catfish, but it doesn't find anything, neither...

If you use **locate** as backend, you might need to update the database. See if you can do it from the program itself, otherwise use the terminal:
```

sudo updatedb

```
Also note that Linux most often is case-sensitive.

---

### Post by WitchCraft on 2008-04-27
> **ghost_ryder35 said:**
> This one is nice looking for commands or binaries, man pages
```

whereis

```

This is definitely not what I am looking for, but it might come in handy at another time.

---

### Post by ghost_ryder35 on 2008-04-27
didnt gutsy come with one on the top toolbar?

---

### Post by WitchCraft on 2008-04-27
> **mali2297 said:**
> 
If you use **locate** as backend, you might need to update the database. See if you can do it from the program itself, otherwise use the terminal:
```

sudo updatedb

```


Ah, that helped, thanks.

> **mali2297 said:**
> 
Also note that Linux most often is case-sensitive.


This I know since 1999 when I learned it the hard way when I installed Debian, and typed ttys0 instead of ttyS0 for installing the mouse...




But still, now seaching for filenames works, but what about searching for contents? I select fulltext search and nothing is found...
Why do I get fatal errors when I try slocate, doodle, beagle and strigi? I installed all of them... and why does pinot find nothing, when locate does?

---

### Post by WitchCraft on 2008-04-27
> **ghost_ryder35 said:**
> didnt gutsy come with one on the top toolbar?

Yes, it comes with a search icon, but the program behind it does not seem to work...

---

### Post by WitchCraft on 2008-04-27
> **WitchCraft said:**
> Yes, it comes with a search icon, but the program behind it does not seem to work...

Correction: Oh, ah, no stars in the search bar in nautilus when searching for filenames ;-)

But you can't search for text in a file, can't you?

---

### Post by WitchCraft on 2008-04-27
> **olskar said:**
> 
Tried the search that is in you placesmenu?


Oh ah, no not in nautilus in "Places"

Didn't even see that, yet. Yes, this works, many thanks!

---

### Post by mali2297 on 2008-04-27
In Ubuntu, **locate** is really the same as **slocate**, so that shouldn't matter. 

The tool locate will only search file names, but perhaps some of the other backends can search contents. From the command line, you can use **grep** to search inside files:
```

grep word *

```
will search for *word* in all files in the current directory.

---

### Post by WitchCraft on 2008-04-27
> **mali2297 said:**
> In Ubuntu, **locate** is really the same as **slocate**, so that shouldn't matter. 

The tool locate will only search file names, but perhaps some of the other backends can search contents. From the command line, you can use **grep** to search inside files:
```

grep word *

```
will search for *word* in all files in the current directory.

Yes, as said i know grep.

It's generally a good tool, but there are some shortcomings:
it does only search in the current directory, or the directories indicated, but not in ALL subdirectories, as far as I know.

Furthermore, grep gives you EVERY line in a file that matches. This is very useful in a smaller project, but in a large project it is very annoying if you have very many matches in a few files, and very few matches in the one or two files that are of interest. So you have to look through an entire list, in my case most of the time huge list, with the possibily of just looking the one file you actually search for over. So I really want it to only give the filename once for every match.

The search on places works this way, so my problem is solved.

But I think one could also redirect the grep output to sed, and then filter it, or not?

---

### Post by dbera on 2008-04-27
You could try using blocate !
[http://beagle-project.org/Blocate](http://beagle-project.org/Blocate)

---

### Post by mali2297 on 2008-04-28
> **WitchCraft said:**
> 
It's generally a good tool, but there are some shortcomings:
it does only search in the current directory, or the directories indicated, but not in ALL subdirectories, as far as I know.

Furthermore, grep gives you EVERY line in a file that matches. This is very useful in a smaller project, but in a large project it is very annoying if you have very many matches in a few files, and very few matches in the one or two files that are of interest. So you have to look through an entire list, in my case most of the time huge list, with the possibily of just looking the one file you actually search for over. So I really want it to only give the filename once for every match.

The search on places works this way, so my problem is solved.

But I think one could also redirect the grep output to sed, and then filter it, or not?

Use the flags **-l** to just print the names of matching files and **-r** for recursive search through subdirectories
```

grep -lr word *

```
There are more options available, check **man grep**.

---

### Post by Nchalada on 2008-06-11
the terminal search's are good n all, but the one in nautilus doesn't work...

it *may* because i've turned indexing off... but still, it should work, it does in windows :S


Any help?

---

