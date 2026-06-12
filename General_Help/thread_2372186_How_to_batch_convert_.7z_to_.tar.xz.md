---
title: "How to batch convert .7z to .tar.xz?"
date: 2017-09-22
forum: General Help
---

### Post by accounts0 on 2017-09-22
I have a folder with several subfolders containing in total approximately 100GB of .7z archives I made in 7-zip in Windows- they're compressed using the .7z 'Ultra' preset.

If I understand correctly, converting them all to .tar.xz will save me some space, so I'm interested in learning how I can batch convert them all. Ideally they'd save in-place in the same subdirectory the originals reside in.

Also, I'm concerned about whether the finished archives are actually usable & 'good' when they're done, so a check would be desirable.

What command(s) should I be looking at to do this?

-Thanks...

---

### Post by btindie on 2017-09-22
Add the below script to the directory where your archives are. "chmod +x" the script and run it from that directory. It'll convert all *.7z files to *.tar.xz files.

```

#!/bin/bash

TMP_BASE=.


while read -r A; do


  TMP=$(mktemp -d -p $TMP_BASE)


  7zr x -bd -o$TMP "$A" >&/dev/null


  echo "Creating: \"${A%.7z}.tar.xz\""


  (cd $TMP; find . -maxdepth 1 ! -name .) | tar -C$TMP -Jcf "${A%.7z}.tar.xz" --xform 's,^./,,' -T -


  rm -rf $TMP


done < <(find . -name \*.7z)

```

Before running it make sure you've got enough space available. It extracts the *.7z archives to TMP_BASE which by default is current directory. If /tmp is in RAM and there's enough space to take the biggest archive then change it to that.

---

### Post by accounts0 on 2017-09-25
> **btindie said:**
> Add the below script to the directory where your archives are. "chmod +x" the script and run it from that directory. It'll convert all *.7z files to *.tar.xz files.


Thanks, but before I go about running it I was wondering if there's a way to automate checking that the output files are valid/uncorrupted/open-able. There are so many that it'd take me all weekend to test opening them all before I delete the originals. Ideas on that ?

---

### Post by accounts0 on 2017-10-04
Well, thanks nevertheless, but the space savings is so minimal it's not worth the effort. Oh, well.

---

