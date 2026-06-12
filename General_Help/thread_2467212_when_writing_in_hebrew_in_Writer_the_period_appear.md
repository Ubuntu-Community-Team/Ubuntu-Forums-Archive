---
title: "when writing in hebrew in Writer the period appears on the other side"
date: 2021-09-19
forum: General Help
---

### Post by ronjjjg8885 on 2021-09-19
how to fix this??


TNNX

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289180&stc=1[/IMG]{on windows and ubuntu too}

---

### Post by rbmorse on 2021-09-19
Does it work correctly if you set the paragraph formatting to right justified?

---

### Post by Impavidus on 2021-09-19
I've never tried writing anything right-to-left, so I'm speculating a bit here.

LibreOffice supports bidirectional text. So you can write some English text (left to right), then some Hebrew text (right to left, inserted right of the English text), then some more English text (left to right, inserted right of the Hebrew text). Of course, this involves some guesswork, as, if the main language of the document had been Hebrew, the Hebrew text had to be inserted left of the first English text the last English text left of the Hebrew text. What appears to go wrong here is that LibreOffice thinks the dot is part of left to right text and left to right is the main direction of the document, so it puts it to the right of the Hebrew text.

I notice it says at the bottom of the screen {en-US}. Does LibreOffice think the main language of the document is English? Try setting it to Hebrew.

---

### Post by HermanAB on 2021-09-20
Maybe, you need to use a Hebrew period, not  the normal period?

---

