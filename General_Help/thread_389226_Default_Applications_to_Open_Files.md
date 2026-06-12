---
title: "Default Applications to Open Files"
date: 2007-03-20
forum: General Help
---

### Post by Catsworth on 2007-03-20
Hi Guys,

I'm having a couple of problems with file opening that I'm hoping someone can help me out with.

1.  Whenever I open a PDF file (with a .pdf) extension it opens using 'Document Viewer', I have Adobe Reader installed and would like it to open with that.

2.  Whenever I open a .doc file (from MS Word) it opens the virus checker, and the file is scanned.  I have OOo installed and would like it to open that.

What I want to change is what I would know in Windows as the association between file extensions and their default applications, I understand though that Ubuntu doesn't use file extensions as such.

Much of the advice here on the forum suggests right-clicking on the file, choosing 'Open With Other Application', and then choosing the required application - the advice given also suggests that this selected application will then become the default.

I have tried this, and it isn't working.  In order to open .doc files I have to continue right-clickig and choosing OOo otherwise it simply keeps opening the virus checker.

If anybody can help with this I would really appreciate it, I need to get these 'file associations' sorted because it's really driving me mad now :(

Thanks.

---

### Post by jeffathehutt on 2007-03-20
The easiest way to change associations is like this:

Right click on one of the files you want to open, then select properties.  There should be an "open with" tab at the top, where you can select a new program.  From this point on, it should open all the files of that type with the new program.

---

### Post by Catsworth on 2007-03-20
Fantastic!

Thanks very much, looks like I was misunderstanding the previous 'right-click' instructions, all sorted now - you're a :KS

---

### Post by kenmiles on 2007-03-20
Change default application
sudo gedit /usr/share/applications/defaults.list

Regarfs, Kenneth.

---

### Post by Catsworth on 2007-03-20
Another way, cool - thx :)

---

