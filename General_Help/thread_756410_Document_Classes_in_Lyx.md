---
title: "Document Classes in Lyx"
date: 2008-04-15
forum: General Help
---

### Post by evanmanny on 2008-04-15
I'm trying to create my own layout file for lyx and I figured that a good place to start is to copy one of the existing layout files and modify it. I "cp /usr/share/lyx/layouts/book.layout /usr/share/lyx/layouts/thesis.layout" and modify the second line of  the new file to read "#  \DeclareLaTeXClass{thesis}" and then go to Tools > Reconfigure and restart lyx as outlined in the documentation. When I try to select thesis as a document class it is listed as "Unavailable: thesis" and if I try to apply it I get the error "The layout file requested by this document, thesis.layout, is not usable. This is probably because a LaTeX class or style file required by it is not available. See the customization documentation for more information. LyX will not be able to produce output." The classes and styles required by thesis are identical to those required by book so I don't see how that's the problem. Does anybody have any insight?

---

### Post by polmir on 2008-04-19
Install this package
```
sudo apt-get install texlive-publishers
sudo apt-get install texlive-science
```

---

### Post by abyhoe on 2008-05-16
> **polmir said:**
> Install this package
```
sudo apt-get install texlive-publishers
sudo apt-get install texlive-science
```
I am having the same problem as evanmanny. I have llncs.layout in /usr/share/lyx/layouts but it is listed as "Unavailable: article (Springer LNCS)".

When I Reconfigure in Lyx, it gives an error message: "The system reconfiguration has failed. Default textclass is used but Lyx may not be able to work properly. Please reconfigure again if needed."

What do I miss?

What is supposed to do after sudo apt-get install texlive-publishers and texlive-science?

Thanks.

---

### Post by kaspar_silas on 2008-07-07
Did you have any success finding the answer to why Lyx gave 

"The system reconfiguration has failed. Default textclass is used but Lyx may not be able to work properly. Please reconfigure again if needed."

As I have this problem as well now.

---

