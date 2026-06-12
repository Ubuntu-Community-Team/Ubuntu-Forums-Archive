---
title: "Text to PDF"
date: 2023-04-11
forum: General Help
---

### Post by zkab on 2023-04-11
I have a directory with a lot of subdirectories.
In each subdirectory there are plain text-files (*.txt).
Now I want to convert all text-files to PDF-files.
How can that be done with a command line?

---

### Post by ajgreeny on 2023-04-11
Simply run the following command.

```
cupsfilter filename.txt > filename.pdf
```

For options etc. please refer to cupsfilter man pages.

It should be simple to create a script to do this to all files ion a folder.

---

### Post by Holger_Gehrke on 2023-04-11
If you want your output slightly more fancy, you could play around with a2ps (anything to postscript) and ps2pdf.
```

a2ps inputfile.txt --output=-|ps2pdf - outputfile.pdf

```
will produce a pdf with landscape pages with two columns with a border around the columns and headers / footers giving a lot of extra information. Play around with the many options it has to get output as plain or as elaborate as you want ...
a2ps is in the repositories under that name, ps2pdf is part of the package ghostscript.

Holger

---

### Post by dragonfly41 on 2023-04-11
pandoc

---

### Post by TheFu on 2023-04-11
I'd use the 'find' command to get a list of the files.

```
find TOPDIR -type f -iname \*txt -exec **txttopdf** {} \;
```
There must be hundreds of methods.  **Pandoc** can do it too. [https://unix.stackexchange.com/questions/17406/how-to-convert-txt-to-pdf](https://unix.stackexchange.com/questions/17406/how-to-convert-txt-to-pdf) has some other options.

BTW, txt is a universal format, easy to search, easy to manipulate for other needs, highly compressible.  

In 2000, my employer asked me to convert millions of text pages to a format for archival purposes.  They wanted the files to be read-only.  I mistakenly selected PDF. These days many PDF files can be edited.  So the effort to create a read-only archive would have been better spent using permissions, compression, and leaving the files as text.  Live and learn.

---

### Post by zkab on 2023-04-12
> **TheFu said:**
> 
```
find TOPDIR -type f -iname \*txt -exec **txttopdf** {} \;
```
I use
```
find TOPDIR -type f -iname \*txt -exec libreoffice --convert-to "pdf" --outdir TOPDIR {} \;

```
but the converted pdf files are not placed in the subdirs where *txt reside ... all pdf files are placed in TOPDIR

---

### Post by SeijiSensei on 2023-04-12
Just change --outdir TOPDIR to --outdir /path/to/target/directory

Make sure the directory exists before running the command.

---

### Post by zkab on 2023-04-13
Maybe I was not clear.
In my TOPDIR there are subdirs s1, s2, s3 ...
In every subdir s1, s2 ,s3 ... there is a text-file that I want to convert and place the converted pdf-file in the same subdir as the text-file.
So subdir s1, s2, s3  should have the text-file & pdf-file after the conversion ...

What yoy sggest ```
--outdir /path/to/target/directory
``` will result that all converted pdf-file are place in one subdir ```
--outdir /path/to/target/directory
```

---

### Post by Holger_Gehrke on 2023-04-13
Create a script like
```

cd $(dirname $1)
libreoffice --convert-to "pdf" $1
cd -

```
and have find -exec that script.

Holger

---

### Post by zkab on 2023-04-13
I made a testcase with TOPSPOT consist of 2 subdir (s1 & s2)
As you can see there are 2 txt-files:
```

[forsete@balder: ~/Downloads] $ find TOPSPOT -type f -iname \*txt
TOPSPOT/CD_000/CD_000_00_Innehåll.txt
TOPSPOT/CD_001/CD_001_00_Innehåll.txt

```
Then I ran find & executed the script 'pdf.sh' ...
```

[forsete@balder: ~/Downloads] $ find TOPSPOT/ -type f -iname \*txt  -exec ./pdf.sh  {} \;
/home/forsete/Downloads
/home/forsete/Downloads

```
No pdf-files were created ...
```

[forsete@balder: ~/Downloads] $ find TOPSPOT -type f -iname \*pdf
[forsete@balder: ~/Downloads] $ 

```
Here is the script:
```

[forsete@balder: ~/Downloads] $ cat pdf.sh
#!/bin/bash

cd $(dirname $1)
libreoffice --convert-to "pdf" $1
cd -

```
Where have I missed?

---

### Post by Holger_Gehrke on 2023-04-13
The braces in the find command need to be quoted or escaped, otherwise the shell will remove them before find is even called. So the command should be:
```

find TOPSPOT/ -type f -iname '*txt'  -exec ./pdf.sh  '{}' \;

```

Holger

---

### Post by zkab on 2023-04-19
Not working ...
```
$ find TOPSPOT/ -type f -iname '*txt'  -exec ./pdf.sh  '{}' \;

(soffice:59500): Gtk-WARNING **: 10:21:06.074: Theme file for Oxygen_White has no directories
Error: source file could not be loaded
/home/forsete/Downloads

(soffice:59550): Gtk-WARNING **: 10:21:06.577: Theme file for Oxygen_White has no directories
Error: source file could not be loaded

```

---

### Post by Holger_Gehrke on 2023-04-19
Just tried it and found the problem. I assumed - from my own habits - that you'd use an absolute path for the starting directory in the find command. In that case the parameter ($1) passed from find to the script would be something like /home/username/topdir/s1/file.txt and libreoffice would find the file. With a relative path - like 'topdir' while the current working directory is $HOME - find would pass 'topdir/s1/file.txt, the script would 'cd' into 'topdir/s1' and then call 'libreoffice --convert-to "pdf" topdir/s1/file.txt'. That file obviously doesn't exist. So to get it to work, I changed the script to
```

#!/usr/bin/env bash

cd $(dirname "$1")
libreoffice --convert-to "pdf" **$(basename "$1")**
cd -

```
and that worked as it should. The double quotes around "$1" are there in case there are spaces in the file or directory names; while using spaces is usually ... discouraged ... by a lot of experienced users, I have gotten into the habit of doing this a long time ago, which means I usually have to be a bit more careful about quoting when scripting.

Holger

---

### Post by The Cog on 2023-04-19
find has a **-execdir** option: > Like  -exec,  but  the specified command is run from the subdirectory containing the matched file

---

### Post by zkab on 2023-04-20
Thanks ... it works OK

---

