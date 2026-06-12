---
title: "Print PDF from Browser - Black Paper"
date: 2017-02-01
forum: General Help
---

### Post by ekusanagi on 2017-02-01
Hello!

I had a problem when I try to print a PDF from browser, sometimes occur  when i print from PDF Editor of Ubuntu.

The printed paper comes out black with smudges, when i try to print with other programs like LibreOffice the printed paper comes out normal.

I have 2 printers, 1 by ip and other shared. And the problem occu on all computers of my network.

I'm trying to change my workspace from Windows to Ubuntu.


Thank you!

---

### Post by ajgreeny on 2017-02-01
Please use the default font for your posts; the large font you used is deemed by many users to be shouting, and it will certainly not get answers any more quickly.

What exactly is the **PDF Editor of Ubuntu** that you mention?

---

### Post by ekusanagi on 2017-02-01
Oh, I'm sorry.


PDF Viewer**** is a default program for open PDF in Ubuntu that come preinstalled.

Thank you.

---

### Post by ajgreeny on 2017-02-01
Which version of *ubuntu are you using as the application used to view, (note, to view, not edit PDFs, which is another story) varies according to your desktop environment.
In many of the OSs, including Ubuntu itself, the pdf document reader is **evince**, but it could be different if you use KDE (Kubuntu), for example.

---

### Post by HermanAB on 2017-02-01
This is a bit weird for sure.  A PDF is a file that is formatted for printing and you can send it straight to a printer and the CUPS system will print it for you.  

On Linux/BSD/Mac, you don't necessarily need to run a specific application to print something - just send the file to CUPS and it will usually figure it out and convert the file to postscript all by itself.

For example to print to the default printer on your machine:

$ lpr -P localhost file.pdf

It also works with text files and even pictures.  You don't need to fire up a PDF reader or Gimp to print.  You can also pipe multiple files and then go and feed the trees and toner into the printer.

---

