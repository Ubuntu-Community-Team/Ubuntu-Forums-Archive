---
title: "Bash script image convert"
date: 2007-10-10
forum: General Help
---

### Post by PurposeOfReason on 2007-10-10
With a recent boredom I put rockbox on my ipod. All is good except album art has to be in .bmp format. I found this script that is supposed to do it easily but when I do I get the following.

```

#!/bin/sh
find /media/SHAWN\ IPOD/Songs/ -iname "*.png"| while read file;
do
convert -size 75x75 "$file" -resize 100x100 "cover.bmp"
cp cover.bmp "${file%/*}"/.
done

```

```

shawn@desktop:~$ '/media/SHAWN IPOD/Songs/.albums' 
/media/SHAWN IPOD/Songs/.albums: 6: convert: not found
cp: cannot stat `cover.bmp': No such file or directory
shawn@desktop:~$ 

```

Could this even work or is there a better way?

---

### Post by cwaldbieser on 2007-10-10
> **PurposeOfReason said:**
> With a recent boredom I put rockbox on my ipod. All is good except album art has to be in .bmp format. I found this script that is supposed to do it easily but when I do I get the following.

```

#!/bin/sh
find /media/SHAWN\ IPOD/Songs/ -iname "*.png"| while read file;
do
convert -size 75x75 "$file" -resize 100x100 "cover.bmp"
cp cover.bmp "${file%/*}"/.
done

```

```

shawn@desktop:~$ '/media/SHAWN IPOD/Songs/.albums' 
/media/SHAWN IPOD/Songs/.albums: 6: convert: not found
cp: cannot stat `cover.bmp': No such file or directory
shawn@desktop:~$ 

```

Could this even work or is there a better way?

Do you have ImageMagick installed?  What is the output of
```

$ type convert

```

---

### Post by PurposeOfReason on 2007-10-10
That was it! Installed it and it worked. Now I feel like an idiot.

---

