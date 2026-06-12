---
title: "Folder and filenames from files copied from Mac partition to Ubuntu partition"
date: 2017-06-03
forum: General Help
---

### Post by cosimos on 2017-06-03
Hello !

I copied thousands of files and folders from my mac partition to my ubuntu ext4 partition through an external fat32 hard disk.

But I discovered recently that all my filenames and folders have big issues with accents, etc.

```
file -bi CB\ 14\ rue\ d\'Assas\ -\ S&#9618;curit&#9618;.rtd
-> application/octet-stream; charset=binary
```

The &#9618; is supposed to be é. This problem occurs on filenames and folder's names with all accent éàçèâê, etc., making the files unreadable on my samba share.

I found this script that act interactively on filenames to correct the encoding (detect encoding and change it to windows-1252 and it's working : 

```
#!/bin/bash

# list of encodings to try. (max 10)
enc=( windows-1252 )

while IFS= read -rd '' file <&3; do
    base=${file##*/} dir=${file%/*}

    # if converting from utf8 to utf8 succeeds, we'll assume the filename is ok.
    iconv -f utf8 <<< "$base" >/dev/null 2>&1 && continue

    # display the filename converted from each enc to utf8
    printf 'In %s:\n' "$dir/"
    for i in "${!enc[@]}"; do
        name=$(iconv -f "${enc[i]}" <<< "$base")
        printf '%2d - %-12s: %s\n' "$i" "${enc[i]}" "$name"
    done
    printf ' s - Skip\n'

    while true; do
        read -p "? " -n1 ans
        printf '\n'
        if [[ $ans = [0-9] && ${enc[ans]} ]]; then
            name=$(iconv -f "${enc[ans]}" <<< "$base")
            mv -iv "$file" "$dir/$name"
            break
        elif [[ $ans = [Ss] ]]; then
            break
        fi
    done
done 3< <(LC_ALL=C find . -depth -name "*[![:print:][:space:]]*" -print0)
```

Sadly it doesn't correct folder's names problems and the fact that it asks an answer for each file (I have thousands) makes it too slow. What other solution do I have ?

Thanks for your assistance in this serious problem...

---

