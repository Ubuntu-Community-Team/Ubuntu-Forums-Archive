---
title: "Batch PDF to PNG conversion with sftrender"
date: 2013-06-05
forum: General Help
---

### Post by O-pos on 2013-06-05
Hello,

I have about 35 single frame SWF pages, which I would like to convert to PNG format in batch, so that the PNG files have either the same names as the corresponding SFW files, or numbered in some kind of order like 01.PNG, 02.PNG, 03.PNG etc..

So far I have been unsuccessful in doing this - every effort results in one single SWF to PNG conversion of that SWF file that is the last one one the alphanumeric order. 

Any thoughts?

---

### Post by SeijiSensei on 2013-06-05
Use a script to iterate over the files
```

#!/bin/bash

cd /path/to/the/flashfiles

for f in *.swf
do
     NAME=$(sed 's/\.swf$//g')
     convert $f $NAME.png
done

exit 0

```

I wrote this quickly so it might not work without a bit of massaging.  It also assumes none of the source filenames have embedded spaces.

---

### Post by O-pos on 2013-06-06
It did not work, unfortunately. Nothing happens at all. ? syntax error?

---

### Post by SeijiSensei on 2013-06-07
I reread your opening post, and you seem to be using a different conversion program than Imagemagick convert, which I used in the script.  Replace the line
```
convert $f $NAME.png
```
with the appropriate command for the software you are using.  "$f" is the placeholder for the source file name, and "$NAME.png" the equivalent for the target.  You might also give Imagemagick a try using "sudo apt-get install imagemagick" to install it.

For a little debugging help, add this line above the one that begins with "convert":

```
echo "Converting from $f to $NAME.png"
```

That should show you if the script is correctly iterating over the files.

I assume you replaced "/path/to/the/flashfiles" with the appropriate path on your computer, and that you marked the script file you created as executable.

---

### Post by O-pos on 2013-06-09
Thanks again.

Actually, I realized that I incorrectly named this thread PDF to PNG, while it should be SWF to PNG

Regarding your code, I correctly indicate the location of the folder where the SWF files are. I did not use your code as a script, but pasted in terminal each line one by one. IN this situation, convert does not work at all, even with a single file.

swfrender (part of swftools package) which I am using, works for a single file with this command: swfrender file.swf -o file.png but I have not figured out the way to execute it for batch processing of multiple files.

---

### Post by O-pos on 2013-06-11
Got it sorted out: 

for img in *.swf; 
do 
swfrender "$img" -o "$img.png"
done

Thanks for your suggestions.

---

