---
title: "Concatenation problem (command line)"
date: 2008-02-03
forum: General Help
---

### Post by ntowakbh on 2008-02-03
I've gotten extremely close with these lines:

```
$(echo "blah" && echo "blah" | cat)
```
Which gives
"blah blah" my problem is the space between the strings.

The other is without $():
```
echo "blah" && echo "blah" | cat
```
Which gives
"blah
blah" my problem with this is the new line.

Could anyone tell me how to concatenate strings without a space or new line? (Example: "blahblah")

Thanks in advance!

---

### Post by lakris61 on 2008-02-03
Some implementations of echo support the option -n for "no newline", some use the form echo 'blah\c', try both.

---

### Post by jrib on 2008-02-03
"foo""bar" concatenates

There's no need for echo in your examples.  If this does not work, then can you be more specific as to what you want to do?

---

### Post by ntowakbh on 2008-02-03
> **_jason said:**
> "foo""bar" concatenates

There's no need for echo in your examples.  If this does not work, then can you be more specific as to what you want to do?

Thanks that worked.

I am trying to make my own script that converts .m4a files to .mp3 files.  Now I just have to figure out how to keep the for loop from messing up by breaking the spaces in filenames into new lines.

---

