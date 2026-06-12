---
title: "Ctrl + V will not work if I close the application I copied text from"
date: 2013-02-12
forum: General Help
---

### Post by Red Planet on 2013-02-12
Hello.

I always have to keep an application open I copied text from to paste the text somewhere. In fact the copied text will be saved to Klipper (if Klipper is on) after it has been copied. But why cannot a simple shortcut Ctrl + V be used to paste the copied text?

OS: Ubuntu 10.04.4 LTS
KDE version: 4.4.5

---

### Post by rnerwein on 2013-02-12
> **Red Planet said:**
> Hello.

I always have to keep an application open I copied text from to paste the text somewhere. In fact the copied text will be saved to Klipper (if Klipper is on) after it has been copied. But why cannot a simple shortcut Ctrl + V be used to paste the copied text?

OS: Ubuntu 10.04.4 LTS
KDE version: 4.4.5
hi
because you copied it to the stack of the running process. and if the process is gone - his stack too.
cheers

---

### Post by Vaphell on 2013-02-12
i use a clipboard manager (parcellite in 10.04) and it works just fine, text is available even after program it was copied from gets closed.

if you want to check what's in the buffers, install xsel
```
$ xsel --help
...
Output options
  -o, --output          Write the selection to standard output

...

Selection options
  -p, --primary         Operate on the PRIMARY selection (default)
  -s, --secondary       Operate on the SECONDARY selection
  -b, --clipboard       Operate on the CLIPBOARD selection
```

...
```
xsel -po
xsel -so
xsel -bo
```

primary is used with highlight-copy/middleclick-paste, clipboard with ctrl+c/ctrl+v

---

