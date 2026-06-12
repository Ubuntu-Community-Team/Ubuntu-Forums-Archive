---
title: "Hi, my batch file operation is failing.  Can you check my CLI command."
date: 2016-10-18
forum: General Help
---

### Post by MechaMechanism on 2016-10-18
Here is my command.  It does not work.  Possibly because of the dollar signs?  I am not to familiar with stringing commands together very well.  I pieced this together based on tidbits from all over the web.  It is calling up the Imagemagick command convert to do operations on 39 PNG files and output the new files in a separate dir.

```
find ./ -name  *.png -exec convert  {} -shave 50x50 -bordercolor white -border 1x1 -fuzz 70% -trim /home/nate/Pictures/trim/{} \;
```

---

### Post by steeldriver on 2016-10-18
What dollar signs are you referring to? Can you be more specific than "it does not work"? Do you get an error message? Are the files converted but the output goes somewhere else?

FWIW I'd probably wrap the convert function in a shell scriptlet e.g.

```

find ./ -name  '*.png' -exec sh -c '
  convert  "$1" -shave 50x50 -bordercolor white -border 1x1 -fuzz 70% -trim "/home/nate/Pictures/trim/${1##*/}"
' sh {} \;

```

or

```

find ./ -name  '*.png' -exec sh -c '
  for f; do convert  "$f" -shave 50x50 -bordercolor white -border 1x1 -fuzz 70% -trim "/home/nate/Pictures/trim/${f##*/}"; done
' sh {} +

```

---

### Post by MechaMechanism on 2016-10-19
> **steeldriver said:**
> What dollar signs are you referring to? Can you be more specific than "it does not work"? Do you get an error message? Are the files converted but the output goes somewhere else?

FWIW I'd probably wrap the convert function in a shell scriptlet e.g.

```

find ./ -name  '*.png' -exec sh -c '
  convert  "$1" -shave 50x50 -bordercolor white -border 1x1 -fuzz 70% -trim "/home/nate/Pictures/trim/${1##*/}"
' sh {} \;

```

Tried that one and it did nothing.  Just went back to the prompt.  Using mine it just does the same thing, no output and no files created.  Is there a certain way these should be typed in.  I just type them in manually and double check them too.  I also copied and paste and that did not work well.

---

### Post by steeldriver on 2016-10-19
What do you get when you just do

```

find ./ -name  '*.png'

```

If there were no error messages, then it usually indicates that the command executed successfully - but that's *its* definition of successful, which might not necessarily be *yours *- for example it will "successfully" not convert any files if there are in fact no files matching the *.png pattern

---

### Post by Keith_Helms on 2016-10-19
> **MechaMechanism said:**
> Here is my command.  It does not work.  Possibly because of the dollar signs?  I am not to familiar with stringing commands together very well.  I pieced this together based on tidbits from all over the web.  It is calling up the Imagemagick command convert to do operations on 39 PNG files and output the new files in a separate dir.

```
find ./ -name  *.png -exec convert  {} -shave 50x50 -bordercolor white -border 1x1 -fuzz 70% -trim /home/nate/Pictures/trim/{} \;
```

The problem is that {} in the find command contains the full path down to wherever the png file is.  For example something like
```
/home/nate/Pictures/vacation/2014-bermuda/scuba01.png
```
The command is trying to write an output file to something like
```
/home/nate/Pictures/trim/./home/nate/Pictures/vacation/2014-bermuda/scuba01.png
```
which fails because several directory levels are missing

What you need is commands that use the full path of the png files for input, but only use the filename part for output.  Try this:

```
while IFS= read -r -d '' file; do
  filename=`basename "$file"`
  convert "$file" -shave 50x50 -bordercolor white -border 1x1 -fuzz 70% -trim "/home/nate/Pictures/trim/$filename"
done < <(find ./ -name "*.png" -print0)
```

This syntax makes the find command print null delimited lines for each png found enabling the while loop to handle filenames that contain spaces or special characters.

---

### Post by MechaMechanism on 2016-10-23
Ha, Ha, Ha.  I had accidentally renamed the png files simply numbers.  So I renamed the files again with .png.  Everything work now.

---

