---
title: "capture dsssl text"
date: 2013-12-08
forum: General Help
---

### Post by evaristegalois on 2013-12-08
I have a dictionary file in *.dsl.dz format. I used dictzip to unzip and now have a *.dsl file. If I open it in vi or emacs, it looks like this:

```
#NAME "Essential English Dictionary v1.00riz"
#INDEX_LANGUAGE "English"
#CONTENTS_LANGUAGE "English"

'hood
[m1][p]noun[/p][/m]
[m2] [trn]*(slang)* a neighborhood[/trn][/m]
's Gravenhage
[m1][p]noun[/p][/m]
[m2] [trn]the site of the royal residence and the de facto capital in the western part of the Netherlands[/trn]; [trn]seat of the International Court of Justice[/trn][/m]
'tween
[m1][p]adverb[/p][/m]
[m2] [trn]in between[/trn][/m]
[500,000 more lines after this]
```

vi and emacs are converting this file from binary (?) to plain text for display (emacs, for example, is in DSSSL abbrev mode), but I want to change the file itself to be a plain text file.

I could just grab the contents line by line and paste them into another file, but with 500,000 lines this turns out to be quite the task for the computer (would take many hours). Is there a way to do this more elegantly?

---

### Post by steeldriver on 2013-12-09
Based on a little bit of searching around, it looks like the .dsl format is UTF-16. For example (I could only find an English-Urdu file)

```

$ file English-to-Urdu-Dictionary-v2.00-utf16.dsl 
English-to-Urdu-Dictionary-v2.00-utf16.dsl: Little-endian UTF-16 Unicode text

```

IF so, you *should* be able to convert it using the 'iconv' command-line utility. *If* the contents are representable in ASCII then something like

```

iconv -f UTF-16 -t ASCII -o *outfile* *dictionary-utf16.dsl*

```

where *dictionary-utf16.dsl* is the name of the dsl file and *outfile* is the name of the file you want it to go in. If you get something like this

```

$ iconv -f UTF-16 -t ASCII -o English-to-Urdu-Dictionary-v2.00-ASCII.txt English-to-Urdu-Dictionary-v2.00-utf16.dsl 
** iconv: illegal input sequence at position 250**

```

then that means the contents can't be converted to pure ASCII text - you can either add a '-c' switch to skip untranslatable characters

```

iconv -f UTF-16 -t ASCII **-c** -o English-to-Urdu-Dictionary-v2.00-ASCII.txt English-to-Urdu-Dictionary-v2.00-utf16.dsl

```

or try UTF-8

```

iconv -f UTF-16 **-t UTF-8** -o English-to-Urdu-Dictionary-v2.00-utf8.txt English-to-Urdu-Dictionary-v2.00-utf16.dsl

```

You could probably also do it directly from vi as follows

[LIST=1]
[*]enter command mode (**Esc :**)
[*]type the command **set fileencoding=ascii**
[*]write and quit (**:wq**)
[/LIST]

Almost certainly emacs can do the same, but I don't know the command sequence

---

### Post by evaristegalois on 2013-12-09
Thank you!

---

