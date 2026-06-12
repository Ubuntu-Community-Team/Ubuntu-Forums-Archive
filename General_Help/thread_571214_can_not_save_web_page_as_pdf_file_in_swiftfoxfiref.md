---
title: "can not save web page as pdf file in swiftfox/firefox?"
date: 2007-10-09
forum: General Help
---

### Post by chunchengch on 2007-10-09
How can I save web page as a pdf file instead of html in swiftfox(firefox)? thanks!

---

### Post by dcstar on 2007-10-09
> **chunchengch said:**
> How can I save web page as a pdf file instead of html in swiftfox(firefox)? thanks!

[http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/](http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/)

---

### Post by chunchengch on 2007-10-09
dcstar,

Thanks!

I installed cups-pdf and saved a web page as pdf file, while when I tried to open it with Adobe Reader, the program said it is not a "supported file type", however, the file could be opened with Envice, what is the problem?

[ATTACH]45747[/ATTACH]

---

### Post by kerry_s on 2007-10-09
> **chunchengch said:**
> dcstar,

Thanks!

I installed cups-pdf and saved a web page as pdf file, while when I tried to open it with Adobe Reader, the program said it is not a "supported file type", however, the file could be opened with Envice, what is the problem?

[ATTACH]45747[/ATTACH]

try adding .pdf to the name instead of just "test" use "test.pdf".
double check make sure you set everything up right.

---

### Post by chunchengch on 2007-10-09
I rename "test" to "test.pdf", and the result is the same. 
Envice can open it, Adobe Reader can not.

[ATTACH]45815[/ATTACH]


Here are the snapshots of setting of the PDF printer (cups-pdf),

[ATTACH]45816[/ATTACH]
[ATTACH]45817[/ATTACH]
[ATTACH]45818[/ATTACH]

---

### Post by ellis rowell on 2007-10-10
If you save a text file with a .pdf suffix it does not make it a .pdf, it has to be saved by software which will convert it to .pdf. The key lies in the fact that all files contain a key to their format in the first few characters of the file. 

In the early days the Sinclair QL had an Archive database, Archive files could be left "open" by closing Archive without closing the file. The difference was one character, Archive could not open the file because it was already "open", we had to use a file editor to change the character.

Apparently Evince can open a text file whereas Adobe Reader cannot.

---

