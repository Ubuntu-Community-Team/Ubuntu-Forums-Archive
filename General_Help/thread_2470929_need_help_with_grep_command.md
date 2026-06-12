---
title: "need help with grep command"
date: 2022-01-16
forum: General Help
---

### Post by lance bermudez on 2022-01-16
how to I use the grep command in my bash script? I have a file that I want to grep.
```

grep 'TODAY' weathertext5.txt

```
I only get the first line some time this line can go over more that one line. The number of lines have no set number. The next line starts with TONIGHT so how to I use grep to get the line from TODAY to TONIGHT.

---

### Post by HermanAB on 2022-01-17
$ man grep

---

### Post by The Cog on 2022-01-17
So I'm guessing the file can look a bit like this - am I right?
> TODAY will be cloudy, chilly,
with lots of volcanic ash
and a sulphurous smell
TONIGHT
will be dark, chilly,
with lots of volcanic ash
and a sulphurous smell
Try one of these two:
```
awk '/^TODAY/{want=1} /^TONIGHT/{want=0} want' weathertext5.txt
sed -n '/^TODAY/,/^TONIGHT/{/^TONIGHT/!p}' weathertext5.txt
```
Thanks to [https://stackoverflow.com/questions/38972736/how-to-print-lines-between-two-patterns-inclusive-or-exclusive-in-sed-awk-or](https://stackoverflow.com/questions/38972736/how-to-print-lines-between-two-patterns-inclusive-or-exclusive-in-sed-awk-or)
Sed line corrected after error pointed out by schragge.

---

### Post by schragge on 2022-01-17
> **The Cog said:**
> 
```
sed -n '/^TODAY/,/^TONIGHT/{/^[color=red]TODAY[/color]/!p}' weathertext5.txt
```
This would omit the TODAY line though. I guess what the OP wants is to omit the TONIGHT line.

There also was [a series of blog posts](https://backreference.org/tag/ranges) by Waldner about ranges matching in sed and awk.

---

