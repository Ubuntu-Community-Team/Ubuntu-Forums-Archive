---
title: "Save/print search result to text file?"
date: 2013-02-22
forum: General Help
---

### Post by MrsUser on 2013-02-22
How can I save a search result to a txt file? When I search in Nautilus, let's say for '.avi', I get a list with results. Can I save this list in a text file somehow?

---

### Post by LewisTM on 2013-02-22
Simply select all files, copy them to the clipboard and paste the results in your favorite text editor.

Cheers!

---

### Post by MrsUser on 2013-02-22
Didn't know about this. Wow, that's simple! However, it also saves the file paths. I'd like to get a list with only the file names.

---

### Post by LewisTM on 2013-02-22
You can strip the paths with this command, once the files have been copied to the clipboard
```
xclip -o -selection clipboard | sed 's/.*\///' | xclip -selection clipboard
```
Then paste in the text editor.

You could write the filtered output directly to a file
```
xclip -o -selection clipboard | sed 's/.*\///' > outputfile.txt
```

---

### Post by MrsUser on 2013-02-22
Works like a charm. Thanks a lot! ):P

---

