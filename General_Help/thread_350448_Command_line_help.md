---
title: "Command line help"
date: 2007-01-31
forum: General Help
---

### Post by fearevilleet on 2007-01-31
Hello,

This is probably a really simple question but I can not figure it out. I am trying to unrar some files via the CLI via ssh but the file names have spaces in them.

Nine Inch Nails.part01.rar

I tried unrar 2 Nine Inch Nails.part01.rar and received the error

Cannot open Nine.rar
No files to extract

I also tried unrar e Nine_Inch_Nails.part01.rar with the same results. 
 
I do a space in the CLI?

Thanks

---

### Post by bodhi.zazen on 2007-01-31
[list=number][*]Use tab completion. Start to type the file name, Nine<tab>
[*]Use a \ to escape the space: > Nine\ Inch\ Nails.part01.rar
[*]Use quotes> "Nine Inch Nails.part01.rar"[/list]

---

