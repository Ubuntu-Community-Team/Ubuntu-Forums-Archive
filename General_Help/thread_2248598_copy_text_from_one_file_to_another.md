---
title: "copy text from one file to another?"
date: 2014-10-15
forum: General Help
---

### Post by sohlinux on 2014-10-15
Hello, how can I copy all text from file1.txt to file2.txt

example

file1.txt has the following text
abc

file2.txt will then have the following text
abc

later on file1.txt has the following text
def

so after its copied the second time file2.txt will have the following text
abc
def

file1.txt has new text quite often so each time I run the command it must add the text from file1.txt to file2.txt on a new line

thanks

---

### Post by radwanski-michal-a on 2014-10-15
It's very simple. In the shell (it's probably bash), execute following code:
cat file1.txt >> file2.txt

regards

---

### Post by VCoolio on 2014-10-15
cat file1.txt >> file2.txt

---

### Post by ajgreeny on 2014-10-15
Do they really need to be separate files or would a soft link help with what you want (or need)?

---

### Post by sohlinux on 2014-10-15
that works, thanks :)

---

