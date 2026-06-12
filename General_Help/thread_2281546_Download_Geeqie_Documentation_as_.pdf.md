---
title: "Download Geeqie Documentation as .pdf"
date: 2015-06-07
forum: General Help
---

### Post by Ralph L on 2015-06-07
I recently installed Geeqie.  Its documentation is on a web site so I have to be web connected to read it.  I often am without that--like in a airplane, camping, etc.  I couldn't find a pdf version of it.  Is there a program that would download it and make a .pdf out of it.  I tried to download it with firefox extension "printpdf", but I just got the first page of a multi-page document.  I need something that would download all pages and put them together.  Geeqie documentation is at file:///usr/share/doc/geeqie/html/GuideIndex.html 
Any help appreciated....

---

### Post by grahammechanical on 2015-06-07
1) Select the text
2) copy the text
3) Paste the text into Lbreoffice
4) Export the text as a PDF document.

Or, if using Firefox

install an addon called Save as PDF 1.5.1-signed. It is described as "Lets you download as PDF in one click." and then there is Print Pages to PDF 0.1.9.2.1-signed. It is described as "Creates one PDF from any amount of open browser tabs."

Regards.

---

### Post by Keith_Helms on 2015-06-07
I don't know of anything that will pull down an entire site with multiple pages and convert that to a PDF.   However, you CAN pull down all the web pages for offline viewing with a browser.  Open a terminal window, create a directory somewhere to hold the pages, CD into that directory, and run the following command.  If you're using some other site to view the manual, change the --domains entry and the last line to reference that site instead.

```
wget \
     --recursive \
     --page-requisites \
     --html-extension \
     --convert-links \
     --domains soc.if.usp.br \
     --no-parent \
         http://soc.if.usp.br/manual/geeqie/html/ 
```

Once it's all downloaded, click on Open File in your browser, navigate down through the directory levels that the command created - soc.if.usp.br/manual/geeqie/html - and open the index.html file.   That should give you the same pages you normally see online.

---

### Post by Ralph L on 2015-07-03
Keith_Helms (and others):  Thank you for your responses.  I really appreciate it.  Keith, your solution worked and certainly helped.  Not as good as a pdf, but definitely allows me to read the manual when not connected to the Internet.  I would never have figured that out on my own.

grahammechanical:  Just using libreoffice as you suggest worked, but the way the manual is formatted would have required an awful lot of editing to make a usable pdf manual.  I tried for a while, but gave up because of the amount of work.  But thank you.

---

