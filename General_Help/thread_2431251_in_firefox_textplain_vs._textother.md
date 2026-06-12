---
title: "in firefox: text/plain vs. text/other"
date: 2019-11-13
forum: General Help
---

### Post by Skaperen on 2019-11-13
in firefox, when i access a "page" with a MIME type of "text/plain" it displays it.  if that MIME type is something like "text/python" it only lets me download it and does not display it whether i download or not.  are these behaviours things that i can change?  how can i set firefox to always display any "text" type while still programmatically handling stuff like "text/html" and "text/javascript" like it should?

---

### Post by SeijiSensei on 2019-11-14
What do you have as the handler for "plain text" files in Edit > Preferences > General > Applications?  If you choose "always ask," does that help? The next time you open a file with MIME-type "text/python" you should get a dialog box asking you to choose how you want such files to be handled.

---

### Post by Skaperen on 2019-11-14
for both text plain and text python nothing shows up under Preferences > General > Applications.  when i get the dialog box for text python, displaying or viewing it is not an option. i get 2 choices, "Open with" (menu) and "Save file".  that menu has 2 choices, "Mousepad (default)" and "Other".  "Mousepad" brings up an external application in its own window, which i do not want.  "Other" informs me that there are no applications found for text/python.  what i want is for firefox to display the contents exactly like it does for text/plain.  for text/plain there is no prompt.  it just shows the file under a tab right in the browser.

here is an example in text/plain:  [http://ipal.net/python/align_columns.py](http://ipal.net/python/align_columns.py)

here is an example in text/python:  [http://ipal.net/python/pidsinlinux.py](http://ipal.net/python/pidsinlinux.py)

---

