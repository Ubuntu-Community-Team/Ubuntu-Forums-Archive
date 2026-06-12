---
title: "Cant Unzip"
date: 2013-03-17
forum: General Help
---

### Post by fabiomassudo on 2013-03-17
HI,

This happens to me when i try to unzip. I tried ark and xarchiver. The file is .zip

---

### Post by ibjsb4 on 2013-03-17
That file looks to be a ".jpg" and not a zip file.  Should be able to go back to the original download and just double click on it.

And welcome to the forums  :)

---

### Post by fabiomassudo on 2013-03-17
> **ibjsb4 said:**
> That file looks to be a ".jpg" and not a zip file.  Should be able to go back to the original download and just double click on it.

And welcome to the forums  :)

Its the file im trying to unzip

---

### Post by steeldriver on 2013-03-17
it looks like it might be a problem with the filename encoding (ISO-8859-1 versus UTF-8??)

---

### Post by fabiomassudo on 2013-03-17
> **steeldriver said:**
> it looks like it might be a problem with the filename encoding (ISO-8859-1 versus UTF-8??)

I just tried another file with a standart filename and it worked. How can i solve that problem?

---

### Post by steeldriver on 2013-03-17
if it manages to extract the files (just can't display them) then you may be able to use convmv to correct the names - do you know where the archive came from (Windows?) and/or what locale?

---

### Post by fabiomassudo on 2013-03-17
It came from windows

---

### Post by fabiomassudo on 2013-03-17
Hi,

Cant unzip files with a special filename encoding,

Ty,

---

### Post by schragge on 2013-03-17
[COLOR=#000000]The command line *unzip* provides an option to disable handling of Unicode in file names.
```
unzip -U zipfile
```[/COLOR]

---

### Post by fabiomassudo on 2013-03-17
> **schragge said:**
> [COLOR=#000000]The command line *unzip* provides an option to disable handling of Unicode in file names.
```
unzip -U zipfile
```[/COLOR]

Is there any way so i can avoid going to the command line all the time?

---

### Post by overdrank on 2013-03-17
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---

### Post by fabiomassudo on 2013-03-19
Anyone?

---

### Post by fabiomassudo on 2013-03-21
Bump

---

