---
title: "Script to use avconv to convert all mp4s to mp3s"
date: 2020-08-01
forum: General Help
---

### Post by raleigh3 on 2020-08-01
I have a lot of mp4s I need to convert to mp3s.

I need some help with a bash script for the job.

This works on single files.

```
#!/bin/bash
#
# Converts mp4s to mp3s
# Uses avconv
# Ex.  mp4tomp3.sh 'Mind Your Own Business by Hank Jr.mp4'
# ALWAYS enclose filenames in single quotes !!

MOV="$*"
FILENAME=$(basename "${MOV// /_}" | sed 's/\(.*\)-.*/\1/').mp3
avconv -i "${MOV}" -vn -f wav "${FILENAME}"
```

---

### Post by SeijiSensei on 2020-08-01
If all the files are in a single directory, wrap the script in a for loop like this:

```

#!/bin/bash
#
# Converts mp4s to mp3s
# Uses avconv
# Ex.  mp4tomp3.sh 'Mind Your Own Business by Hank Jr.mp4'
# ALWAYS enclose filenames in single quotes !!

for f in *.mp4
do
   FILENAME="$(basename "$f").mp3"
   avconv -i "$f" -vn -f wav "${FILENAME}"
done

```

Handling files with embedded spaces is always difficult.  In cases like this I usually first replace the spaces with underscores using sed.

Also avconv is pretty much deprecated these days. Use ffmpeg.

---

### Post by raleigh3 on 2020-08-02
Thanks  SeijiSensei's for your help.

---

