---
title: "Bash match date pattern: YYYY.MM.DD-HH.MM.SS"
date: 2007-10-30
forum: General Help
---

### Post by Meson on 2007-10-30
I'm working on a backup script that appends a timestamp to files but I need to ignore already stamped files, rather than appending timestamp upon timestamp on each backup routine.

The suffix I'm putting on the end of each file is __YYYY.MM.DD-HH.MM.DD So I'd like to match this.

Currently I have something like:
backup_expr="*__+[0-9]+[0-9]+[0-9]+[0-9].+[0-1]+[0-9].+[0-9]+[0-9]-+[0-9]+[0-9].+[0-9]+[0-9].+[0-9]+[0-9]"

Is there a easier way in bash to match a number of specified digits?  So a 4 digit number followed by a 2 digit, etc.  Also, I actually use periods, does bash see that . as a single wildcard.  Do I need to escape it?

Thanks

---

### Post by konig12 on 2007-10-30
Check out this page for a good description of regular expressions.  The details for bash might be slightly different but this should be pretty good.

[http://www.regular-expressions.info/reference.html](http://www.regular-expressions.info/reference.html)

from what I understand you want something more like:

backup_expr=".*__[\d]{4}\.[\d]{2}\.[\d]{2}\-[\d]{2}\.[\d]{2}\.[\d]{2}"

the "\d" represents any digit character, the {} specifies the number of times to match the given set, and you do need to escape the "." otherwise it will match any character.

Hope that works,
Andrew

---

### Post by Meson on 2007-10-30
yes that's exaclty what i want for a pearl style regex.... does bash follow the same conventions?  I was led to believe through my googling that it does not...

---

### Post by Meson on 2007-10-30
*__[0-9][0-9][0-9][0-9].[0-1][0-9].[0-3][0-9]-[0-2][0-9].[0-5][0-9].[0-5][0-9]

This works but i don't like the way it looks!

---

### Post by konig12 on 2007-10-30
How exaclty are you trying to do this? are you using the regex in grep or directly in bash?

---

### Post by Meson on 2007-10-30
The expression is used for the --exclude option of rsync.

---

### Post by konig12 on 2007-10-30
In that case I believe that there is no way to use the {#} style syntax.  I was thinking in terms of grep or perl matching, which has more functionality than the standard bash matching.  There may be a better way, but as far as I can tell, you will be best off just sticking with your pattern that works.

---

