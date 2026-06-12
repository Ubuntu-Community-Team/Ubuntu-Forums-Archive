---
title: "Libreoffice corrupt file- help please"
date: 2021-05-30
forum: General Help
---

### Post by ronmx on 2021-05-30
hi all, new here. Working on Libreoffice went to open my spreadsheet ( that is 4 months old) and this error message appears: READ ERROR format error discovered in the sub-document content.xml at 2,543247 (row, col) 

after searching online and completing different possible solutions none have worked. Tried the zip- no go. Downloaded a recovery tool- no go. Tried the notepad- do not know what to look for or how to fix ( any suggestions then I can go thru this process) 
This spreadsheet is of great importance and recreating it is not possible after all the time that has been put into it. if anyone has time to respond I would greatly appreciate it. I need help!!  Thank you

---

### Post by dragonfly41 on 2021-05-30
I have had success in using XMLCopyEditor to open and validate corrupt XML files.

This last post refers ..

[https://askubuntu.com/questions/426009/how-can-one-open-an-xml-file-with-libreoffice](https://askubuntu.com/questions/426009/how-can-one-open-an-xml-file-with-libreoffice)

I have just looked in Synaptic Package Manager and both packages (including debugger) can be installed from repo.

I suggest that you first create a backup copy before any such experiments.

---

### Post by Holger_Gehrke on 2021-05-30
A few years ago there were two or three cases on this forum of people having corrupted OpenOffice or LibreOffice Writer files with similar error messages. Back then it was a repetition of an attribute, something like
```

<foo bar="1" bar="2" bar="3>some content of the foo-tag</foo>

```
which is clearly not valid, you can't have the same attribute multiple times on one tag.

Unpack the Office file with zip. Edit the content.xml file with an editor that doesn't get confused by extremely long lines (the content.xml has all content in one unbroken line, potentially several megabytes long) and  'understands' XML and can jump directly to the error (I know emacs can do it in xml-mode and I wouldn't be surprised if vim could too). Pack everything back together. Done.

Holger

---

