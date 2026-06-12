---
title: "copying from terminal and then pasting into vim"
date: 2013-05-14
forum: General Help
---

### Post by gibxam on 2013-05-14
Hello Friends,

I have run into some weird behavior while copying from the terminal (either by using "right-click copy" or "ctrl-shift-c") and then pasting into vim (also either by using "right-click paste" or "ctrl-shift-p"). Sometimes the text that I paste will overwrite some of the existing text, and almost always the beginning part of the copied text is lost when I paste it. 

What I am really trying to do is copy text from the terminal and paste it, in its entirety into vim without losing any of the copied text and without overwriting any of the already existing text. Your insights into this are valued, thank you.

---

### Post by Impavidus on 2013-05-15
Make sure you are in insert mode before pasting. Else the first part of the string is interpreted as a series of commands that may delete part of the text already present.

---

### Post by gibxam on 2013-05-15
Thank you so very much.

---

