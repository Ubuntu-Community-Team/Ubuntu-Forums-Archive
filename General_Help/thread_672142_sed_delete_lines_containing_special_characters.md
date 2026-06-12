---
title: "sed delete lines containing special characters"
date: 2008-01-19
forum: General Help
---

### Post by jazzor on 2008-01-19
I have a file with a list of directories, a snippet of which looks like this:

/usr/share/myfolder
/usr/share/someotherfolder
/opt/anotherfolder
/root/afolder

And in a script i want to be able to delete such lines from the file, most likely using SED.
Now, normally it would be done by something like this: sed -i "/myregexpression/d" myfile, and in a script would be: sed -i "/$MYVAR/d" myfile.

This doesnt work now because $MYVAR contains slashes which ofcourse need to be escaped. So either I have to escape the slashes somehow in $MYVAR or otherwise tell sed to accept $MYVAR as a literal. So any suggestions as to how I can work this out?

---

### Post by dagnabit dang doohickey on 2008-01-19
Use a character other than slash as the delimiter:
```
sed -i "#$MYVAR#d"
```
Edit: This command won't work. Jump two posts down.

---

### Post by dagnabit dang doohickey on 2008-01-19
Scratch my last post.

I ran a bunch of tests and, according to the results, it seems that when using sed delete the delimiter cannot be changed. It appears the sed delimiter can only be changed when the sed command appears at the beginning of the sed script (ex. s/// and y///).

To get around the problem of using sed delete with values that contain slashes, use sed with two commands:
```
sed -i -e "s#$MYVAR##" -e '/^$/d'
```

---

### Post by jazzor on 2008-01-19
Thanks for your posts. In fact, your idea of using a different delimiter is correct, but it needs a "\" before the delimiter for deletion, so the correct command is something like this:

sed -i "\#$MYVAR#d" myfile

Hope this helps others too.

---

### Post by dagnabit dang doohickey on 2008-01-19
Glad you figured that out. Only being able to change the delimiter for some sed commands didn't make sense.

Here's the bit about about using the preceeding backslash in the sed man page for anyone that cares.
```

\**c**regexp**c**
         Match lines matching the regular expression regexp.  The  c  may
         be any character.

```

---

