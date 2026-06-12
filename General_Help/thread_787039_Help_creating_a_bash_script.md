---
title: "Help creating a bash script"
date: 2008-05-08
forum: General Help
---

### Post by lawentzel on 2008-05-08
I am trying to convert a whole bunch of files from HTML to Wiki. I have the program to do it, however it only converts one HTML file at a time.  I have over 4600 files to convert.  So doing it one at a time isn't really an option.  Can someone help me with a bash script?  I have only done VERY minor stuff with them in the past.

The command I am typing to convert the files looks like this:
```
html2wiki --dialect MediaWiki -- encoding iso-8859-1 --base-uri http://website/wiki/ --wiki-uri http://website/wiki/ input.html > output.wiki
```

The "input.html" is what needs to change. I have tried using the * wild card.  This actually grabbed the first HTML file and added it to output.wiki then exited.

Your help is appreciated.  Thanks.

---

### Post by beren.olvar on 2008-05-08
Hi
i would try something like:
```

for i in *.html; do
  a=`basename $i .html`
  html2wiki --dialect MediaWiki -- encoding iso-8859-1 --base-uri \
  http://website/wiki/ --wiki-uri http://website/wiki/ $i > $a.wiki
done

```

This way all the files.html would get converted into files.wiki
conserving their base-names (before the .html)
Note this will only work if you have all the html files in the same directory.

cheers

---

### Post by lawentzel on 2008-05-09
I am now getting the following message when I run the script.

```
./wiki: line 3: $a.wiki: ambiguous redirect
```

I've named the script "./wiki" hence the first part.  Any suggestions?  Thanks.

Lee

---

### Post by lawentzel on 2008-05-09
Never mind, despite the errors, it seemed to have worked.  Thanks!

---

### Post by wootah on 2008-05-09
> **beren.olvar said:**
> Hi
i would try something like:
```

for i in *.html; do
  a=`basename $i .html`
  html2wiki --dialect MediaWiki -- encoding iso-8859-1 --base-uri \
  http://website/wiki/ --wiki-uri http://website/wiki/ $i > $a.wiki
done

```

This way all the files.html would get converted into files.wiki
conserving their base-names (before the .html)
Note this will only work if you have all the html files in the same directory.

cheers

Isn't there an issue when the input file name has a space when using "for i in *.html; do" ?

---

