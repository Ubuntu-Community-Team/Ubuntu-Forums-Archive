---
title: "meanings of the bash colors"
date: 2005-06-22
forum: General Help
---

### Post by billiejoex on 2005-06-22
I noticed that the ls command generates outputs of different colors, depending on the file type located in thedirectory(for example executable files are listed in green). 
Where do I can find the complete list of the color's meanings?

---

### Post by musicman2059 on 2005-06-22
[QUOTE=billiejoex]I noticed that the ls command generates outputs of different colors, depending on the file type located in thedirectory(for example executable files are listed in green). 
Where do I can find the complete list of the color's meanings?[/QUOTE]
 A green name is something that is executable (has the executable permissions set on it), and a blue name is a directory.  As for pink, I have no idea.

---

### Post by Zeddicus on 2005-06-23
Methinks you'll find:

```

dircolors --print-database
```

Rather enlightening. :)

---

### Post by billiejoex on 2005-06-23
Thank you man.

---

