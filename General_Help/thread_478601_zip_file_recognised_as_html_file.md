---
title: "zip file recognised as html file"
date: 2007-06-19
forum: General Help
---

### Post by mysfit_i on 2007-06-19
I recently installed Ubuntu 7.04 and have noticed a problem when I download .zip files.

When I save them to my hardrive they initially show as an archive file with the open box icon as I expect.
Trouble is when I right-click on them to extract, the icon changes to a page with a world on it.
If I click on it I get the following message:

[I]Cannot open genj_app-2.4.3.zip
The filename "genj_app-2.4.3.zip" indicates that this file is of type "ZIP archive". The contents of the file indicate that the file is of type "HTML document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "HTML document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. [/I]

If I right-click and open with Archive Manager I get the following message:
[I]
An error occurred while loading the archive.[/I]

I come across an almost identical problem with .jar files as well.

Being a newbie and coming across such problems I haven't a clue where to start in correcting this :-(

Can anybody here help?

many thanks

massedgadget

---

### Post by RedSquirrel on 2007-06-19
This may not help you much, but...

I use the program "unzip" in a terminal to unzip files with the .zip suffix.

I'm not sure if it's installed by default, but it's in the repositories.

```
sudo apt-get install unzip
```

```
man unzip
```

---

### Post by incubus on 2007-06-19
unzip does come installed by default.

I would imagine it's a problem with the archive manager.  What is its name in Gnome?  I could try to reinstall it.

incubus

---

### Post by mysfit_i on 2007-06-20
I already had thought of trying unzip in a terminal, but when I do I get the following message:

Archive:  genj_app-2.4.3.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of genj_app-2.4.3.zip or
        genj_app-2.4.3.zip.zip, and cannot find genj_app-2.4.3.zip.ZIP, period.

And it is not a multidisc archive and it is a zip file because on a previous installation I downloaded it and installed it OK :-(

Does this error message shed any light on my problem?

cheers

David

---

