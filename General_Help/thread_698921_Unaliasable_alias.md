---
title: "Unaliasable alias"
date: 2008-02-16
forum: General Help
---

### Post by hoydooley on 2008-02-16
Can I make a system-wide alias that can not be unaliased by users???

I need it because I want to restrict users to run a specific program without certain options.

---

### Post by Sudz on 2008-02-16
I don't think you can prevent people from setting their own shell aliases to whatever they want.  There isn't tiered access control over shell operation, you need to do that with files...

What you can do is replace the program that you want to control with a script to add or remove the options you are concerned about.

---

### Post by fatmano on 2008-02-16
sounds more like a sudo file entry rather than a global alias

---

