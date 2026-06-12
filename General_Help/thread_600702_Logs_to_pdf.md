---
title: "Logs to pdf"
date: 2007-11-02
forum: General Help
---

### Post by svalding on 2007-11-02
Are there any good utilities to take log files and put them into pdf format? I've got a Nagios installation, and would like to expand it's built in reporting features. Right now it pulls from the logs and displays in an html format. I want to put this into pdf format from the logs so we can email them to different people within the department.

---

### Post by lolindrath on 2007-11-02
Hello,

Gutsy Gibbon actually includes a PDF printer so you could open the logs up in HTML and print them to the PDF printer.

--Lolindrath

---

### Post by Lord_Dicranius on 2007-11-02
I haven't played around with PDFs in Gutsy yet, but as lolindrath said above, Gutsy has PDF support by default.  I'm sure there's a way to do it by command-line, at which point you could just write up a quick script to run on the HTML files to convert to PDF.  I'm not at home on Ubuntu right now though, or else I'd try and come up with a command :(

---

