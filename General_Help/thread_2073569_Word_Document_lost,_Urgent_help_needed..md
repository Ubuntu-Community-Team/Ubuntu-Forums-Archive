---
title: "Word Document lost, Urgent help needed."
date: 2012-10-19
forum: General Help
---

### Post by louisgonick on 2012-10-19
Greetings, 

I've spent the past hours working on sometihng I must hand in. I downloaded a file and without renaming it, I started working on it. I recall clicking the save button all the time to avoid any mishap. 

When I am finally done with it, I save one last time and close the Libre office window. The document was on my desktop, I try to re-open it and it had none of my work on it. NOTHING! I checked under other locations in case I have worked on another duplicate and nothing. 

For some reason, libreoffice didn't save anything I did. 

Re-writing it is not an option.


Thanks, 
any help is appreciated.

---

### Post by louisgonick on 2012-10-19
I'm extremely outraged right now. Doesen't libre office autosave in some sort of temp file? I remember clicking on the save button! Where did it go!

---

### Post by drmrgd on 2012-10-19
You might try to search the system for the file.  The command line 'find' command has an 'mtime' option that will allow you to search for files based on the last time they were modified:

```
find ~/ -type f -mtime 0 -iname "*.odt"
```

That will start searching your home directory for files that were modified today with an .odt extension on them.  I'm not sure if you kept the Libre Word extension or have an MS Office extension on it.  

This might be a starting point to try.

---

### Post by louisgonick on 2012-10-19
> **drmrgd said:**
> You might try to search the system for the file.  The command line 'find' command has an 'mtime' option that will allow you to search for files based on the last time they were modified:

```
find ~/ -type f -mtime 0 -iname "*.odt"
```

That will start searching your home directory for files that were modified today with an .odt extension on them.  I'm not sure if you kept the Libre Word extension or have an MS Office extension on it.  

This might be a starting point to try.

The file still exists, but no changes were made to it even though I saved my changes. 

Although, I believe that as I panicked, I may have replaced it for another blank copy of it.

Is there any way I can recover that replaced file?

---

### Post by oldfred on 2012-10-20
When I lost some files, I used photorec to recover them. But some of the text files I had saved almost daily for the couple of months since my last backup (more frequent now). Photorec found almost every copy, I was never sure I found the last saved version. But I had lots of room on drive so nothing was overwriting previous data on drive.

You can in photorec tell it to only look for certain file types, but it does not speed process as it still scans entire drive. On my system it took 6 hours to do scan, wrote many, many files only with extensions which I had to sort thru.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

---

### Post by Zill on 2012-10-20
A lot depends on how you have configured LibreOffice.  For example, in OpenOffice (which functionally is *very* similar to LibreOffice), the Tools, Options, Load/Save, General menu screen has the option to "Always create a backup copy".

The OpenOffice help then defines this option as:
> Always create a backup copy
Saves the previous version of a document as a backup copy whenever you save a document. Every time OpenOffice.org creates a backup copy, the previous backup copy is replaced. The backup copy gets the extension .BAK.
To change the location of the backup copy, choose Tools - Options - OpenOffice.org- Paths, and then enter a new path for the backup file.
If this option had been selected then your file *should* still be available with a .BAK extension in your chosen path.

---

### Post by Frogs Hair on 2012-10-20
Was _save as_ used to move the document to a directory/ folder  when you started or just save ?  I don't think Libre Office stores items in recent documents unless saved in a directory  It will only list them .

---

### Post by critin on 2012-10-20
> I checked under other locations in case I have worked on another duplicate and nothing. Is this a Microsoft Word document?  

I just modified a shared Word Perfect doc in Libre to see where it goes and I found a bak copy in recent documents, a saved copy in three different formats in my Documents folder, and another copy in my shared doc folder.  I did not change the title or format.

I also checked in the dash under find files and they were all there too.
I'm sure it's there somewhere.

---

