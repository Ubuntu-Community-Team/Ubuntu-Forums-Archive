---
title: "copy files following pdfgrep"
date: 2013-08-25
forum: General Help
---

### Post by vahaboglu on 2013-08-25
Hello,
I have a huge collection of pdf files. Time to time I need to search a string inside them using "pdfgrep -cr 'xxx' ./*". This command produces an output giving the location and title of the pdf file followed by the occurence time of the string incide it, such that:
./2VF685TH/XXX.pdf:0
./4724GX6Z/YYY.pdf:1
This means I may find my search string inside YYY.pdf. Now I want to copy this YYY.pdf (and all others with >0 occurence of the string) to another location.
Can I do this in the command line with something like "pdfgrep ..... -exec (or xargs. or ..) cp > ~/xxy/".
Any help will be appreciated.

---

### Post by Vaphell on 2013-08-26
does this pdfgrep support -l option like grep?
```
-l, --files-with-matches  print only names of FILEs containing matches
```


in case of -c try something like this
```
while read -r ln; do f=${ln%:*}; c=${ln##*:}; [ "$c" -gt 0 ] && cp -t "dest/dir" "$f"; done < <( pdfgrep -cr xxx . )
```

---

### Post by vahaboglu on 2013-08-26
thank you Vaphell,
with Code:
pdfgrep -cr "PATTERN" "PDFPATH" -exec cp "{}" > OUT.txt
grep -e  '\:[1-9]' OUT.txt | sed 's/\:[0-9]*//g' > match.txt

I get a match.txt file with the path and title of relevant pdf references. So may be grep references line by line from this match.txt and copy files to another path may solve my problem.

---

### Post by vahaboglu on 2013-08-26
Thank you Vaphell your code is working nicely.

while read -r ln; do f=${ln%:*}; c=${ln##*:}; [ "$c" -gt 0 ] && cp -t "/home/yyy/zzz" "$f"; done < <( pdfgrep -cr xxx . )

---

