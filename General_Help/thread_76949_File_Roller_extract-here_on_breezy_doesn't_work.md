---
title: "File Roller extract-here on breezy doesn't work?"
date: 2005-10-16
forum: General Help
---

### Post by audax321 on 2005-10-16
I just noticed that the:

```

file-roller --extract-here <filename>

```

command doesn't seem to work. It asks me if it can create the directory and I tell it to create the directory, but it just gives me an error message saying:

> 
Extraction not performed

Could not create the destination folder: Generic error.


All of this is occurring in my home folder and it should not be having a problem creating a folder there.

Any ideas what is going on? Anybody else getting this error?

---

### Post by temcat on 2005-10-16
Working OK here.

---

### Post by audax321 on 2005-10-16
Hmmmm, thats odd. It doesn't work for me whether I run as root or not. Did you upgrade from Hoary or did you do a clean install of Breezy? I did a clean install on my laptop, but it works fine using the version of file-roller that came with Hoary. :???:

---

### Post by jordilin on 2005-10-16
Generally I don't use file roller, since I prefer using tar, gzip or bzip directly. In any case I have done a man over file-roller and it says that to extract in the current directory you must use # file-roller -f filename, you must pass the -f command. 
It doesn't say anything about the --extract-here command.
I've tried the command with the -f option, and I haven't had any problem. When you launch the command file-roller -f , a window pops-up asking you some questions such as the destination directory. All ok, I'm using Breezy Badger, fresh install,
Which version are you using?

---

### Post by audax321 on 2005-10-16
Well according to file-roller --help, the extract-here option is supposed to create a directory of the form <filename>_FILES and then extract the contents to that folder. This was the default for the extract here command in the Ubuntu right click menu until Breezy. Now the extract here command in the right click menu actually extracts to the current folder. So I want to have a nautilus-script that will make the <filename>_FILES folder and extract to it. 

Under Hoary, both:

file-roller --extract-here <filename>   (with prompt for confirmation)

AND

file-roller -f --extract-here <filename> (without confirmation)

work as they should. But under Breezy I get the directory creation error. I can, however, extract into the current directory. So it's just a problem with making the directory to begin with, not the actual extraction itself.

---

### Post by temcat on 2005-10-16
[QUOTE=audax321]Hmmmm, thats odd. It doesn't work for me whether I run as root or not. Did you upgrade from Hoary or did you do a clean install of Breezy? I did a clean install on my laptop, but it works fine using the version of file-roller that came with Hoary. :???:[/QUOTE]

Sorry, I was wrong, it doesn't work here either. But right-click menu option Extract Here does work, as does the -f option.

When on command line, I prefer tar -xvzf <filename> for tar.gz fuiles and tar -xvjf <filename> for tar.bz2 ones.

---

