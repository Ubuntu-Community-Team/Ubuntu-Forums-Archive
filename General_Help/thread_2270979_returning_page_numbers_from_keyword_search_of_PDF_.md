---
title: "returning page numbers from keyword search of PDF files and the times per page"
date: 2015-03-26
forum: General Help
---

### Post by lud2 on 2015-03-26
Hello,

I need to look for keywords in a hundred of PDF and I have find this script:
[http://ubuntuforums.org/showthread.php?t=1368062](http://ubuntuforums.org/showthread.php?t=1368062)

It's great but I need to know also when I have the keyword n times on a page or line, how can I change this script to do that ?

```
#!/bin/sh

[ "$*" = "" ] && printf "\nYou forgot a search string!\n\n" && exit 1

oldfile=xxx
cptF=0
cptT=0

find $PWD -iname "*.pdf" -type f | 
{
while read file ; do
   pages=$(pdfinfo "$file" | awk '/Pages:/ { print $NF }')
   for i in $(seq ${pages}) ; do
      match=$(pdftotext -nopgbrk -q -f $i -l $i "$file" - | \
         fgrep -i -w -c -m 1 "$*")
      if [ "$match" -eq 1 ] && [ "$file" != "$oldfile" ] ; then
printf "\nTotal dans ce fichier $cptF"
         printf "\n\n$file\n"

         printf "Page(s)"
         oldfile="$file"
cptT=`expr $cptT + $cptF` 
    cptF=0

      fi
      if [ "$match" -eq 1 ] ; then
cptF=`expr $cptF + 1`
 printf " $i "
    
fi
   done
done

[ "$oldfile" = xxx ] && printf "\nNo matches!"
}
```

Lud

---

### Post by TheFu on 2015-03-27
Don't know, since the pdftotext command isn't per-page, it is per-file. To use that, you'd need to split every PDF page into a different document, right?  Of course, you might see something that I didn't in the manpage for it. If you left the page breaks in, that might be helpful, but I don't know how with the tools you are using unless you split each text page into a separate file.  The -f and -l options look interesting for that - use **pdfinfo** to find the total number of pages first.  Looks doable now.

**recoll** has a proximity return capability that might be useful. Doubt it works per-page either, but nearby might be enough? Recoll is amazing, but requires advanced indexing, which can become huge.

Of course, none of these pdf search tools work with image-based PDF files or with type-3 fonts. For those, only running some sort of OCR and putting the text *under the image* is useful. gscan2pdf does that, but the OCR isn't always great. I use this only for very important, old, family documents that I'd like to easily find later by keyword search.

BTW - I worked in document management in both printing and government for about 8 yrs. We dealt with PDF with 100K+ documents and millions of pages.

---

