---
title: "unable to print specific PDF documents from Adobe Acrobat Reader 7.0"
date: 2013-03-27
forum: General Help
---

### Post by prasadvj on 2013-03-27
We have implemented Thin Clients under the Ubuntu 9.10 server. Under this environment we are unable to print specific PDF documents (that are generated thru our ERP) from Adobe Acrobat Reader 7.0 in Ubuntu 9.10. The same PDF documents are printed in Acrobar 8.x and above version, but takes lot of time for processing the prints.

If anybody has the similar situation and have find out the solution for the same, please let us know.

Thanks in anticipation.

Prasad.

---

### Post by mörgæs on 2013-03-27
9.10 has been out of support for two years now. I would begin with a fresh install of 12.04 LTS.

---

### Post by HermanAB on 2013-03-27
Yup, this is an old Adobe problem that was fixed years ago.  So, obviously the solution is to upgrade your system, or at the very least, upgrade Adobe.

---

### Post by prasadvj on 2013-04-05
Thanks, for the reply and suggestions. The problem is I cannot upgrade the Ubuntu to the next version as the Thin Clients in my environment are not compatible with the next version of Ubuntu. So I have to live with 9.10.

I had installed Adobe Reader 8.0 and also 9.1 both works fine but it takes lot of time to print the documents. That is the reason why I have degraded the Adobe Version. 

I have tried different PDF viewer like evince, Foxit etc but none of them work as expected. 

It would be a great help if anybody has a solution for the same.

Thanks in anticipation.
Prasad

---

### Post by ibjsb4 on 2013-04-05
One more to try is "epdfviewer", its a lightweight thats been around a long time and in the repositories either under that name or just "epdfview".

[http://www.addictivetips.com/ubuntu-linux-tips/epdfviewer-lightweight-pdf-viewer-for-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/epdfviewer-lightweight-pdf-viewer-for-ubuntu-linux/)

---

### Post by mörgæs on 2013-04-05
> **prasadvj said:**
> ... as the Thin Clients in my environment are not compatible with the next version of Ubuntu. 

Do you have a hardware description, please?

---

### Post by coldraven on 2013-04-05
If it is a network printer could you use FPDF to print directly from the server?
That would be beyond me but someone might know how.
[http://www.fpdf.org/](http://www.fpdf.org/)

---

### Post by HermanAB on 2013-04-05
Note that most PDF readers use the same ghostscript code underneath and will therefore have the same bugs.  However, Xpdf (and of course Adobe) are different.

---

