---
title: "simple way to wildcard copy"
date: 2007-03-11
forum: General Help
---

### Post by undecidable on 2007-03-11
Is there any way to simply do a wildcard copy?
	eg	cp  filea*  fileb*

This will not work with cp because it only accepts a dir as the 'dest' argument
if the src is wildcarded.

The 'rename' command which is available in Ubuntu
will allow me to do wildcard renames
using perl expressions,
so I could copy to a dir, rename, then move back.
But is there a 1-step command?

There appears to be a wildcard-based 'mmv' command that will do it
([http://www.die.net/doc/linux/man/man1/mmv.1.html](http://www.die.net/doc/linux/man/man1/mmv.1.html))
but this command does not appear to be in Ubuntu.
(I am new to Linux - do different distributions have different shell commands?)

thanks for any assistance / insights.
I am testing Dapper 6.05.

---

### Post by WW on 2007-03-11
Nevermind... my suggestion didn't do what you wanted.

---

### Post by undecidable on 2007-03-11
Apology for being unclear.

I know how to use rename, but it just 'renames' files,
so you lose the 'original'.

I want to create a new copy of a set of files with a different name,
  eg f01 -> x01,  f02 -> x02,...
so I end up with both the old set f01, f02,... 
and the new set  x01, x02,...

So I am looking for something like the old dos wildcard copy,
which for the example above would be:
  copy f* x*
which I think for mmv would be:
  mmv -c f* x#1

---

### Post by WW on 2007-03-11
**mmv** is available in the universe repository: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mmv&searchon=names&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mmv&searchon=names&version=all&release=all)

---

### Post by undecidable on 2007-03-11
WW

Thanks very much - very helpful.  I had assumed that as it was in the Man pages of other distributions, it was a standard shell command, and as it wasn't in Ubuntu's Man pages, it was not available in Ub.   

Will get it and try it.

---

### Post by undecidable on 2007-03-14
I just want to confim for anyone else looking for this, that mmv enables wildcard copy and rename .  cp and mv do not, rename does, but uses perl expressions.

by wildcard copy I mean simpel example:  x01, x02, x03...  copy to z01, z02, z03...

mmv is not there by default but can be installed from Universe.

---

### Post by cssutto on 2007-06-25
I have looked at the man page for mmv and it confuses me.

I want to combine .mov files into one.

Assume a series of quickview .mov files,   Autoshow1, autoshow2, autoshow3 arranged in their directory in that order.

What would the mmv command be to copy all of them into one file renamed autoshow?

I would rather copy than move so that in the event of a disaster, the originals could be accessed for another attempt.

CSSJR

---

### Post by thePsychologist on 2007-06-25
But I don't get what's wrong with rename. For your example:

> by wildcard copy I mean simpel example: x01, x02, x03... copy to z01, z02, z03...

If you use:

```
rename 's/^x/z/' *
```

Does it all in one step.

---

### Post by cssutto on 2007-06-25
I figured it out.

Append is the magic word.

mmv -a "/directory/subdir/video/autoshow*" autoshow.mov

does it.

CSSJR

---

### Post by cssutto on 2007-06-25
OOPS!!

It appended them to the new file, but only the first is able to be played.

CSSJR

---

### Post by undecidable on 2007-06-25
cssutto

mmv does a 'raw' append, which works ok for text files.
But most other file types, eg .mov, have header info (at the beginning)
describing the contents.
Youy cannot just concatenate these types of files.
Instead you will need a specialist program to read the two movies, 
combine into a new movie then save.
Similarly you cant just concatenate 2 spreadsheets.

---

