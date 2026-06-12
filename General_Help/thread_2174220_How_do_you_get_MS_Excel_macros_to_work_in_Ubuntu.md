---
title: "How do you get MS Excel macros to work in Ubuntu?"
date: 2013-09-13
forum: General Help
---

### Post by marinecomm on 2013-09-13
I have a spreadsheet writting in MS Excel, an .xls document, which contains macros. I'm having a problem finding a program what will allow me to open the document and the macros work. 

I tried opening the document in LibreOffice and the macros won't work even though I went to **Tools -> Options -> Load/Save -> VBA Properties ->** and made sure Load Basic Code and Executable Code were both checked. I even went to **Tools -> Options -> Security -> Macro Security ->** and set it to Low. I converted the .xls document to a LibreOffice document and LibreOffice still won't run the macros. 

I tried Gnumeric. Some of the macros seemed to work in Gnumeric but most of them didn't.

I installed Calligra and tried opening it with Sheets, but Calligra just freezes and I have to force quit out of it.

I do not have Windows, I do not own MS Office and have no means or desire to buy either one. 

So, what other options are there left for me? I have been searching around Google/Bing but haven't found a solution yet. any thoughts or ideas? i'm running Xubuntu 12.04 64-bit. Thank you.

---

### Post by oldfred on 2013-09-13
I have not tried for years, so someone may know if better now.

Whenever I tried converting a spreadsheet, I always had to go in and edit a few commands as they do not convert 100%. I did not know details of commands in either system but in a couple of cases was to single step thru, find error and look up correct command in OpenOffice. Have not tried lately with LibreOffice, but should be similar. But it is a lot of work. Sometimes easier just to start over.

---

### Post by vasa1 on 2013-09-13
Read [https://help.libreoffice.org/Common/Using_Microsoft_Office_and#Macros_in_Microsoft_Office_and_LibreOffice](https://help.libreoffice.org/Common/Using_Microsoft_Office_and#Macros_in_Microsoft_Office_and_LibreOffice)

---

### Post by Lars Noodén on 2013-09-13
I don't do macros any more but would point out anyway that one major advantage of LibreOffice is that you can do your macros in Python or JavaScript.  No need to learn a separate language just for macros any more.

---

