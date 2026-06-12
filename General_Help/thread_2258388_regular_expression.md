---
title: "regular expression"
date: 2014-12-27
forum: General Help
---

### Post by hatef2 on 2014-12-27
Hi ,
I need to replace all of these expressions that located between double-quotes from a .txt or .odt file:
" [" to "["
"[ " to "["
"] " to "]"
" ]" to "]"
". " to "."
" ." to "."
", " to ","
" ," to ","
it could happen that one replace once all these expressions by a common program but still you can find some of these expressions due to the space character: " ".
so I need a script or something that not only replace these expressions but work as recursively to avoid the mentioned problem
solution?

TNx in Advance.

---

### Post by steeldriver on 2014-12-27
For plain text files, you could use perl's *lookaround* capabilities to replace spaces that are either followed by or preceded by any one of your punctuation characters:

```

perl -pe 's/\s(?=[,[\].])//g; s/(?<=[,[\].])\s//g;' file

```

For odt files it will be more complicated as iirc the text is saved as compressed XML.

---

### Post by hatef2 on 2014-12-27
Thanks. :)
could I ask you to explain a bit this code , cause in fact those symbols that I mentioned is not my complete list, if I can understand what exactly this code does, maybe I can expand it as what I exactly want

---

### Post by hatef2 on 2014-12-27
> **steeldriver said:**
> For plain text files, you could use perl's *lookaround* capabilities to replace spaces that are either followed by or preceded by any one of your punctuation characters:

```

perl -pe 's/\s(?=[,[\].])//g; s/(?<=[,[\].])\s//g;' file

```

For odt files it will be more complicated as iirc the text is saved as compressed XML.

It does not work for me, 
Consider this :
```

"                    Hello Jack       [                     f      .                        v.       d.       ]   "
```
the result of ur code is:
```

"                    Hello Jack      [                    f     .                       v.      d.     ]  "
```
I need some thing that gives me this:
"Hello Jack[f.v.d.]"

---

### Post by steeldriver on 2014-12-27
The expression I posted removes exactly one space - based on your original post.

If you want to remove any contiguous whitespace either side of your listed punctuation characters, replace \s by \s+

```

perl -pe 's/[COLOR=#0000ff]**\s+**[/COLOR](?=[,[\].])//g; s/(?<=[,[\].])[COLOR=#0000ff]**\s+**[/COLOR]//g;'

```

Note that will replace newlines as well - if you only want to replace horizontal whitespace, you can use \h instead:

```

perl -pe 's/[COLOR=#0000ff]**\h+**[/COLOR](?=[,[\].])//g; s/(?<=[,[\].])[COLOR=#0000ff]**\h+**[/COLOR]//g;'

```

Testing:

```

$ echo "                    Hello Jack       [                     f      .                        v.       d.       ]   " | perl -pe 's/\h+(?=[,[\].])//g; s/(?<=[,[\].])\h+//g;'
                    Hello Jack[f.v.d.]

```

If you also want to remove leading horizontal whitespace you can add

```

perl -pe '[COLOR=#0000ff]**s/^\h+//;**[/COLOR] s/\h+(?=[,[\].])//g; s/(?<=[,[\].])\h+//g;'

```

---

### Post by schragge on 2014-12-27
> **hatef2 said:**
> in fact those symbols that I mentioned is not my complete list
Then you should explain what symbols make up your list. E.g. this will remove horizontal space before and after non-word characters, i.e. anything that is not alphanumerics or underscore, and sqeeze long runs of blanks between words into one:
```
sed -r 's/[ \t]*(\W)/\1/g;s/(\W)[ \t]*/\1/g'
```

---

