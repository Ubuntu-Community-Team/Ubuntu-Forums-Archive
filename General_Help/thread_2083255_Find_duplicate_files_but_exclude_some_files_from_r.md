---
title: "Find duplicate files but exclude some files from results"
date: 2012-11-11
forum: General Help
---

### Post by parameter on 2012-11-11
I need to search my server's filesystem for duplicate files. However, some files that are duplicates are okay and I don't want to see them listed in the results regardless of their filenames or location. Is there a CLI-based duplicate file finder that can do that?

I was hoping to store the MD5 checksum of files that I want to be ignored in a text file and then either tell the duplicate file finder to ignore files with those checksums or filter out the results of a search myself with grep.

So far I have tried fdupes, duff, and rdfind without success. fdupes would be great if it would show the checksum with the single line results, but it doesn't. duff shows the checksum, but it lists the results over multiple lines. rdfind doesn't come close to doing what I need.

Are there any other programs that can do what I need?

---

### Post by Vaphell on 2012-11-12
try this, it takes duff output and checks if the sha1 in header is to be found in hash file. If that's the case the script skips the whole block.
```
#!/bin/bash

hashfile=$1
[ -f "$hashfile" ]  || exit 1               # bad hashfile, exit
shift
for d; do [ -d "$d" ] || exit 1; done       # bad dir(s), exit

while read -r ln
do
  if [[ $ln =~ digest.[0-9a-f]{40} ]]       # if header line
  then
    sha1=${ln##* }; sha1=${sha1%?}          # - extract sha1
    grep -q "$sha1" "$hashfile" && sha1=""  # - sha1 in hashfile => set sha1 to null
  fi
  [ "$sha1" ] && echo "$ln"                 # print line if sha1 not empty
done < <( duff -r "$@" )
```
example of use
```
./duplicates.sh ./sha1list.txt dir1 dir2
```

alternatively it would be easy to print the extracted sha1 next to every relevant line name and pass everything to *grep -v*

Similar script could be easily written for fdupes.

---

### Post by parameter on 2012-11-12
Thanks very much, Vaphell! Your shell script works perfectly and does just what I need.

---

