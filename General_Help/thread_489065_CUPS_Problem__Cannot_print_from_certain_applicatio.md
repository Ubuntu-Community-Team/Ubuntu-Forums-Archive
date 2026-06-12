---
title: "CUPS Problem?  Cannot print from certain applications"
date: 2007-06-30
forum: General Help
---

### Post by brn on 2007-06-30
I have a Canon PIXMA MP160 using the MP160 v 2.70 driver from openprinting.org, with Dapper.  It can print text files directly from gEdit as well as images from EOG and gThumb.  For any other application; browser, email client, even *lpr filename*, the job reaches the queue but then sits there, never reaching the printer.  The printer is ready and if I send another file from gEdit or one of the image viewers, it prints successfully.  But the stalled jobs remain stuck in the queue.  Can anyone suggest what  might cause this selective inability to print from certain applications but not others?  

Thanks

---

### Post by malenki on 2007-07-01
Hello,

I have the same issu but with HP 1210 printer since an update.

Yesterday it worked fine, and after I launched an update (update-manager)

Today : I want print something (simple PDF file), and... "job-stopped" ! But the printer is ready !

What is this ?

---

### Post by malenki on 2007-07-01
Hum...

Very strange : with gedit and another PDF file, I can print, but with the PDF made with OOo, I can't print it... Bug of OOo ?

---

### Post by malenki on 2007-07-01
To fix this issu with OOo, I don't export to PDF, but I print into a postscript file.

Then, I use ps2pdf14 to get proper PDF file from the PS file.

```
$ ps2pdf14 my_file.ps
```

and you get my_file.pdf, which can be print in regular way.

---

