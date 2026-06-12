---
title: "pdf printer does not create fpdf file"
date: 2008-03-18
forum: General Help
---

### Post by cybergalvez on 2008-03-18
I'm using ubuntu 7.10, and I added the pdf printer to my printers, however then I do a test print nothing ends up in my PDF folder.  What should I do?
Jose

---

### Post by Cybergod on 2008-03-18
> **cybergalvez said:**
> I'm using ubuntu 7.10, and I added the pdf printer to my printers, however then I do a test print nothing ends up in my PDF folder.  What should I do?
Jose

I'm really not familiar with the pdf printer.  If you are using OpenOffice, you can export your material as PDF from there.

---

### Post by cybergalvez on 2008-03-18
> **Cybergod said:**
> I'm really not familiar with the pdf printer.  If you are using OpenOffice, you can export your material as PDF from there.

True, and I generally do use openoffice when I can, bu toccationally I need to generate PDF's from other applications and the pdf printer is a convenient way to make them, when it was working at least it was.

Jose

---

### Post by cybergalvez on 2008-03-20
> **cybergalvez said:**
> I'm using ubuntu 7.10, and I added the pdf printer to my printers, however then I do a test print nothing ends up in my PDF folder.  What should I do?
Jose

Still hoping to find an answer for this one, anyone out there with some suggestions?
Jose

---

### Post by Cybergod on 2008-03-20
Go to System>Administration>Printing, and select PDF in the left pane.  Now to the right you'll see "Printer State".  What is the state?  Click the "Policies" tab  and see if "Enabled" and "Accepting Jobs" is checked under State.  Click the "Access Control" tab and make sure the dot is besides "Allow...".   If everything is correct here, click back on the "Settings" tab and then click "Print Test Page".  Now look in the PDF folder in your home folder and see if the test page is in there.  If it still doesn't work after this, edit the /etc/cups/cups-pdf.conf file.
```
gksudo gedit /etc/cups/cups-pdf.conf
```
Look for
```
Out ${HOME}/somethinghere
```
and change to 
```
Out ${HOME}/PDF
```

---

### Post by cybergalvez on 2008-03-21
> **Cybergod said:**
> Go to System>Administration>Printing, and select PDF in the left pane.  Now to the right you'll see "Printer State".  What is the state?  Click the "Policies" tab  and see if "Enabled" and "Accepting Jobs" is checked under State.  Click the "Access Control" tab and make sure the dot is besides "Allow...".   If everything is correct here, click back on the "Settings" tab and then click "Print Test Page".  Now look in the PDF folder in your home folder and see if the test page is in there.  If it still doesn't work after this, edit the /etc/cups/cups-pdf.conf file.
```
gksudo gedit /etc/cups/cups-pdf.conf
```
Look for
```
Out ${HOME}/somethinghere
```
and change to 
```
Out ${HOME}/PDF
```
 
Everything under system>administration>printing is giid, but I don't seem to have a /etc/cups/cups-pdf.conf file

Jose

---

### Post by cybergalvez on 2008-03-26
bump, anyone out there with some advice?
Jose

---

### Post by Andavane on 2008-03-27
> **Cybergod said:**
> Go to System>Administration>Printing, and select PDF in the left pane.  Now to the right you'll see "Printer State".  What is the state?  Click the "Policies" tab  and see if "Enabled" and "Accepting Jobs" is checked under State.  Click the "Access Control" tab and make sure the dot is besides "Allow...".   If everything is correct here, click back on the "Settings" tab and then click "Print Test Page".  Now look in the PDF folder in your home folder and see if the test page is in there.  If it still doesn't work after this, edit the /etc/cups/cups-pdf.conf file.
```
gksudo gedit /etc/cups/cups-pdf.conf
```
Look for
```
Out ${HOME}/somethinghere
```
and change to 
```
Out ${HOME}/PDF
```

I went into "etc" and found the cups-pdf.conf file.
Re: the changing "/somethinghere" to "/pdf" I see in the file it is already set to pdf.
Also from reading the file I see that the writer says he'd like to know if something is working or isn't working.

I'd like to tell him, but do not know how.
Going inside these files is entirely new to me, and still think of myself very much as beginner, even if not absolute beginner.

How can I get back to him?

It seems I am not the only one who is having troubles printing any screen to a pdf from gutsy.

As I remember last year in "Feisty Foal" the pdf-maker worked fine.

Would really appreciate a solution as at the moment I go back to Windows XP to access the pdf-maker.

best wishes

John

---

### Post by gaussian on 2008-03-27
I was struggling with this too. This is how it worked for me (YMMV):

1) If I try to print a pdf-test page it appears to go nowhere (from Administration-Printers). I finally found it in /var/spool/cups-pdf/anonymous or something like that (not on my ubuntu computer, cannot check right now). It was under /var/spool anyway

2) If  I use an application to print something gives an option under cups-pdf to print to a file (this at least worked from Thunderbird) Checking that it worked perfectly, the file appeared in $HOME/PDF.

Even if this does not work you don't have to boot up to Windows to create pdf's. Just create yourself a Generic Postscript printer, print to a file and use command line tool ps2pdf to convert to pdf.

---

### Post by Andavane on 2008-03-27
ArsGeek's blog ha solved this for me here on gutsy.
[http://www.arsgeek.com/?p=1720]("http://www.arsgeek.com/?p=1720")
the steps in gutsy weren't exactly the same.
If you select "other" then "generic" and add a postscript file, and name it to something you recognise.
I rebooted and then tried it and it worked.

One simple tip when following the blog:
If you can't see the small pictures, right-click on them and choose:
"Open Link in New Tab"
It then appears in a separate tab in firfefox and can be read easily, then you just click on the previous tab to see where you were.

A very basic thing indeed, but some may not know it and try in vain to read the small pictures.

andavane

---

### Post by stchman on 2008-03-27
> **cybergalvez said:**
> I'm using ubuntu 7.10, and I added the pdf printer to my printers, however then I do a test print nothing ends up in my PDF folder.  What should I do?
Jose

Try this.

[http://www.stchman.com/pdf_cups.html](http://www.stchman.com/pdf_cups.html)

---

