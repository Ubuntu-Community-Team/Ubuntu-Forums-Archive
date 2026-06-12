---
title: "Input/output error during bulk file copy between 2 usb disks"
date: 2008-06-07
forum: General Help
---

### Post by zi99y on 2008-06-07
Hi all, Not posted in a long time, most of my probs have already been addressed by other posts.

I have bought a new USB2.0 (FAT32) hard drive, and am attempting to copy old data from my older USB2.0 (NTFS) disk. 

I have attempted copying in Windows and different flavours of Linux to no avail. It gets about 10Gb through and complains about a file reporting **"Input/output error"** after this no more files are copied as the drive is no longer available although still shows mounted. (Error was different in Windows)

Here is a snippet from the console where the problem occurs:

```
cp: failed to preserve ownership for `./Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 5 - Extreme Expressions.mp3': Operation not permitted
`/media/Storage 250Gb NTFS/mp3/Library/Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 6 - Further Away Than Yesterday.mp3' -> `./Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 6 - Further Away Than Yesterday.mp3'
cp: failed to preserve ownership for `./Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 6 - Further Away Than Yesterday.mp3': Operation not permitted
`/media/Storage 250Gb NTFS/mp3/Library/Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 7 - Fairground Under My Furniture.mp3' -> `./Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 7 - Fairground Under My Furniture.mp3'
cp: reading `/media/Storage 250Gb NTFS/mp3/Library/Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 7 - Fairground Under My Furniture.mp3': Input/output error
cp: cannot stat `/media/Storage 250Gb NTFS/mp3/Library/Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 8 - Taff\'s Cabs.mp3': Input/output error
cp: cannot stat `/media/Storage 250Gb NTFS/mp3/Library/Albums2/nine yards orchestra - our backyard/Nine Yards Orchestra - Our Backyard - 9 - Swing Into The Light.mp3': Input/output error
cp: failed to preserve ownership for `./Albums2/nine yards orchestra - our backyard': Operation not permitted
cp: cannot stat `/media/Storage 250Gb NTFS/mp3/Library/Albums2/Nirvana': Input/output error
cp: cannot stat `/media/Storage 250Gb NTFS/mp3/Library/Albums2/no doubt - the singles': Input/output error
cp: cannot stat `/media/Storage 250Gb NTFS/mp3/Library/Albums2/norah jones - come away with me': Input/output error
cp: cannot stat `/media/Storage 250Gb NTFS/mp3/Library/Albums2/nova tunes 1.3 [electronic][2006]': Input/output error

```

Any ideas appreciated.

---

