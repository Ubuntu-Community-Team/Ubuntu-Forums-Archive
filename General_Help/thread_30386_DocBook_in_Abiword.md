---
title: "DocBook in Abiword"
date: 2005-04-28
forum: General Help
---

### Post by nat on 2005-04-28
I have seen that Abiword can save documents as Docbook. (my gentoo install does). Does anyone know how to enable Docbook support in Abiword in Ubuntu?

Thanks!

---

### Post by Alexander Kirillov on 2005-04-28
[QUOTE=nat]I have seen that Abiword can save documents as Docbook. (my gentoo install does). Does anyone know how to enable Docbook support in Abiword in Ubuntu?

Thanks![/QUOTE]
 Works out of the box here - nothing to enable. Just select "save as" and scroll down to DocBook.

---

### Post by nat on 2005-04-29
I dont have that option here in the "save as...". That is why I asked. I maybe miss some packages?

im running abiword-gnome.

---

### Post by Alexander Kirillov on 2005-04-29
[QUOTE=nat]I dont have that option here in the "save as...". That is why I asked. I maybe miss some packages?

im running abiword-gnome.[/QUOTE]
 Which DocBook-related packages do you have? I have docbook, docbook-xml, and docbook-dsssl.

Are you certain there is no DocBook option? I had to scroll the list - it is at the bottom of the list of formats. What about other formats, such as latex or XSL-FO?

---

### Post by nat on 2005-05-02
I have:

ii  docbook        4.3-1ubuntu2   standard SGML representation system for tech
ii  docbook-dsssl  1.79-1         modular DocBook DSSSL stylesheets, for print
ii  docbook-simple 1.0.0-6.1      Simplified DocBook XML Doctype and css style
ii  docbook-xml    4.3-1.1ubuntu1 standard XML documentation system, for softw
ii  docbook-xsl    1.66.1-1       stylesheets for processing DocBook XML files

No, I am 100% sure there is no docbook in the "save as..." no latex either. Its only abiword formats, MS word and rtf, plain text and html. (totally 10 different formats)

strange. I have dookbook on another ubuntu box.

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=nat]I have:

ii  docbook        4.3-1ubuntu2   standard SGML representation system for tech
ii  docbook-dsssl  1.79-1         modular DocBook DSSSL stylesheets, for print
ii  docbook-simple 1.0.0-6.1      Simplified DocBook XML Doctype and css style
ii  docbook-xml    4.3-1.1ubuntu1 standard XML documentation system, for softw
ii  docbook-xsl    1.66.1-1       stylesheets for processing DocBook XML files

No, I am 100% sure there is no docbook in the "save as..." no latex either. Its only abiword formats, MS word and rtf, plain text and html. (totally 10 different formats)

strange. I have dookbook on another ubuntu box.[/QUOTE]
 Do you have package abiword-plugins installed? Are they activated (check  Tools-Plugins menu in abiword)?

---

### Post by nat on 2005-05-03
[QUOTE=Alexander Kirillov]Do you have package abiword-plugins installed?[/QUOTE]
This was the package I needed. Thank you very much!

---

