---
title: "[SOLVED] non-english encoding problem"
date: 2007-12-17
forum: General Help
---

### Post by maysam on 2007-12-17
hi,
I don't know is it a right category to ask this question or not, anyway, some Arabic/Persian text are not intelligible in  Firefox and some are! How can I fix this problem?
see the attachments.

---

### Post by maysam on 2007-12-19
I found the solution:
Go to  /usr/share/fonts/truetype/
Create a folder and rename it to ttf-persian-fonts
Copy Arial, Times, Tahoma (and all other popular fonts) to this folder, you can find theme in Windows\Fonts folder, if you have Windows installed.
Then type sudo fc-cache -f -r -s
On next restart all is ok!

---

