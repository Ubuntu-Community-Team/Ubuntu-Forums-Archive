---
title: ".abw File rescue"
date: 2005-05-03
forum: General Help
---

### Post by Chen_Zhen on 2005-05-03
Hello everyone, I'm new to this forum and to the unix world as well. 
I was working on a document using Abiword and, after reseizing an image I had just inserted, the program went crazy and I was forced to close it. Now everytime I try to open this file (which is .abw format), Abiword fails to load it properly, the page starts flashing very fast and I cannot do anything. I have tried to open the file on Open Office but instead of the proper file I get the abiword code. Please somebedy help me, I am really desperate since this file I was working on is my univesity thesis and I haven't got much time to finish it.
Thanks in advance.

---

### Post by ow50 on 2005-05-03
You can try converting your document to RTF format using Abiword. At the terminal type:
```
abiword --to=rtf filename.abw
```

Any word processor, OpenOffice for example,  should be able to open RTF.

---

### Post by Chen_Zhen on 2005-05-03
In this document I have used many Chinese characters (that's what I'm graduating in), if I convert in rtf format will I lose anything?
Thank you

---

### Post by ow50 on 2005-05-03
[QUOTE=Chen_Zhen]In this document I have used many Chinese characters (that's what I'm graduating in), if I convert in rtf format will I lose anything?
Thank you[/QUOTE]

Probably not, but I wouldn't know for sure. Just try it to find out. Converting will keep your original abw file untouched.

---

### Post by Chen_Zhen on 2005-05-03
Thank you! It works! You have no idea how much you have helped me, thank you really

---

