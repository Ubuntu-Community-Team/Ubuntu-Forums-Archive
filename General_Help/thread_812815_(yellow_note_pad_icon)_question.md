---
title: "(yellow note pad icon) question"
date: 2008-05-30
forum: General Help
---

### Post by e24ohm on 2008-05-30
I honestly can not remember the exact name of the application, but it is the basic note pad editor (yellow note pad icon).

The other day I created a document and saved it, but then I needed the document so I emailed it to myself. When I open the document on a windows base machine, at the end of each line there is a small square right after the period to end a sentence.

Do I have to format the text document in any special way from the command line? I remember ready something along the lines of this a few months back, but now I can not find the resource from which I thought I read it from.

Thank you,

---

### Post by pointone on 2008-05-30
Windows uses a different "newline" character than Linux.

You can install the "tofrodos" package and run "unix2dos <filename>" to convert the file to a Windows-readable format, or run "dos2unix" to convert the other way. I am not sure what programs exist in Windows for this. I believe certain programs (Office, Wordpad?) will interpret the file correctly, regardless, and simply opening and saving the file in these will reformat the file.

---

