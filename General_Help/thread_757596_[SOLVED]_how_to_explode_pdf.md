---
title: "[SOLVED] how to explode pdf"
date: 2008-04-17
forum: General Help
---

### Post by behrooz.s on 2008-04-17
hi,

I searched the web to find a application to explode pdf, but I couldn't find. does anyone know how to do this?

---

### Post by marufaberlin on 2008-04-17
What do you mean by "exploding pdf"?

---

### Post by behrooz.s on 2008-04-17
for example I have a pdf that contains 700 pages, I want to explode it to 7 pdfs that each one contains 100 pages.

---

### Post by bingoUV on 2008-04-17
The following will give you one of the shrapnels of your explosion. Do similarly for 101 to 200, 201 to 300 and so on.
```

acroread -toPostScript -start 1 -end 100 <pdf_file.pdf> <ps_file1.ps>
ps2pdf <ps_file1.ps>

```

---

