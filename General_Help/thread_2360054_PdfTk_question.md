---
title: "PdfTk question"
date: 2017-05-01
forum: General Help
---

### Post by PDA1 on 2017-05-01
I have many pdfs in one folder on my computer that I need to remove one page from, add in a different page and then save the file with the same name as the original file.

When working with only one pdf the following code works ok but the output file names on both lines must be different than the original file name of 2017.pdf (or PDFTK wont work).  I'd like it to have the final output file name as the original file name so I don't have to retype it.  What should I do?

```
pdftk 2017.pdf cat 1-2 4-end output a2017.pdf\
&&pdftk A=a2017.pdf B=page3.pdf cat A1-2 B1 A3-end output combined.pdf
```

Thank you

---

### Post by PDA1 on 2017-05-01
I sort of figured it out.  It's not perfect but does the job, though it does create an additional file with a ".pdf.pdf" as the file extension.  However, the original file name is kept intact with the new page inserted in its proper place.

   *[FONT=Ubuntu][SIZE=2]for f in 2*.pdf;       [/SIZE][/FONT]*
*[FONT=Ubuntu][SIZE=2]do  pdftk "$f" cat 1-2 4-end output "${f%}.pdf"[/SIZE][/FONT]*
*[FONT=Ubuntu][SIZE=2]pdftk A="${f%}.pdf" B=[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]**page3.pdf**[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2] cat A1-2 B1 A3-end output "${f%}";[/SIZE][/FONT]*
[I][FONT=Ubuntu][SIZE=2]done

[/SIZE][/FONT][/I][FONT=Ubuntu][SIZE=2]You programmers probably understand what all of that curious code means.  I sure don't.[/SIZE][/FONT]

---

### Post by entropy1 on 2017-05-01
If you want to remove the extra .pdf from your new file names, this is easy to do in a terminal with the rename command. For example, if you have files
```

file1.pdf.pdf
file2.pdf.pdf
file3.pdf.pdf

```
you can first do a dry run using the command
```

$ rename -n -v 's/pdf\.pdf/pdf/' *
rename(file1.pdf.pdf, file1.pdf)
rename(file2.pdf.pdf, file2.pdf)
rename(file3.pdf.pdf, file3.pdf)

```
Now that the output looks right, remove the -n and use the command
```

$ rename -v 's/pdf\.pdf/pdf/' *
file1.pdf.pdf renamed as file1.pdf
file2.pdf.pdf renamed as file2.pdf
file3.pdf.pdf renamed as file3.pdf

```

---

### Post by PDA1 on 2017-05-01
I've got a better idea!  

The extra files can be deleted by using this command-  rm *.pdf.pdf

'Tried is once and it works well.  

Thanks for the idea.

---

