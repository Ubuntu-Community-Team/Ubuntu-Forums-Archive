---
title: "xml blog"
date: 2013-01-05
forum: General Help
---

### Post by lonewolf69 on 2013-01-05
I downloaded a blog template to try it locally.  I have it unzipped in /var/www/blog and can access with IP/blog/template but it throws an error.  

XML Parsing Error: not well-formed
Location: [http://75.118.219.58/Blog/Minimalist/Minimalist.xml](http://75.118.219.58/Blog/Minimalist/Minimalist.xml)
Line Number 1151, Column 23:           <div expr:g:background-color='data:backgroundColor' expr:g:text-color='data:textColor' expr:g:url='data:post.absoluteUrl' g:height='42' g:type='RatingPanel' g:width='280'/>
----------------------^

Last night the error was on line 1...

<?xml version="1.0" encoding="UTF-8" ?>

Am I missing something on this?  I have been an ASP programmer for 14 years but never worked with xml.

Thanks for any ideas.
K

---

### Post by dragonfly41 on 2013-01-06
You might have "white space" .. extra lines .. at the beginning of your file

Here is a beginner's tutorial

[http://www.w3schools.com/xml/xml_dtd.asp](http://www.w3schools.com/xml/xml_dtd.asp)

Also try installing xmlcopyeditor which is a useful xml editor in the Ubuntu Software Centre.

---

