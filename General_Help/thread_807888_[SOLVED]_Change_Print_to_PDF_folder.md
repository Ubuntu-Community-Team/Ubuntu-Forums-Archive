---
title: "[SOLVED] Change Print to PDF folder"
date: 2008-05-26
forum: General Help
---

### Post by neur0 on 2008-05-26
How do I change the default folder to which the Print to PDF prints?
Right now it prints in the ~/PDF folder and creates it if its not there.

---

### Post by drsaamah on 2008-05-26
YES!  More information on how to customize the cups pdf printer would be greatly appreciated.  The other problem is that the "printed" pdf will automatically save the file as the web page title and will therefore overwrite any file in the ~/PDF folder that may already have that name.

---

### Post by latna on 2008-05-26
For the default directory.

```
sudo $EDITOR /etc/cups/cups-pdf.conf
```

Look under Path Settings for the Out directive.

I'm not sure about the file naming. There's a directive in that file to make cups use a name supplied on the command line instead of creating one of it's own. I'm not sure the gnome print dialog is quite as configurable though. I can't figure out how to do it with kde anyway.

---

### Post by Patb on 2008-05-26
According to [this link]("http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/"), you can supposedly edit the line "Out ${HOME}/PDF" in the file /etc/cups/cups-pdf.conf. 

But unfortunately I have never been able to make this work.  If I change "/PDF" to "/.PDF" say, it just goes through the print process but produces nothing.  Any suggestions would be appreciated.  

Cheers, Pat.

---

### Post by neur0 on 2008-05-26
Same problem, after changing the default, nothing prints.

---

### Post by latna on 2008-05-26
Hmmm... sorry about that, you're right. I just tried it on kde and noticed that I have a PDF option and a "print to file" option that lets me chose a file name, a directory to store it in, and whether I want to print to pdf or postscript. There's gotta be something like that in gnome I would think.

---

### Post by noynac on 2008-05-26
> **neur0 said:**
> How do I change the default folder to which the Print to PDF prints?
Right now it prints in the ~/PDF folder and creates it if its not there.
To change the PDF directory, you have to edit both the cups-pdf.conf and usr.sbin.cupsd files. The howto in post 12 of the following thread worked for me:

[http://ubuntuforums.org/showthread.php?t=626718](http://ubuntuforums.org/showthread.php?t=626718)

---

### Post by noynac on 2008-05-26
> **drsaamah said:**
> ...The other problem is that the "printed" pdf will automatically save the file as the web page title and will therefore overwrite any file in the ~/PDF folder that may already have that name.

Change the "Label" key in the cups-pdf.conf file to "1". Afterwards, a job ID will be added to all PDF's to prevent one PDF from overwriting another.

```
### Key: Label
##  label all jobs with a unique job-id in order to avoid overwriting old
##  files in case new ones with identical names are created; always true for
##  untitled documents
##  0: label untitled documents only, 1: label all documents
### Default: 0

Label 1
```

---

### Post by neur0 on 2008-05-26
Y, worked!
I found it was Apparmor that was guilty, but didn't know how to change it.
Thanks

---

