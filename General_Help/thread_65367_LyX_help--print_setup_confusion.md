---
title: "LyX help--print setup confusion"
date: 2005-09-13
forum: General Help
---

### Post by DW5 on 2005-09-13
I'm trying to set up Lyx on my machine, but am too newbie to get the printing set up right.  I followed the lyx documentation about using teTexconfig to get my printer printing properly (using lpr -PStylus-C84 as command--I'm printing to an Epson Stylus C-83 and that's what lpstat -a reveals).  I can print the test page from the teTexconfig.

The Lyx documentation then says to launch the preferenced dialog and tell Lyx to use the configuration by setting the adapt_output and Spool_command.  

I click on preferences and see a check box saying adapt_output.  I check it.  I see print command: dvips.  I leave it alone. I see spool_command: 

/usr/share/lyx/scripts/lyxprint.sh

I leave it alone, click apply, ok. Try to print and nothing happens.  Hmm.  I think I might have to change the spool_command to something, but don't know quite what and the Lyx documentation is a bit vague on that.

I'm also thinking as a side thought--I wonder if this can just print to a cups printer and let cups spool the job?  If so, how?

Curiously

DW

---

### Post by DW5 on 2005-09-14
I have narrowed this problem down some by following some of the archived discussion.  I know several things. 

1) lyx is generating a dvi file to be printed in its /tmp directory as it is supposed to.
2) the command dvips (as specified in lyx) will print the generated dvi file when submitted via the command line
3) using tetexconfig I have set up my Epson Stylus-C84 to print properly.  It work when I print a test page from the texconfig frontend
4) I have the latest debian releases for tetex and lyx
5) when I run lyx -dbg I see this message when I try to print:

```
This is dvips(k) 5.92b Copyright 2002 Radical Eye Software (www.radicaleye.com)
' TeX output 2005.09.14:1048' -> lyxsample.ps
<texc.pro>. [1]
lpr: error - unable to access "Stylus-C84" - No such file or directory
``` 

I don't know how to interpret this.  The printer Stylus-C84, a definition for which I set up in tetex (and which works there) is also a printer known to my system. At least it is when I run lpstat -a as seen here:

```
dwilliam@DUUbuntu:~$ lpstat -a
Aficio-1060-PS accepting requests since Jan 01 00:00
Stylus-C84 accepting requests since Jan 01 00:00
``` 

Any ideas?

DW

---

### Post by DW5 on 2005-09-14
I have solved the lyx printer problem I had, but in a way that I did not like.

I checked the /usr/share/lyx/scripts/lyxprint.sh file and it called for kprinter. 

Hmm, I thought.  So, despite the fact that I would rather use gnome features, I downloaded kde so that I could get its kprinter.  After I installed it, I tried printing from lyx and bang  it worked.

Perhaps one of the gnome gurus can look at this script and tell me how to do it with regular gnomish ubuntu...

```
#!/bin/sh

test -x /usr/bin/kprinter || exec lpr "$@" || exit 1

TMPFILE=`mktemp -q -t lyxview.XXXXXXXXXX` || exec lpr "$@" || exit 1

trap "rm -f $TMPFILE; exit 1" HUP INT QUIT TERM

kprinter "$@" 2> $TMPFILE

if [ $? -eq 1 ] && grep -qs "cannot connect to X server" $TMPFILE; then
    lpr "$@"
fi

rm -f $TMPFILE
```

---

