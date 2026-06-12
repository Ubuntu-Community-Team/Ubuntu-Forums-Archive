---
title: "Print (on paper) source code INCLUDING syntax highlighting for multiple files"
date: 2013-04-22
forum: General Help
---

### Post by HeXor0815 on 2013-04-22
Hello everyone!

I have several files of python code, which I need to print out (on paper), I know it sounds crazy, but I have to, for education...

In order to not open each file in a text editor and hit print, I use the command line argument

```
for $file in `ls <mydir>`; do lpr -P <printer> <file>; done
```

which works fine and the files are printed out. The problem now is, that this printed out version has of course no syntax highlighting anymore, which makes it hardly readable...

Of course I can easily achieve paper printed output with syntax highlighting by
```
for file in `ls`; do gedit $file; done
```
to open each file after another and then hit print in gedit, but this is very annoying for a large number of files...

Therefore the question is, whether there is a way to print source code INCLUDING syntax highlighting from the command line, without opening an editor.

Any help is very appreciated!

Cheers
HeXor

---

### Post by btindie on 2013-04-22
There's 'enscript' and 'highlight' in the repo.
[URL="http://blog.vinceliu.com/2008/06/printing-syntax-highlighted-source-code.html"]
http://blog.vinceliu.com/2008/06/printing-syntax-highlighted-source-code.html[/URL]

---

### Post by HeXor0815 on 2013-04-22
Thanks for the reply btinidie!
This sounds indeed like a solution I am searching for.

But when I use
```
$enscript --color=1 -Epython -P <printer> <pythonfile>
```
it returns
```
lp: Bad page-ranges values 0-0.
```

I found at
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=604961](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=604961)
that this is a known bug, because enscript uses lp instead of lpr, while lpr uses -P option to specify the printer, lp uses the -P option for the page range....

Using the aquivalent (according to man enscript) options -d or --printer results in the same problem!
Some workarounds change the lp command to lpr in the enscript config file, but I have no access rights there (working on terminal).

I think for my version
```
$enscript -VGNU Enscript 1.6.5.2
Copyright (C) 1995-2003, 2007, 2008, 2009, 2010 Free Software Foundation, Inc.
```
this is not fixed yet... Do you any workaround?


[COLOR=#ff0000][B]
EDIT:

[/B][/COLOR]Well I found a workaround for my self:
First create *.eps with syntax highlighting using enscript and then print the *.eps files using lpr
```
for FILE in `ls <INPUTDIR>`; do
  enscript <FILE> --color=1 -Epython -o <OUTFILE>
done

for FILE in `ls <OUTPUTDIR>`; do
  lpr -P <PRINTERNAME> <FILE>
done
```

Not the most elegant, but working solution ;-)
Thanks for the hint for enscript!

---

