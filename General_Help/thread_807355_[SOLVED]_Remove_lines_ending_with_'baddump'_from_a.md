---
title: "[SOLVED] Remove lines ending with 'baddump' from a text file?"
date: 2008-05-25
forum: General Help
---

### Post by dorkdork777 on 2008-05-25
I've got a simple text file with almost 3000 lines of information, but a load of the lines end with "baddump" (minus the quotes). I need those lines to be removed completely, hopefully without leaving any blank lines behind. I've searched, but I can't find a way to do this. (Besides manually of course, but that would crush my soul).

The lines that need to be deleted are all different, besides that they all end with "baddump".

Any links to apps or terminal commands that could remove those lines for me would be very helpful! :)

---

### Post by drs305 on 2008-05-25
For brevity, latna has a slick solution in the next post!

What you are looking for is a script running the **sed** command. I don't know enough about it to give you the command sequence, but while you are waiting for some expert advice if you do a search for "sed 'remove any line with' " you will find some good examples. You can read up on the command to become familiar with what advice you will hopefully receive. I don't think this would be a difficult script to make yourself if you found a couple of good examples.

---

### Post by latna on 2008-05-25
Try this:

```
grep -v "baddump$" name_of_file
```

The $ character at the end tells grep to search for lines that end with baddump. The -v option tell grep to search for the inverse match, meaning lines that don't end with baddump. If this gives the output that you like then:

```
grep -v "baddump$" name_of_file > new_file
```

For completeness, this would search for lines beginning with baddump.

```
grep "^baddump" name_of_file
```

---

### Post by ibuclaw on 2008-05-25
[EDIT]
Oops, someone beat me to it... ;)

Good Job Latna!

[OLDPOST]
grep will do just as well.
Bonus Points: it's more human readable too.
```
grep -v "baddump" /path/to/file > /path/to/newfile
```

Regards
Iain

---

### Post by ibuclaw on 2008-05-25
Well... Just for sed's sake, here's another implementation:
```
sed -i '/baddump$/d' name_of_file
```

Regards
Iain

---

### Post by dorkdork777 on 2008-05-25
Brilliant - grep worked perfectly! Thanks to you both! :D

---

