---
title: "Command to join files"
date: 2007-04-09
forum: General Help
---

### Post by chick3n on 2007-04-09
I used to remember the command i would use on dos to join multiple files together.
ex. name.001 + name.002 + name.003

Is there one i can use within linux to do that?

---

### Post by chick3n on 2007-04-09
i appolagize i found the answer on google in like 2 secs. I shoulda checked there first. my bad.

---

### Post by jfinkels on 2007-04-09
you can insert the contents of one file into another using the shift operator ">>" like this, assuming test1 and test2 are text files. "cat" prints the contents of a file to standard output, and the >> operator shifts that output into the end of the second file.

```

cat test1 >> test2

```

---

