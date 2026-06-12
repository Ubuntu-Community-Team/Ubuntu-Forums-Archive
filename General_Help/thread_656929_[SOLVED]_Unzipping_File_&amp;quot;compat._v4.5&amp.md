---
title: "[SOLVED] Unzipping File: &amp;quot;compat. v4.5&amp;quot; error"
date: 2008-01-03
forum: General Help
---

### Post by PartisanEntity on 2008-01-03
I have a zip file I am trying to unzip, but when I do so I get the following error:

>    skipping: data.filext             need PK compat. v4.5 (can do v2.1)
   skipping: data2.filext  need PK compat. v4.5 (can do v2.1)

Could it have something to do with the file size? Both files seem to be 4GB in size even though the zip file itself is only 377MB.

---

### Post by heimo on 2008-01-03
try running
```
file packagename.zip

```
where packagename.zip is obviously filename for the compressed file.

---

### Post by PartisanEntity on 2008-01-03
Doing that gave me the following output:

> filename.zip: data

---

### Post by heimo on 2008-01-03
> **PartisanEntity said:**
> Doing that gave me the following output:

Oh... :-( That wasn't so helpful after all. I was hoping something like:
```
filename: 7-zip archive data, version 0.2
```
or
```
filename: Zip archive data, at least v2.0 to extract
```

You could read couple first bytes of the file to see if there's "PK" or "7Z" to see if it's regular zip or 7z file. File command should have recognized the type of that file, I think.
```

dd if=filename.zip count=2 bs=1
```

---

### Post by jeffus_il on 2008-01-03
It is the 4GB limit.
See this:
[http://kbase.redhat.com/faq/FAQ_80_10118.shtm](http://kbase.redhat.com/faq/FAQ_80_10118.shtm)

---

### Post by PartisanEntity on 2008-01-03
Here is the output of dd if=filename.zip count=2 bs=1:

> PK2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.000213726 seconds, 9.4 kB/s

---

### Post by heimo on 2008-01-03
> **jeffus_il said:**
> It is the 4GB limit.
See this:
[http://kbase.redhat.com/faq/FAQ_80_10118.shtm](http://kbase.redhat.com/faq/FAQ_80_10118.shtm)

Excellent! So, enabling universe (if not already) and running
```
sudo aptitude install p7zip-full
7za e filename.zip
```Should do it. :)

EDIT: p7zip -> p7zip-full

---

### Post by PartisanEntity on 2008-01-03
Thanks, p7zip did the trick!

---

