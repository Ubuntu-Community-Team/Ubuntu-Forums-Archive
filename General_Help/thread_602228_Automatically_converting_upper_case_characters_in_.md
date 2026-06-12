---
title: "Automatically converting upper case characters in files and hyperlinks to lower case"
date: 2007-11-04
forum: General Help
---

### Post by zoqaeski on 2007-11-04
I've got a heap (>50) of *.html files which have most of their hyperlinks referencing files with upper case letters in them, some of which are File.html and others which are like FileWithCamelCaseName.html . 
Now, I want to be able to batch rename the files (and their containing folders) to lower case, replacing CamelCase with camel_case where that occurs, and then change all of the hyperlinks in the files to match these new names, without manually finding each one and changing each reference (because there are so many files, and I don't have several hours to spare).
I'm sure such an operation could be done automatically, i.e. with sed or vim or something, but I can't quite get my head around the regular expressions this would need (especially considering that the html files are strict XHTML1.1 with lots of "double quotes" for variables and the like). Could anyone give me a pointer in the right direction?

---

### Post by dcstar on 2007-11-04
> **zoqaeski said:**
> I've got a heap (>50) of *.html files which have most of their hyperlinks referencing files with upper case letters in them, some of which are File.html and others which are like FileWithCamelCaseName.html . 
Now, I want to be able to batch rename the files (and their containing folders) to lower case, replacing CamelCase with camel_case where that occurs, and then change all of the hyperlinks in the files to match these new names, without manually finding each one and changing each reference (because there are so many files, and I don't have several hours to spare).
I'm sure such an operation could be done automatically, i.e. with sed or vim or something, but I can't quite get my head around the regular expressions this would need (especially considering that the html files are strict XHTML1.1 with lots of "double quotes" for variables and the like). Could anyone give me a pointer in the right direction?

There are multiple rename utilities available in the repositories, a simple search in Synaptic returns a list that you can look at and select to try.

---

