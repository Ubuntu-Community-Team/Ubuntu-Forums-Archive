---
title: "Combine two commands"
date: 2020-06-13
forum: General Help
---

### Post by raleigh3 on 2020-06-13
Looking for a way to combine these 2  so I do it in one step.

From the command line.

```
convert Tess.jpg tess.tif

tesseract tess.tif tess
```

For example

text2file <name of scanned document>

---

### Post by TheFu on 2020-06-13
is this a trick question? You've posted the answer already.

BTW, please use code tags so we can tell the difference between a comment and what you think is part of a script.

---

### Post by raleigh3 on 2020-06-13
> **TheFu said:**
> is this a trick question? You've posted the answer already.

BTW, please use code tags so we can tell the difference between a comment and what you think is part of a script.

No.

Looking for a way to combine these 2 so I do it in **one step**.

---

### Post by ActionParsnip on 2020-06-14
How about if you run:

```

sudo gedit /usr/bin/text2file; sudo chmod +x /usr/bin/text2file

```

Add the below:
```

#!/bin/bash
for FILE in "$@"
do
convert $FILE /tmp/temp.tif
tesseract /tmp/temp.tif $HOME/Desktop/$FILE-output.txt
done

```

Something like that..... Not tested that but just hacked it out quickly

---

### Post by Impavidus on 2020-06-14
I think convert supports writing to a pipe, but I don't know if tesseract can read from a pipe. If it can (search the man page), you can use a pipe instead of a temporary file.

BTW, don't use sudo gedit. Make it at least sudo -H gedit, but the preferred solution is sudoedit.

---

### Post by Holger_Gehrke on 2020-06-14
The conversion isn't necessary. Tesseract uses the Leptonica library for reading images. It has been able to handle jpg for several years, even though there's still documentation floating around the net that says otherwise.

Holger

---

### Post by TheFu on 2020-06-14
+1 for using **sudoedit** 

To change the editor to gedt for sudoedit and other things like crontab -e, 
```
export EDITOR=gedit
``` so it will use gedit. Add that to your ~/.bashrc or other shell startup script.

manpages are pretty great:
```
NAME
       tesseract - command-line OCR engine

SYNOPSIS
       tesseract imagename|stdin outputbase|stdout [options...]
       [configfile...]
```
So tesseract can work with pipes in or out or both.

```
IN/OUT ARGUMENTS
       imagename
           The name of the input image. Most image file formats (anything
           readable by Leptonica) are supported.
```
as Holger_Gehrke says above.  All "hidden" in the manpage on the system.  i threw jpg and png files at it and both were OCR'd.  The jpg produced slightly better results for the same image

Saying *one step* isn't clear.  Typing 1 command that does 50 things could be 1-step to some people. Or looking for an existing single command that handles everything could be the interpretation.

---

### Post by raleigh3 on 2020-06-15
Thanks to all for the great help. :-)

---

