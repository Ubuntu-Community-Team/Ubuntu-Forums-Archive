---
title: "emacs line wrapping"
date: 2019-10-05
forum: General Help
---

### Post by Skaperen on 2019-10-05
i have a file with some lines that are N columns wide.  i wanted to be sure no new lines got any longer, so i opened a terminal N columns wide and started [COLOR=#006400][FONT=courier new]**emacs**[/FONT][/COLOR] with that file.  there are enough columns to display the file without wrapping lines, but [COLOR=#006400][FONT=courier new]**emacs**[/FONT][/COLOR] still wraps them and puts a \ at the end of the line it displays and the last character is on the next line by itself.  is there a way to disable line wrapping when the line is exactly fitting the terminal display?

note, i unset the DISPLAY environment variable to have [COLOR=#006400][FONT=courier new]**emacs**[/FONT][/COLOR] display in the terminal instead of opening its own window in X.

---

