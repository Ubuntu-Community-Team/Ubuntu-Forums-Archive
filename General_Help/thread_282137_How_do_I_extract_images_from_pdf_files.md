---
title: "How do I extract images from pdf files?"
date: 2006-10-22
forum: General Help
---

### Post by brynjarh on 2006-10-22
What software can I use to extract images from pdf files?

---

### Post by meng on 2006-10-22
kpdf and Adobe reader will allow you to copy and paste figures. I'm not sure about xpdf and evince, but they may allow this too.

---

### Post by metalheart on 2006-10-22
Install xpdf-utilities with apt. There is a tool called pdfimages. It should do what you want. I have not tried this myself, but thanks to your question I will :-).

---

### Post by metalheart on 2006-10-22
Disregard my previous post. There are poppler-utilities wich have been already installed and have also tool called pdfimages.

---

### Post by rajan on 2007-10-25
sorry for reopening the old post, but i found that the pdfimages included with the poppler files didn't work (and gave no error). I had to install the full xpdf package to get it to work and now pdfimages works flawlessly. 

using dapper 6.06 as of this post.

---

### Post by octavi78 on 2008-03-13
I had the same problem as you, my problem was on the parameters: <image-root> has to be the prefix of all your images (it cannot be just ".") For example to extract the images of a file called example.pdf in the current directory try
```
pdfimages example.pdf ./exampleimage
```
it will extract the images with names like "exampleimage-001.ppm", "exampleimage-002.ppm". Then you can convert them to

---

