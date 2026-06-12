---
title: "peazip in context menu"
date: 2013-04-16
forum: General Help
---

### Post by Stauricus on 2013-04-16
hello everybody
i'm wondering if there is a way to have a peazip command to extract a file to a new folder in the context menu. something like this: 
[IMG]http://farm3.staticflickr.com/2152/2542590082_49fafe3f8f.jpg[/IMG]

i got this pic from google images, but what i want is the function "Extract to .\error.log.etc". an option in context menu that creates a new folder with the same name of the compressed file, and extract the files to it. the default "Extract here" function in PCManFM just extract everything to the same folder, making a huge mess.
i'm using Lubuntu 12.10 and Peazip (but any extractor is fine to me).
thanks in advance :)

---

### Post by codyj110 on 2013-04-16
i'm not sure of what ui there is for just clicking and making it happen but you can open a terminal and type this in the folder were the zip file is          
unzip filename.zip -d foldername
just replace flodername with what you want to call it. it will extract files into new dir

---

### Post by Stauricus on 2013-04-17
well, that's an idea, but does not solve the problem.
when you install IZarc in Windows, the context menu is automatically created. in Lubuntu, it does not...

---

