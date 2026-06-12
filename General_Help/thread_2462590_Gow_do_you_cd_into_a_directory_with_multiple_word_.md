---
title: "Gow do you cd into a directory with multiple word name?"
date: 2021-05-24
forum: General Help
---

### Post by sofasurfer on 2021-05-24
File is in  /Home/Username/ Documents/Folder Containing PDF Files/names.pdf
I want to grep the names.pdf (I'm new to grepping). I can cd to 'Documents' but how do I cd to 'Folder Containing PDF Files'

---

### Post by The Cog on 2021-05-24
Use quotes round the filename, or use a backslash in front of the spaces. I guess you mean /home (Linux is case sensitive), and there is not really a space before Documents.
```

cd "/home/Username/Documents/Folder Containing PDF Files/names.pdf"
# or
cd '/home/Username/Documents/Folder Containing PDF Files/names.pdf'
# or 
cd /home/Username/Documents/Folder\ Containing\ PDF\ Files/names.pdf'

```
Note that 
You can use "tab completion" to finish partially entered filenames which helps a lot (type the start of the name then press the tab key). This will either finish the filename or stop and wait where there is more than one possible next letter. So this will probably get you there:
```
cd /ho**<TAB>**Username/Doc**<tab>**Fold**<tab>**names**<tab>**
```

---

### Post by ajgreeny on 2021-05-24
I always replace spaces in a file or folder name with an underscore to avoid so many of these problems.

In my Xubuntu I have a custom actions item to do this with a right click using command ```
rename 's/\ /_/g' %F
```
Dead simple, very quick, and incredibly useful.

---

### Post by HermanAB on 2021-05-24
As shown above already, quotes and tab are your friend.

---

### Post by TheFu on 2021-05-24
In addition to using tab-completion, I will use wildcard patterns in shells.
BTW, grep doesn't really work on PDF files.  Need to convert those to text .... **pdftotext** is the tool for that.  PDF files are encoded using ASCII-85 and can be compressed, making text search tools not so good.

So, if I wanted to look inside this (I think it has typos with an extra space BEFORE "Documents" and /Home is also wrong, but whatever, it is what you provided, assuming that is all correct)
 /Home/Username/ Documents/Folder Containing PDF Files/names.pdf
I'd use
```
$ pdftotext /Hom*/User*/*Doc*/Fol*/names.pdf - | egrep {some kewl regex}
```
If I correct it for the bad typos above, I'd use
```
$ pdftotext ~User*/Doc*/Fol*/names.pdf - | egrep {some kewl regex}
```

Let me go test that. Yep, the trick is that pdftotext only accepts a single input file, so to search multiple files at the same time, we'd need to wrap the pdftotext use in a loop ... I typically do that like this:
```
#!/bin/bash
for filename in "$@"; do
   echo "INFO: Searching on $filename
   $(/usr/bin/pdftotext  $filename - | egrep -i {some kewl regex})
done
```

To use this script, say it is ~/bin/pdfgrep, then
```
$ ~/bin/pdfgrep ~User*/Doc*/Fol*/*.pdf
```

All sorts of caveats exist doing this.  Input filenames cannot have spaces because spaces are the default delineation character for "$@" expansion.  There are ways to handle that, but they are all a hassle.  As ajgreeny & Herman say, removing all spaces from directory and filenames is step one to a happier life using scripts.  I fought this for a few years, before giving up and just removing any funky characters from all filenames.  That was over 20 yrs ago and I've been so much happier in my scripting since doing that.

---

### Post by dragonfly41 on 2021-05-24
RipGrep searches also PDF .. and other types ...

[https://github.com/phiresky/ripgrep-all](https://github.com/phiresky/ripgrep-all)

---

### Post by sofasurfer on 2021-05-26
Wow! You guys are like some kind of space alien geniuses from the future. It took me about an hour to figure this out. I settled on the quotation mark method. I was very impressed with the tab method. I used both. I was able to convert the pdf into text and save it. I then grepped the text file and scrolled through it forward and backward. Now I can't remember why I wanted to do this. I'm sure it will come to me eventially. Thanks.

---

