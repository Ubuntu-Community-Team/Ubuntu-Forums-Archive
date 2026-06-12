---
title: "Printing a landscape page from KPDF"
date: 2006-10-18
forum: General Help
---

### Post by Jochus on 2006-10-18
When I'm printing a page that is in landscape from KPDF through CUPS to my HP Deskjet 690C, the printer only prints 3/5 of the page. The rest stays blank. What could the problem be?

---

### Post by elbuntu on 2006-11-09
I have exactly the same problem, but then with an epson printer ! Did you find a solution by now ?

---

### Post by ferd on 2006-11-09
Same here, on a HP 8250. I'm guessing the printer in not the problem. I'm using Dapper.

---

### Post by feest on 2006-11-09
well this is a nice thing to try here so i did. the paper gets stuck in the printer and i have to remove it manually...

 :-k :-k :-k  not good.

---

### Post by stani on 2006-11-10
This is unfortunately a confirmed bug:
[https://launchpad.net/distros/ubuntu/+source/kdegraphics/+bug/47649](https://launchpad.net/distros/ubuntu/+source/kdegraphics/+bug/47649)

As a temporary solution you can print with xpdf, which you can install with this command:

```
sudo apt-get install xpdf
```

---

### Post by elbuntu on 2006-11-13
That would work, except that in xpdf one can not change the print properties such as paper, print quality etc.....

---

### Post by stani on 2006-11-13
You can also print to file as postscript (.ps) which will work fine in kpdf.It is easy to convert a .ps file to pdf with this command:
```
ps2pdf document.ps document.pdf
```


In case you want print pdf directly, maybe this will help. If you are using Kubuntu, you can install kprinter as a printer option in OpenOffice. Then you create pdf's by printing rather than exporting as pdf. To do so, follow these steps:
```
sudo /usr/lib/openoffice/program/spadmin
```

Press "New printer".

Choose "Connect to a PDF Converter", press "Next".

Choose "The default driver", press "Next".

Enter the following command line "kprinter --stdin", choose your home directory (eg. /home/elbuntu) with the "..." button, press "Next".

Enter the name "kprinter", click "Finish".

So next time you want to make a pdf, you just print and choose the "kprinter", which will open the familiar dialog box after finishing a print command in OpenOffice.Kprinter also allows you to use your other printers instead of pdf.


(Of course don't forget to set to landscape with "Format>Page")

Some information came from this thread:
[http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/](http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/)


Good luck,

Stani

---

