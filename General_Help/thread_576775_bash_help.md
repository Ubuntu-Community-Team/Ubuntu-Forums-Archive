---
title: "bash help"
date: 2007-10-15
forum: General Help
---

### Post by midspot on 2007-10-15
I have a text file (actually an html file) that I want to parse out everything between the table tags only (including the tags themselves).

Is there any easy way to do this? I would think this would be real simple but it's proven to be a real headache over the last couple of hours...

thanks

---

### Post by r-mo on 2007-10-15
Have a look at the xmlstarlet package, sounds like it may do what you want, although it might not like it if it's not valid xhtml :s  Or use perl, it's simpler than bash for this kinda thing ;)

you might have more luck asking in the programming forum too ;)

---

### Post by stylishpants on 2007-10-15
I'm not clear on what you mean by "parse out".  Do you want to show only the stuff in the table tags, or everything but what's in the table tags?

If it's the former, you could use sgrep, like this: sgrep ' "<table>" .. "</table>" ' file.html

Example:
```


fhanson@fhanson:/tmp$ cat file.html
<html>
        <head>
                head text
        </head>
        <body>
                in body
                <table>
                        <tr><td>in table</td><td>table text</td>
                        <tr><td>in table</td><td>table text</td>
                </table>
                after table
        </body
</html>

fhanson@fhanson:/tmp$ sgrep '"<table>" .. "</table>"' file.html
<table>
                        <tr><td>in table</td><td>table text</td>
                        <tr><td>in table</td><td>table text</td>
                </table>


```

---

### Post by milosz.galazka on 2007-10-15
Try using ruby or python instead of bash to such things it will be a lot easier.

---

### Post by midspot on 2007-10-15
awesome! that works great!!!

except for one thing I can't seem to sort out now...

Is there anyway to run another grep command to remove the first <tr> tag (and its contents) from what is left?

thanks a bunch!

---

### Post by stylishpants on 2007-10-15
Well, you could use perl for that.

```

 sgrep '"<table>" .. "</table>"' file.html  | perl -e '$_=join("",<>); s#<tr>.*?</tr>##ms; print'
```

That should work whether or <tr> and </tr> are on the same line or not.

However, it will only remove the first <tr> ... </tr> in the entire sgrep output, not the first one in each table.  Is that what you want?

---

### Post by midspot on 2007-10-15
perfect, you da man!

---

