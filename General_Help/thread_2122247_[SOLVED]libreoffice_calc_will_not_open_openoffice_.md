---
title: "[SOLVED]libreoffice calc will not open openoffice calc file"
date: 2013-03-04
forum: General Help
---

### Post by col48 on 2013-03-04
I am running Ubuntu 10.04 (32-bit) and have OpenOffice 3.2 in which I have a spreadsheet (which I regularly edit) containing a macro which is invoked when I click on a button which occupies the area of one cell.  The spreadsheet contains just one sheet.  It is the only spreadsheet I have which includes a macro.

I have obtained a DVD with Ubuntu 12.04 (64-bit) and wanted to check hardware compatibility.  So I try it as a 'Live' DVD to check.  Naturally, it uses LibreOffice in place of OpenOffice.  I think it's version 3.5.  I find it can open other spreadsheets happily but it objects to the one with a macro, coming up with 'Unknown Error 305' [I think it's 305].  The file is not particularly large.

How can I get round this?  If push came to shove, perhaps I could export the OO spreadsheet as a csv and paste the macro into a txt and import the results into LO - would this work?  But I'd like to know why it is happening and whether there is a more straightforward solution - which could be implemented in OO before making the switch which I will probably eventually make.

[I'm not around much to review responses for a few days so apologies in advance for this]

---

### Post by lechien73 on 2013-03-04
It sounds like it could be a replica of this issue: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/972595](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/972595)

The good news is there appears to be a solution, but you probably won't be able to apply the fix to a Live DVD.

Hope this helps.

---

### Post by col48 on 2013-03-05
Thanks, lechien, looks very likely, although as you say I don't think I can apply it to a LiveDVD.

I'll leave this open until I have installed 12.04 which won't be until I'm a bit less busy.

---

### Post by Cheesemill on 2013-03-05
If the fix is just to install LibreOffice Base then this *can* be done using the Live DVD.

You can install any software you want when running from a Live DVD (limited in size to half your machines RAM), it just won't be there after a reboot.

---

### Post by col48 on 2013-05-06
Version 3.5.7.2 (64bit) does not have this problem - as installed today - so I'm marking this as solved.

---

### Post by col48 on 2013-05-11
This post is just to add SOLVED to the title

---

