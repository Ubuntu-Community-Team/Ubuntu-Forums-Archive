---
title: "Change script to reduce mp4 size on all files in a directory"
date: 2024-10-28
forum: General Help
---

### Post by raleigh3 on 2024-10-28
How can I change script to reduce mp4 size on all files in a directory ?

```
#!/bin/bash
# Reduce mp4 to 480i resolution and reduce size considerably

[ ! $1 ] && {
echo -e "Error!! No filename given."; exit 1; } || echo -e "Searching for $1"
ffmpeg -i $1 -s hd480 -strict -2  $1Small.mp4

```

---

### Post by walterdeanase on 2024-10-28
> **raleigh3 said:**
> How can I change script to reduce mp4 size on all files in a directory ?

```
#!/bin/bash
# Reduce mp4 to 480i resolution and reduce size considerably

[ ! $1 ] && {
echo -e "Error!! No filename given."; exit 1; } || echo -e "Searching for $1"
ffmpeg -i $1 -s hd480 -strict -2  $1Small.mp4

```
why do you do?

---

### Post by Holger_Gehrke on 2024-10-29
The IMHO best way to do this is
```

#!/bin/bash
# Reduce mp4 to 480i resolution and reduce size considerably

while [ -e "$1" ] ; do {
  ffmpeg -i "$1" -s hd480 -strict -2  "${1%%.mp4}Small.mp4"
  shift
done

```

Now you can call this script with multiple parameters or a glob which will get expanded to multiple parameters by the shell - e.g. with the script named 'reduce' you could call 'reduce [Aa]*.mp?' to run it on all files whose name starts with 'a' or 'A' and which have a name ending in '.mp?' (so it would convert both .mp4 and .mpg). You could even use extended globs like '!(*txt|*srt|*Small.mp4)' to run it on everything not named like one of the expressions in the parenthesis.

Holger

---

