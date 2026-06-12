---
title: "Openoffice won't open opendocuments?"
date: 2006-12-19
forum: General Help
---

### Post by lorenzo on 2006-12-19
Hi,
yesterday I have installed OOo 2.1.0 but, before that, I have installed OOo 2.0.4-2. That broke something on file association, I suppose, so now my problem is:

1) I can open my OOo documents with OOo 2.1.0 with "Open with"
2) I can associate in nautilus preferences OOo as default application

but still....

If I double click on the document it says that "even if it is called xxxx.ods it is a java archive" and that "for security reason it won't open it" and to "use open with".

Any suggestion on how to fix it?

Thanks,
Lorenzo

---

### Post by blueturtl on 2006-12-19
Right click the .ods file and select properties.
From the window that opens select the tab 'Open with...'
In this tab you can see the programs that appear in the 'Open with...' menu.
Out of the ones on the list the one that is checked is the one that will be used when you double click this type of file. If you don't have a proper option for OpenOffice you can click the 'Add' button in the lower right corner of the window to manually add OpenOffice and fix the association.

---

### Post by lorenzo on 2006-12-19
That's the first thing I did: does't work!

OOo is set as default for open with. But Nautilus still refuse to open it directly. ](*,) 

Any more suggestion?

---

### Post by lorenzo on 2006-12-20
More info: Nautilus shows my OOo documents with "application/x-java-archive" MIME types...

does anyone knows how to correct this?:-k 

Thanks,
Lorenzo

---

### Post by lorenzo on 2006-12-20
More: when I open Nautilus I can see my OOo spreadsheet (.ods) as "OpenDocument - Spreadsheet" but If I just single click on it (without opening it) it changes to "Java Archive".

I'm totally lost!:( 

Any help?

Thanks,
Lo

---

### Post by saceirdoth on 2006-12-21
+1 (i have stayed with openoffice 2.0.4, but i have installed java 1.6.0)

---

### Post by blueturtl on 2006-12-28
Did you install the new open office from the repos or somewhere else? AFAIK if you install from outside the official repos you are throwing yourself at the mercy of the people who packaged the software for you. Did you do a full uninstall of the OpenOffice packages before you updated?

---

### Post by lorenzo on 2006-12-28
Well, probably I messed up something... btw:

1) I have installed from the Ooo tar, with alien + dpkg
2) I have removed some old OOo packages afterwards...

I can try cleaning up everything and install it again but I really would like to know WHERE the problem is. OOo 2.1.0 works smoothly. I just dont understand how ubuntu (or is it gnome) determine MIME types and why does not let me do what I want to do.

---

### Post by lotto on 2006-12-28
First of all, sorry for hijacking the thread! I have the same kind of trouble with MIME types.
I have Ubuntu Dapper Drake with Gnome installed. 
Real audio file .ram has text file icon, its MIME type is "text/plain" and it opens with text editor. I cannot remove this entry. 
Although I can add a streaming audio application to open the .ram file it is no good, because it results in all files with MIME type of text/plain to open with the audio application.

Help would be very much appreciated!

---

### Post by lorenzo on 2007-01-09
Help!
Still having the same problem. There's more. Now in Nautilus when I chose "properties" of an OOo document, it hangs....

sigh! ](*,)

---

### Post by malmjako on 2007-02-11
I have this problem too. It only started appearing a couple of days ago, and ZIP archives are also identified as some kind of java file.

---

### Post by ljulliar on 2007-05-18
I went through the same upgrade process with OpenOffice 2.2 and had the same problem. I fixed it by uninstalling the JRE 1.6 package which is not really necessary if you have java installed already. It's this package which seems to break file associations. Once you have removed the JRE 1.6 package make sure to log out and log in again.

---

### Post by hutzut on 2008-01-31
This problem happens every time I install a new revision of Java.  I found the fix on a redhat forum.

[http://www.redhat.com/archives/rhl-list/2007-March/msg03614.html](http://www.redhat.com/archives/rhl-list/2007-March/msg03614.html)

Steps to fix:

edit '/usr/share/mime/packages/x-java-archive.xml'

find the 'match' tag with the missing '<' at the beginning, probably line 35.

[FONT="Courier New"]        match type="host16" value="0xcafe" offset="40" />[/FONT]

Add the '<'

[FONT="Courier New"]        <match type="host16" value="0xcafe" offset="40" />[/FONT]

Save the file.

From the command line run:

[FONT="Courier New"]$ sudo update-mime-database /usr/share/mime[/FONT]

Log out and back in.

---

