---
title: "Convert multiple videos at once with FFMPEG"
date: 2007-06-09
forum: General Help
---

### Post by shironeko on 2007-06-09
I need to convert multiple videos at once with FFMPEG.

Let's see, I got this folder with 111 uncompressed .avi video files, and I want to encode them to .avi (whatever name), but so that their size is much smaller.

I could do that with:

ffmpeg -i name.avi differentname.avi

But I can't do that with 111 Files!

Therefor I need a way to reencode this files all at once with FFMPEG.

Thanks  ^^

---

### Post by reclusivemonkey on 2007-06-09
```

#!/bin/sh
for file in *.avi
do
        ffmpeg -i "$file" converted_"$file"     
done

```

Save that as a script called something like "convert.sh" in the folder with all you avis. Then make it executable with

```

chmod +x convert.sh

```

You can then run it with just

```

./convert.sh

```

WARNING! I am no expert scripter, so make sure you have a backup of these files. I can't guarantee it won't eat them all :-S

---

