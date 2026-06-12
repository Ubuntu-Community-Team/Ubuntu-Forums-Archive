---
title: "ZFS: List of files that have been deduped?"
date: 2014-06-06
forum: General Help
---

### Post by Asquirrel on 2014-06-06
I wrote a script (see below) that attempts to locate all files which have been deduplicated by ZFS. I am trying to find which files have been deduplicated because...amongst 10 TB of data, I know some of it is very prone to duplicates, and most is not, but I have no idea which pieces ZFS (due to block, rather than string-based, dedup) will dedup well. I know I can get a list of plain files from zdb, but I am unsure of how to interpret it. I was lead to believe that lines like this:

```
586    1    16K    512      0    512    0.00  ZFS plain file
686    1    16K  8.50K      0  8.50K    0.00  ZFS plain file
```

indicate a file has been deduped, whereas a line like this:
```
9141    3    16K   128K   150M   197M   98.28  ZFS plain file
9142    3    16K   128K  95.1M   197M   99.05  ZFS plain file
```
indicates the files have been compressed only. Are my assumptions correct, or, as I fear, does the latter case indicate it *might* be compressed, or deduped, or both?

```
#!/bin/bash

if [ $# -lt 1 ]
then
        echo "Usage: $0 <ZFS dataset>"
        exit 1
fi

mountpoint="`zfs get -H mountpoint $1 | awk '{print $3}'`"
cache_file="/tmp/allfiles.`echo \"$1\" | sed 's#/#_#g'`"

#Check to see if our cache of all files exists.
if [ -s $cache_file ]
then
        echo "Using cache file $cache_file, delete it if it is out of sync."
else
        echo "Recreating cache file $cache_file, this could take a while."
        find "$mountpoint" -ls > $cache_file
        sed -i 's/^ *//g' $cache_file
fi

zdb -dd $1 | grep 'plain file' > /tmp/all_files.thisrun

while read line
do
        if [ "`echo $line | awk '{print $7}'`" = "0.00" ]
        then
                to_find="`echo $line | awk '{print $1}'`"
                #The awk sets fields to null because 'ls' doesn't properly escape spaced commands, and awk would get confused.
                grep "^$to_find " $cache_file | awk '{$1="";$2="";$3="";$4="";$5="";$6="";$7="";$8="";$9="";$10="";print}'
        fi
done < /tmp/all_files.thisrun

rm /tmp/all_files.thisrun
```

---

### Post by Asquirrel on 2014-06-06
I did a bit of testing and managed to answer this myself. Correct: inodes listed with 0.00 as in column 7 (the % column) are deduped files. Files with a percentage between 0 and 100 (exclusive) are compressed. If there is any overlap between the two...for my test data, the overlap is very small (~30 files out of 5000).

---

