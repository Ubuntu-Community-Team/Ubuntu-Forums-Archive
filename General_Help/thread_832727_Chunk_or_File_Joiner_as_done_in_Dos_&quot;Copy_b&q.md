---
title: "Chunk or File Joiner as done in Dos &quot;Copy /b&quot;"
date: 2008-06-18
forum: General Help
---

### Post by Bojangles00 on 2008-06-18
I have looked at a lot of things to help join files such as the good ol' dos command--

```
Copy /b "file.iso" + "file2.iso" "final.iso"
```

So far I have heard of something called 'Chunk' that can do this but searched everywhere and couldn't find it.  I tried gfslicer but some of the libs are unsupported and/or didn't work.

If anyone could direct me to the download of Chunk or something like it, I would be very grateful.  (Or even something that can run .bat(s))

Thanks.

---

### Post by sdennie on 2008-06-18
I think you can just use cat for this:

```

cat file1 file2 file3 file4 > output

```

---

### Post by iaculallad on 2008-06-18
Using find, cat, with xarg together could produce your "batch file":

```
find . -name filename*.file_ext | sort | xargs -s '{}' cat '{}' >> outfile.ext
```

---

