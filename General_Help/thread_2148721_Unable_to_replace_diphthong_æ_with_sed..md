---
title: "Unable to replace diphthong æ with sed."
date: 2013-05-26
forum: General Help
---

### Post by Peterinall on 2013-05-26
Hello there,
     I have large files with diphthong characters  and want to replace them with alphabets. I have tried the below command without any result
```
sed -r 's:æ:a:g' <in >out
```
I am pasting it on [paste.ubuntu.com]("http://paste.ubuntu.com/5703500/") as html files are not allowed, . 

Any input is highly appreciated.

---

### Post by sudodus on 2013-05-26
That command works for me. Maybe you don't have æ, but some code, that is printed as æ. Check the source, the html file without parsing it as html and/or without interpreting anything!

---

### Post by steeldriver on 2013-05-26
I had a look at your pastebin, and the ae ligatures appear to be UTF-8 e.g.

U+00E6    æ    c3 a6    LATIN SMALL LETTER AE

You could try

```
sed -e $'s/\xc3\xa6/ae/g'
```

(which seemed to work for me) or if you want to get rid of other UTF-8 characters, there's iconv:

```
iconv -f utf8 -t ascii//TRANSLIT -o *newfile**.html **yourfile**.html*
```

however there seems to be one invalid UTF-8 character in 'diarrh--a' - it looks like c2 9c, but I'm guessing it should be c5 93 (ligature oe) - so you could precede the iconv with a sed for that specific 2-byte character:

```
sed $'s/\xc2\x9c/oe/g' *yourfile**.html* | iconv -f utf8 -t ascii//TRANSLIT -o *newfile**.html*
```

or even

```
sed $'s/\xc2\x9c/\xc5\x93/g'* yourfile**.html* | iconv -f utf8 -t ascii//TRANSLIT -o *newfile**.html*
```

to correct the oe ligature (somewhat pointless) and then replace all the UTF-8 with iconv

---

