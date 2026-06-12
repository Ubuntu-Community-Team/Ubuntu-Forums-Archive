---
title: "Libreoffice 4.3.3 as html wysiwyg editor"
date: 2014-06-07
forum: General Help
---

### Post by tsaker on 2014-06-07
Did a clean install of Trusty with LO. In prior versions including Saucy, I used Libreoffice Writer as a quick wysiwyg html editor. I just tried to do the same and discovered that when exporting from odt or opening an html file and saving it in the same format turns a 20-30 kb file into a 20-30 mb file. I have Bluefish, but I'm very inexperienced with coding html directly and don't have the time to learn it right now. Kompozer doesn't seem to be available anymore in the Software Center. I want to update some web pages. Am I missing some setting in Libreoffice that keeps the file size at the proper level instead of bloating it to unimaginable heights?I have Bluefish

---

### Post by vasa1 on 2014-06-07
Instead of exporting, did you try "Save as" and then choosing the html format from filetypes?

---

### Post by tsaker on 2014-06-07
Yes, I did. Same result.

---

### Post by vasa1 on 2014-06-07
I took a 1.6 kiB **"plain text"** file, added some bold/italic formatting and saved as HTML. The html file is 4.3 kiB.

---

### Post by tsaker on 2014-06-07
I took an existing html file (20.3 kb), changed some links and text, saved it in html format. Resulting file size: 38.1 mb.

---

### Post by tsaker on 2014-06-07
The text version is 43.3 kb.

---

### Post by tsaker on 2014-06-07
I started from scratch. So far, the file size is 14.3 kb.

---

### Post by tsaker on 2014-06-09
As soon as I added images, the file size ballooned again to 36 mb. I give up.

---

### Post by SeijiSensei on 2014-06-10
You need to add the images as hyperlinks.  You can't insert the images directly into the document.  Use hyperlink tags like:
```
<img src="/images/mylogo.png" height= ... >
```
Of course you also have to place the images into the proper directory on the web server.

[WordPress]("http://wordpress.org/") is a handy tool if you want to design a site from scratch.  It gives you all the tools to design the pages, upload images, etc.  You can either install your own instance on a web server or set up an account at wordpress.com.

---

