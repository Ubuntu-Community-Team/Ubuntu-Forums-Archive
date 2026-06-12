---
title: "LibreWriter Remove Manual Page Breaks"
date: 2015-04-30
forum: General Help
---

### Post by webmanoffesto on 2015-04-30
I'm using LibreOffice Writer. Example: Page 5 has text, a manual page break, and an empty 1/4 page. Page 6 has then 10 lines of text, only. I can't figure out how to move the 10 lines on page 6 to page 5 all in one shot. (The pages have bulleted lists, each line has a manual "carriage return".)

If I put my cursor at the end of the text on page 5 and press the Delete key, only one line comes up to page 5. 
If I put my cursor before the text on page 6 and press Back Space, again, only one line comes up to page 5.

How do I fix this problem?

---

### Post by amanchesterman on 2015-05-01
First, just to be clear: you are following the instructions here
[https://help.libreoffice.org/Writer/Inserting_and_Deleting_Page_Breaks](https://help.libreoffice.org/Writer/Inserting_and_Deleting_Page_Breaks) 
and you only get one line of the bulleted list moving to page 5, is that correct?

If so, then I guess that you are deleting the manual page break successfully, but there is something else preventing the list on page 6 from moving to page 5 as an entire block.

The reason may well be the 'carriage return' at the end of each line. In effect, that makes each line in the list behave like an independent paragraph. If I were you, I would highlight one of those lines and look at Format > Paragraph > Text Flow. In particular, look at the 'keep with next paragraph' and the widow and orphan control check boxes.
Another thing that may help is to toggle 'non-printing characters' on your toolbar (or press Ctrl + F10). This shows/hides all the carriage returns, blank spaces etc. and may enable you to find hidden text that is interfering with what you want to do.

---

### Post by webmanoffesto on 2015-05-01
> **amanchesterman said:**
> I would highlight one of those lines and look at Format > Paragraph > Text Flow. In particular, look at the 'keep with next paragraph' and the widow and orphan control check boxes.

I selected all the lines on page six, unchecked all those boxes, and that solved the problem. Thank you.

---

