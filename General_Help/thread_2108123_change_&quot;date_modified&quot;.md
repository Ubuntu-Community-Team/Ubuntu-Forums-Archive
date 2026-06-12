---
title: "change &quot;date modified&quot;"
date: 2013-01-23
forum: General Help
---

### Post by rybnik on 2013-01-23
Is there a way to artificially change the "date modified" information in a file?  (without actually modifying the file)  I just want to specify a date and have that stored in the "date modified" section.  I have both nautilus and dolphin installed.

---

### Post by sudodus on 2013-01-23
> **rybnik said:**
> Is there a way to artificially change the "date modified" information in a file?  (without actually modifying the file)  I just want to specify a date and have that stored in the "date modified" section.  I have both nautilus and dolphin installed.
Use the terminal command ***touch***.

```
touch filename
``` gives it the current time
```
touch -r ref-file filename
``` gives filename the same time stamp as ref-file.
```
touch --date=STRING
``` gives it the date in STRING according to ```
info touch
```

---

### Post by ajgreeny on 2013-01-23
```
touch -d "Wed 23 Jan 2013 23:20:55" filename
```will do it.

I found the date string most diffecult to understand until I found you can use whatever string is showing in your file manager, ie in my nautilus **Wed 23 Jan 2013 23:20:55**

---

### Post by Dave_L on 2013-01-23
This date/time format will also work, and I find it more convenient:

```
touch --date='2013-01-23 23:20:55' filename
```

---

### Post by rybnik on 2013-01-28
Perfect.

Thanks!

---

