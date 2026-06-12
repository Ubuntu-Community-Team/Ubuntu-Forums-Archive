---
title: "External USB VIDEO HDD, no alphabetic sorting..."
date: 2007-01-10
forum: General Help
---

### Post by daller on 2007-01-10
Hi There,

I recently bought an Argosy HV355U 300GB Mobile Video HDD.

I can transfer all my movies to it, but I have a problem!

With 300+ folders, I would like them sorted alphabetically- currently they are sorted by date (changing the name of a folder sends it to the bottom of the list.) - New folder are also in the bottom...

Can I somehow sort them? (maybe hack the date on them, to make them sort alphabetic.) - I'm NOT doing it manually on each folder :D

Thank you!

**EDIT: This is an issue with the TV-part of the device! - Not my computer sorting them incorrectly!**

---

### Post by dcstar on 2007-01-10
> **daller said:**
> Hi There,

I recently bought an Argosy HV355U 300GB Mobile Video HDD.

I can transfer all my movies to it, but I have a problem!

With 300+ folders, I would like them sorted alphabetically- currently they are sorted by date (changing the name of a folder sends it to the bottom of the list.) - New folder are also in the bottom...

Can I somehow sort them? (maybe hack the date on them, to make them sort alphabetic.) - I'm NOT doing it manually on each folder :D

Thank you!

**EDIT: This is an issue with the TV-part of the device! - Not my computer sorting them incorrectly!**

If you want to copy them in a specific order, do something like:
```
ls > file.txt
```
to capture the contents of the directory in question, then
```
sort file.txt > sorted.txt
```
so then you will have a sorted list of files ("man sort" for the various options)

Then edit the file and use cut-and-paste to add in the commands to copy each file, Then make this file executable and run it.

It should copy each file (one at a time) in the order you did the sort in.

---

### Post by daller on 2007-01-11
> **dcstar said:**
> If you want to copy them in a specific order, do something like:
```
ls > file.txt
```
to capture the contents of the directory in question, then
```
sort file.txt > sorted.txt
```
so then you will have a sorted list of files ("man sort" for the various options)

Then edit the file and use cut-and-paste to add in the commands to copy each file, Then make this file executable and run it.

It should copy each file (one at a time) in the order you did the sort in.

Copy? (EDIT: They are on the HDD already - Not on my computer!) - It's 300GB - I'd rather not do that! - Can't I just change the timestamp?

Thank you!

---

