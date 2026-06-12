---
title: "LibreOffice Writer spellcheck glitch"
date: 2017-02-06
forum: General Help
---

### Post by apol1 on 2017-02-06
Im not really sure where to post this thread but here goes :)

So I was doing some writing and out of nowhere on page 8 spell check (as I type) no longer works. Anywhere before page 8 it works fine fine.

Ive looked at threads talking about how to turn spell check on and off but this is just weird.

What should I do? Im very new to this OS 

Thx in Advance

---

### Post by vasa1 on 2017-02-06
Exit the LibreOffice suite completely. Run```
pgrep soffice
```to confirm. Nothing should appear in response. Now rename *~/.config/libreoffice* to, say, *~/.config/libreoffice.old* and open your LibreOffice Writer document. Let us know if spellcheck is back to normal.

---

### Post by apol1 on 2017-02-15
I entered your code and got a number. Where are these things I need to change? Is it a file or a terminal command?

---

