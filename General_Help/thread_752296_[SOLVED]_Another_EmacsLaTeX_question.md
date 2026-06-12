---
title: "[SOLVED] Another Emacs/LaTeX question"
date: 2008-04-11
forum: General Help
---

### Post by dstein on 2008-04-11
So I am using emacs to edit a LaTeX file. I would like some sort of word-wrap function so that my LaTeX input is easy to read. I figured that auto-fill-mode would be  a good idea. Is there any better way to do this? Also, what about the lines that I typed not using auto-fill-mode. Is there any way to apply word-wrap to them automatically, without entering line-breaks manually? Lastly, what is the default length of a line using auto-fill-mode? Is there any way to adjust this? Thanks!

---

### Post by andrewc6l on 2008-04-11
Auto-fill is a good mode to use. For text that you want to format, set a mark at the beginning, go to the end, and fill the region.

Since I can never remember the key bindings, I always:

1. go to top of the paragraph
2. ESC-x set-mark-command
3. go to bottom of the paragraph
4. ESC-x fill-region

You can also use ESC q in a paragraph to fill the paragraph.

---

### Post by dstein on 2008-04-11
Oh perfect. Thanks. Is there any way to adjust the number of characters per line?

---

### Post by gaussian on 2008-04-12
> **dstein said:**
> Oh perfect. Thanks. Is there any way to adjust the number of characters per line?

Try this:
Control-u 80 ESC-x set-fill-column

---

