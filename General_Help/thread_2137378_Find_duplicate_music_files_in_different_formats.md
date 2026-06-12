---
title: "Find duplicate music files in different formats"
date: 2013-04-20
forum: General Help
---

### Post by ZootHornRollo on 2013-04-20
Hi,

I have let my music collection get into a bit of a mess.

I have a large collection of FLAC files which also have an MP3 duplicate for syncing with a sn MP3 player.

I now wish to remove these duplicates.

Any idea how to go about it without going into each folder indiviually?

i can't simply search for .mp3 and delete as there are some albums i only have MP3 copies of.

Thanks,

---

### Post by Vaphell on 2013-04-20
what do you consider a duplicate? is it about exactly the same naming convention of directory/files? tags?

---

### Post by ZootHornRollo on 2013-04-20
hi,

Yes, files are same name, in the same directory.  Only difference being file extention .flac/.mp3

---

### Post by prodigy_ on 2013-04-20
```
#!/bin/bash

# replace /path/to/folder with actual path and folder name
find /path/to/folder -type f -iname '*.flac' -print0 | \
	while read -r -d $'\0' full_path; do
		rm "${full_path%.*}.[mM][pP]3" 2>/dev/null
	done
```

---

### Post by papibe on 2013-04-21
Hi ZootHornRollo.

This code create a report of all duplicates filenames with different extensions:
```
#!/bin/bash

MUSICDIR="/path/to/music"

# For each file look for files with the same name (different extension).
while read -d $'\0' -r file; do

        # Initializations.
        count=0
        echo "$file"

        # Register each copy
        while read -d $'\0' -r copy; do
                count=$(($count+1))
                echo -e "    $count $copy"
        done < <(find "$MUSICDIR" -type f \( -regex .\*/"$file"\\.[^.]\* -or -name "$file" \) -print0)

done < <(find "$MUSICDIR" -type f -not -name .\* -exec bash -c 'b="${1##*/}"; printf "%s\0" "${b%.*}"' _ '{}' \; | sort -z | uniq -zd)

```
Regards.

---

### Post by CaptainMark on 2013-04-21
I don't know about most other media players but banshee will automatically detect that my old ipod only accepts mp3's and as it syncs it will encode my songs to mp3 for the ipod and discard the copy when finished, so i can sync my .ogg library to my ipod and not have to duplicate my library in a different format

---

### Post by ZootHornRollo on 2013-05-22
guys, can't thank you enough!  That is perfick!

Sorry its taken so long to get around to running it.

THanks again!

---

### Post by ZootHornRollo on 2013-05-22
> **CaptainMark said:**
> I don't know about most other media players but banshee will automatically detect that my old ipod only accepts mp3's and as it syncs it will encode my songs to mp3 for the ipod and discard the copy when finished, so i can sync my .ogg library to my ipod and not have to duplicate my library in a different format

windows phone devices are not recognised as media players but as storage devices, unfortunately.

---

