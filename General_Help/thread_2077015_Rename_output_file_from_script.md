---
title: "Rename output file from script?"
date: 2012-10-27
forum: General Help
---

### Post by derekcentrico on 2012-10-27
Below is my script that uses Handbrake CLI to convert videos to the MP4 container so I can play it easily across all devices. 

Currently, the output ends up being very, very long because it keeps the old extension and I have to have the output file add onto it.

```
#!/bin/bash
# handbrake processing script "convert.sh"

for file in /mnt/storage2/Videos/Convert.Pending/*

# 6 Channel Passthrough only; Android devices cannot hardware decode
do HandBrakeCLI -i "$file" -o "$file".hb.mp4 -f mp4 -4 -O --strict-anamorphic -m -e x264 -q 19 -a 1 -E copy:ac3 -6 6ch -B 640 --verbose=1

#move original
mv $file /mnt/storage2/Converting/Processed/

#move new
mv $file.hb.mp4 /mnt/storage2/Videos/Movies/
```

How can I modify this basic script so that it will take the $file injected and output it to something less than the full $full?

I'd like it to take the first part before the "." for extension, keep it, and use it in the output plus the new extension.

Input appreciated!

---

### Post by steeldriver on 2012-10-27
You can use the bash % and %% parameter substitutions to remove the shortest matching suffix or the longest matching suffix respectively

```
file="long file.with.lots.of.extensions"; echo "${file%.*}"
long file.with.lots.of
``````
$ file="long file.with.lots.of.extensions"; echo "${file%%.*}"
long file
```To grab *just* the extension you can use the corresponding # or ## to snip the shortest or longest prefix

```
$ file="long file.with.lots.of.extensions"; echo "${file##*.}"
extensions
```Hope this helps

---

