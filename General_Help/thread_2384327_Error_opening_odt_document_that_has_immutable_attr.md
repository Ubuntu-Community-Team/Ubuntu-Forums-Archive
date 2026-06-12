---
title: "Error opening odt document that has immutable attribute set"
date: 2018-02-05
forum: General Help
---

### Post by raleigh3 on 2018-02-05
I set the immutable attribute on an .odt document.
  
When I try to open it with LibreOffice, it says "General input/output error while accessing."

  
I don't get that message when opening a text file with the immutable attribute.

  
Is there a way to stop that error?

---

### Post by ajgreeny on 2018-02-06
I have just tried that myself but having to use abiword to open the immutable .odt file as I do not use LO on this very limited and old netbook.  The file opened without a problem in abiword.

If you remove the immutable attribute can you then open the file or is it corrupt in some other way?

---

### Post by vasa1 on 2018-02-06
If I set the immutable attribute for a .odt file, I see what OP sees using LibreOffice Version: 5.4.4.2. Reversing the attribute allows the file to be opened.

A text file opens either way.

---

### Post by ajgreeny on 2018-02-06
The .odt file I first made immutable then opened in abiword was an old one (about 4 or 5 years) so I wonder if that was the reason for my ability to open the file, or if it was that I used abiword, not LO to open it?

---

### Post by vasa1 on 2018-02-06
I just tested with a new file created with LibreOffice Version: 5.1.6.2 (the default with Xubuntu 16.04.3). Same thing. I'll install abiword and give it a try.

Abiword 3.0.1 opens the file without issue. So it seems to be something about LibreOffice. OP could check if it's a feature or a bug.

---

### Post by ajgreeny on 2018-02-06
Interesting!

Perhaps a good reason to use abiword occasionally.

---

### Post by raleigh3 on 2018-02-06
I found that I could use the read only attribute instead of the immutable attribute.

I was wanting to keep from accidentally overwriting a template.

---

### Post by vasa1 on 2018-02-06
> **raleigh3 said:**
> I found that I could use the read only attribute instead of the immutable attribute.

I was wanting to keep from accidentally overwriting a template.That's what I use. I don't use the immutable attribute.

---

