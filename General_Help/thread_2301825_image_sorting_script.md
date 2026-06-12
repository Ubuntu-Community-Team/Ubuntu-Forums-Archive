---
title: "image sorting script"
date: 2015-11-05
forum: General Help
---

### Post by nepomo on 2015-11-05
Hello,

this might be more of a general problem... I am trying to chronologically sort a large image collection. Thus, nothing too new here...

I am using this script:
```

#!/bin/bash

source="/data/sorter"
target="/data/sorter_sorted"
diff="/data/sorter_undated"

mkdir -p "${diff}"

find "$source" -type f | while read file ; do
   date=$(exiv2 "$file" 2> /dev/null | awk '/Image timestamp/ { print $4 }')
   [ -z "$date" ] && echo "$file" >> "${diff}"/000_error.txt && cp "$file" "${diff}" && continue
   year=${date%%:*}
   month=${date%:*}
   month=${month#*:}
   day=${date##*:}
   mkdir -p "${target}/${year}"
   mkdir -p "${target}/${year}/${year}-${month}-${day}"
   cp "$file" "${target}/${year}/${year}-${month}-${day}"
done

find "$target" -type f | while read file ; do
   exiv2 rename "$file"
done

for file in `find $target -name "*.JPG" -print 2>/dev/null` ; do mv $file ${file%.*}.jpg; done
for file in `find $target -name "*.jpeg" -print 2>/dev/null` ; do mv $file ${file%.*}.jpg; done

```

On the original collection, I additionally used fslint to delete any double files, I guess this was based on the MD5 sums!?

However, there are around 100GB of data in a massively complex folder tree with lots of data from digital cameras, which are not images. 

As far as I understand that, those files do not have exiv2 data and would all be ending up in the undated folder according to the script. 

Now the problem:

```
find /data/sorter -type f | wc -l
```

gives me the number of files in the source folder (~30.000)

if I do the same on the the two new folders, the _sorted and _undated, the sum of these is less (~28.000). Hence I am loosing aroudn 2000 files due to the script...

I cannot figure out what I am doing wrong. Any advice on the whereabouts of the files would be great, also the script is probably far from ideal... :)

Thanks in advance.

Cheers.
-nepomo

---

