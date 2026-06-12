---
title: "Search in all files in folder"
date: 2008-02-20
forum: General Help
---

### Post by daller on 2008-02-20
I'm trying to find different functions in a complex php-code.

It's split over several files, and I would therefore love to be able to search in all files with one command / GUI tool, and find what file(s) include the searchstring.

Is there such a tool?

---

### Post by erginemr on 2008-02-20
Then **grep **is the way to go. From a terminal, you should change (cd) into the folder where your php scripts are located, and use "grep your_code_snippet" or "grep -i your_code_snippet" for a case-insensitive search, to find the corresponding files. 

**"man grep" **will give you more information on how to use it.

---

### Post by anaconda on 2008-02-20
grep your_code_snippet *

would do that. if the filename doesnt start with a "."

grep your_code_snippet .*
if filename starts with a "."

---

