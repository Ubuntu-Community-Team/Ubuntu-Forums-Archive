---
title: "firefox: find text fails on local PDF"
date: 2020-02-25
forum: General Help
---

### Post by Skaperen on 2020-02-25
i am running firefox 2 different ways:

1.  a .desktop icon runs /usr/lib/firefox/firefox with no arguments which has been configured to load [COLOR=#a52a2a][FONT=courier new]**file:///home/phil/mylinks.html**[/FONT][/COLOR] which has a link to [COLOR=#a52a2a][FONT=courier new]**file:///home/share/python-docs-pdf-letter/python-3.7.4-docs-pdf-letter/library.pdf**[/FONT][/COLOR] which i click on.

2.  a different .desktop icon runs the same image with arguments [COLOR=#0000cd][FONT=courier new]**-p profilename file:///home/share/python-docs-pdf-letter/python-3.7.4-docs-pdf-letter/library.pdf**[/FONT][/COLOR] where that profile was just created and this is its first usage (each time i test it).

i wanted to change to method 2 so i can go directly to that document.

both ways always run the same image under the same username (phil) and finally access the same PDF file.  the browser has a large window that is almost full screen, the same exact size in both cases.

i press Cntl+F for find and get the find field at the bottom.  in the first case i enter "os.lchown" and it finds the function description.  it also found earlier places as i typed the letters.  for example when i typed "o" it found the "o" in "Python" in the title.  in the second case, when i typed "o" the input field changed to red and it gave the message "Phrase not found".  it could not find the "o" that i can see right there.

what is it doing different in these two different ways?  how can it not find the letter "o" anywhere in the document?

---

