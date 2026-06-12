---
title: "string manipulation"
date: 2012-10-26
forum: General Help
---

### Post by Drenriza on 2012-10-26
Hi guys.

Anyone who can tell me how i can cut this string

[ftp://aaaaa:bbbbbb@cccccc.cc.cc/ddddddd-2.5/eeeee](ftp://aaaaa:bbbbbb@cccccc.cc.cc/ddddddd-2.5/eeeee)

to

aaaaa:bbbbbb@cccccc.cc.cc
dddddddd-2.5
eeeee

i dont need the ftp:// part. I have tried to use cut, but i could not get the correct result.
Because i would like to have the lines spitted onto a new line, and with cut i could only get it to
split them to the same line.

Thanks on advance.

---

### Post by MG&amp;TL on 2012-10-26
Using *cut  *and *tr*:

```
echo ftp://aaaaa:bbbbbb@cccccc.cc.cc/ddddddd-2.5/eeeee | cut -c 7- | tr '/' '\n'
```...hope that helps. :)

Explanation:

echo ftp[...]  -[I]just replace this with wherever you get the string from.

[/I]cut -c 7-    -[I]cut any characters from the 7th onwards.

[/I]tr '/' '\n'    -*replace any / character with a newline.*

---

### Post by steeldriver on 2012-10-26
... or sed

```
echo "ftp://aaaaa:bbbbbb@cccccc.cc.cc/ddddddd-2.5/eeeee" | sed -r 's#ftp://([^/]*)/.*#\1#'
aaaaa:bbbbbb@cccccc.cc.cc
```Of course languages like php have explicit url parsing functions

[http://www.php.net/manual/en/function.parse-url.php](http://www.php.net/manual/en/function.parse-url.php)

---

### Post by codemaniac on 2012-10-26
```
echo "ftp://aaaaa:bbbbbb@cccccc.cc.cc/ddddddd-2.5/eeeee" | awk -F"/" '{printf $3"\n"$4"\n"$5}
```

---

### Post by Drenriza on 2012-10-26
Thanks guys.

Here is a lot i can use and hopefully learn from :)

Kind regards.

---

### Post by Vaphell on 2012-10-26
... or
```
string='...'
echo ${string/.cc\/*/.cc}

```

---

