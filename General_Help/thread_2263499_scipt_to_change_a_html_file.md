---
title: "scipt to change a html file"
date: 2015-02-01
forum: General Help
---

### Post by hamed.obaidy on 2015-02-01
Hello, all

I am mostly a GUI user and do not know much about shell scripting. The problem I have is that I need a shell script that searches for all html files in a folder and for each file that is found replace 
```
<html lang="en">
```
to
```
<html lang="fa" dir="rtl">
```

First is it possible to do such a thing in shell, and second how can be done.

Thank you

---

### Post by Lars Noodén on 2015-02-01
It can be done with a perl one-liner.

```

perl -pi.bak -e 's/<html lang="en">/<html lang="fa">/' *.html

```

The **-p** means wrap the executable part in a loop, passing input to the default variable, $_
The **-e** means execute the following perl code.  s/// is a substitution and applied to the default variable, $_
The **-i** means save the original file, if something is changed, with the following extension.

For all run-time options in perl see the manual page for perlrun:
[http://manpages.ubuntu.com/manpages/trusty/en/man1/perlrun.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlrun.1.html)

For all the regular expression information, see the manual page for perlre, though you've probably seen PCRE before elsewhere
[http://manpages.ubuntu.com/manpages/trusty/en/man1/perlre.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlre.1.html)

---

### Post by hamed.obaidy on 2015-02-01
Very simple and neat. Thank you.
I should expend more time to learn scripting.=d>=d>=d>

---

