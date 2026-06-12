---
title: "Is there a program like LS for web pages?"
date: 2008-02-25
forum: General Help
---

### Post by disturbedite on 2008-02-25
we all know & love ls, but is there a program like it to display the contents of web pages?

i.e.
ls [http://www.google.com/](http://www.google.com/)
file1
file2
file3
etc

---

### Post by HermanAB on 2008-02-25
man wget

---

### Post by disturbedite on 2008-02-25
ah.  i didn't know wget had that ability.  i guess i assumed it could only retrieve.  but on second thought, i suppose if its able read a site's structure, it should be able to list it...

---

### Post by mrsteveman1 on 2008-02-25
Unless the webserver has indexes enabled the only files you will be able to see are those files listed in or linked to from the index.html page, because by default the browser/wget doesn't know any other page exists.

---

