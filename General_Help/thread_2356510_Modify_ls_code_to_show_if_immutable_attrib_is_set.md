---
title: "Modify ls code to show if immutable attrib is set"
date: 2017-03-23
forum: General Help
---

### Post by raleigh3 on 2017-03-23
I need the info that this produces plus whether the immutable attrib is set.
  ```
[INDENT]ls -lAxot --time-style=+%m-%d-%Y



[/INDENT]
```

---

### Post by vasa1 on 2017-03-23
> **raleigh3 said:**
> I need the info that this produces plus whether the immutable attrib is set.
  ```
[INDENT]ls -lAxot --time-style=+%m-%d-%Y'



[/INDENT]
```
Does that work for you? How?

---

### Post by raleigh3 on 2017-03-24
Sorry, remove the single quote at the end.

---

### Post by Keith_Helms on 2017-03-25
Use the lsattr command to show whether immutable is set.

---

### Post by raleigh3 on 2017-03-25
I wanted just one command to show ALL file attributes and files.

---

### Post by vasa1 on 2017-03-25
> **raleigh3 said:**
> I wanted just one command to show ALL file attributes and files.
If it doesn't exist, someone will have to code a form of *ls* that offers attribute information as well.

Otherwise, it may be possible to construct a one-liner that uses a sequence of lsattr, grep, awk, xargs and ls to get what you want.

Edit: Does```
lsattr -R | grep -E "^----i" | awk ' { print $2 } ' | xargs ls -lAxot --time-style=+%m-%d-%Y
```work for you? While the immutable attribute isn't expressly mentioned in the final output, the output is only for files with the immutable attribute because of the grep regex.

---

### Post by raleigh3 on 2017-03-28
Thanks, it works.

---

