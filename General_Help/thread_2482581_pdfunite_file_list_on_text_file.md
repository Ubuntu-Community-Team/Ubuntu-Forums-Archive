---
title: "pdfunite file list on text file"
date: 2023-01-04
forum: General Help
---

### Post by jfca283 on 2023-01-04
Hello, 
I need to unite a list of many pdf files.
The names are on a text file.
I tried using pdfunite file_list.txt output.pdf, but obviously, It didn't work.
How can I join the files using pdfunite and the txt file?
Thanks for your answers and time, folks.
Have a good day.

---

### Post by dragonfly41 on 2023-01-04
Try this Python package ..

[https://pypi.org/project/PDFknife/](https://pypi.org/project/PDFknife/)

---

### Post by ActionParsnip on 2023-01-04
[https://askubuntu.com/questions/2799/how-to-merge-several-pdf-files](https://askubuntu.com/questions/2799/how-to-merge-several-pdf-files)

Has some good answers. Even a GUI opinion (yuck)

---

### Post by Holger_Gehrke on 2023-01-05
```
pdfunite $(cat file_list.txt) output.pdf
```
The '$(...)' is a command substitution, the output of the command in the parentheses takes the places of the whole construct before the outer command is executed.

Holger

---

### Post by mIk3_08 on 2023-01-05
> **jfca283 said:**
> Hello, 
I need to unite a list of many pdf files.
The names are on a text file.
I tried using pdfunite file_list.txt output.pdf, but obviously, It didn't work.
How can I join the files using pdfunite and the txt file?
Thanks for your answers and time, folks.
Have a good day.
You need first to convert the txt file to pdf then you can use 
```
pdfunite output1.pdf output2.pdf
```
Mine, I am using pdftk. 
the command is almost the same with the pdfunite
```
pdftk output1.pdf output2.pdf cat output filename.pdf
```

---

