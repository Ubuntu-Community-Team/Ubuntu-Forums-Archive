---
title: "bash script help for recursive file conversion"
date: 2018-02-02
forum: General Help
---

### Post by getut on 2018-02-02
I need some help with a small bash script to convert color pdf files to monochrome pdf files of known density and maintain as much clarity as possible.

I have the base command working as intended... yes I do mean to overwrite the original.

convert -density 1200 -threshold 70% testinput.pdf -resample 100 testinput.pdf

But I'm having trouble scaling this up to a script or one liner that will:

1) recursively process all pdf files in all folder below the start point
2) handle spaces in directories and filenames

There are literally hundreds of threads out there similar that add a renamed file. But I can't find any version of command that meets the two objectives above. I can post scripts or lines I've tried if anyone wants me to but all involve piping output out of find or using xargs and I haven't found the magic.

---

### Post by Holger_Gehrke on 2018-02-02
mogrify is another tool from the ImageMagick suite. It does all the things convert does, but does them 'in place'. the '-print0' (that's a zero at the end, not a capital o) action of find makes it output a list of file paths and names with '0' byte as separator, which is exactly what xargs expects to get if you pass it the option '-0' (and this, too is a zero). That combination of options on find and xargs is safe from most - if not all - unusual characters in filenames. The option '-L 1' stops xargs from stuffing multiple file names into one command, which mogrify does not really like, and we end up with:
```
find . -iname '*.pdf' -print0|xargs -0 -L 1 mogrify -density 1200 -threshold 70% -resample 100
```

Holger

---

### Post by 1clue on 2018-02-02
I believe this would also work:

```

find . -name '*.pdf' -exec mogrify -density 1200 -threshold 70% -resample 100

```

Although as I don't have a directory full of files to convert I have no real way to test it.

---

### Post by steeldriver on 2018-02-02
^^^ I believe that would fail with a 

```
find: missing argument to `-exec'
``` error ;)

Something like this should work, if you prefer to use your original command (however I'd suggest you use the mogrify version, since that's apparently intended for in-place conversion):

```

find . -name '*.pdf' -execdir sh -c '
   for f; do echo convert -density 1200 -threshold 70% "$f" -resample 100 "$f"; done
 ' sh {} +

```

(I've left an `echo` in so that you can verify what it's going to do without actually doing it)

---

