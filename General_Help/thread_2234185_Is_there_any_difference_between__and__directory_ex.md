---
title: "Is there any difference between ** and * directory expansion?"
date: 2014-07-13
forum: General Help
---

### Post by CkDGTAT on 2014-07-13
What is the matter of using ** instead of * in

for i in **; do sth;done

Thank you

---

### Post by ian-weisser on 2014-07-13
In which language?

---

### Post by varunendra on 2014-07-13
No difference as far as I know and have experienced.

It could be *.*, which will limit the expansion to only those items that have a dot (.) in the file names (e.g., file.pdf or "fileversion 1.4 extended")

**PS:** I am assuming the question to be about bash. Not sure if there may be a difference in some other language.

---

