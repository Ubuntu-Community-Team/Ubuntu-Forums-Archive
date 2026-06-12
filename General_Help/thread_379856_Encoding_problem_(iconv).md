---
title: "Encoding problem (iconv)"
date: 2007-03-08
forum: General Help
---

### Post by lhabjane on 2007-03-08
I've copied some files from my windows system, but when I open some files, I get weird characters instead of Croatian characters. Can I somehow convert these files to UTF-8 or something? If I ```
iconv -t UTF-8
```  my characters get ignored. Where's the problem? Can I at least replace them manually with **sed** ?

Thanks in advance

---

### Post by zvacet on 2007-03-09
Try this 
```
sudo apt-get install msttcorefonts 
```

---

### Post by lhabjane on 2007-03-09
Already done that.. Forgot to mention, if I change these files with Text editor, I can type in Croatian letters, and when I press save it says: "Must be saved as UTF-8", and after that letters are ok.  But I have 10mb of these files, I can't change them manually..

---

### Post by zvacet on 2007-03-09
system>help>system documentation
In search field type Desktop user guide
I hope you will find all you need there.If not ask again.Maybe somebody more expirienced than me will know the answer.

---

### Post by lhabjane on 2007-03-10
Nothing new in that guide. The problem still remains. :(

---

### Post by zvacet on 2007-03-10
This is what I did.Press upper left icon(hd1) and go into the Windows.There I found some strange document in plain text.Just copy-paste and now is in my Ubuntu Desktop.

---

### Post by lhabjane on 2007-03-10
> **zvacet said:**
> This is what I did.Press upper left icon(hd1) and go into the Windows.There I found some strange document in plain text.Just copy-paste and now is in my Ubuntu Desktop.

Yeah, good for you. You haven't read my previous posts?

---

### Post by zvacet on 2007-03-11
> 1.Choose Tools - Options. Go to Language Settings - Languages.
2.Under Default languages for documents, select the document language for all newly created documents. If you mark For the current document only, your choice will only apply to the current document. Close the dialog with OK.
I know it is trivial question,but did you install additional laungage support?

---

### Post by lhabjane on 2007-03-11
I installed support for Croatian. But, the problem is, that I have an application that loads that file (not just text editor) and the problem is the same: no croatian letters! Obviously the problem isn't in fonts (as my application is written to support croatian).

---

### Post by zvacet on 2007-03-11
I quoted Open Office help,and didn´t help you.I´m runing out of options.Only thing crossing my mind is to look at [http://www.ubuntu-hr.org/]("http://www.ubuntu-hr.org/")
I belive they can handle it.I tryed my best,but it seems is not good enough.Sorry.

---

### Post by lhabjane on 2007-03-11
Thnx anyway! I've made my own utility in java that converts between encodings

---

