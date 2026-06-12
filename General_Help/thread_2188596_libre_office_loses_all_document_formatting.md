---
title: "libre office loses all document formatting"
date: 2013-11-18
forum: General Help
---

### Post by jimw on 2013-11-18
I'm using ubuntu 12.04.  Suddenly yesterday when I opened the latest chapter I'm writing,  the document all came out in one page.  I was able to fix it by hitting _View/Web layout_, but today the same problem occurred, and I couldn't fix it.

Since I'm using a dual boot system, I switched over to Windows, opened the same doccument, and it was properly formatted.

Has anybody else had this problem?  

I've been wondering if it's  a problem with the Linux?

BTW, my wife can take a thumb drive with my documents on it, and they all open properly on her machine.

JimW

---

### Post by ajgreeny on 2013-11-18
Sounds like a LO configuration problem to me which may be solved by renaming the hidden **libreoffice** folder in your /home, which for me using xubuntu is **~/.config/libreoffice**.

Certainly worth a try and if it messes everything up just delete the new libreoffice folder and restore the original.

---

### Post by jimw on 2013-11-18
I've tracked  down the appropriate file, but I'm a little leery about renaming it.  I do understand that if I save the original somewhere else, I can replace  it, with no harm  done.

However, what constitutes "renaming?"  If I change it to /.config/libreofficeA, would that suffice?

Thanks,

JimW

---

### Post by jimw on 2013-11-18
I just renamed the file, putting an "A" at the end of it, and all seems to work, save that it lost the  page numbering, which I was able to fix easily.

Thanks for the suggestion.

JimW

---

