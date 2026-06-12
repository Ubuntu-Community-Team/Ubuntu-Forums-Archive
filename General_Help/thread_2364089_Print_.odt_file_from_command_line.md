---
title: "Print .odt file from command line"
date: 2017-06-18
forum: General Help
---

### Post by raleigh3 on 2017-06-18
Is there a way to print a .odt file from the command line ?

---

### Post by vasa1 on 2017-06-18
*man libreoffice*```
       -p file...
              Prints  the given files to the default printer and ends. The splash
              screen does not appear.

              If the file name contains spaces, then it must be enclosed in  quo&#8208;
              tation marks.

       --print-to-file   [--printer-name   printer_name]   [--outdir  output_dir]
       file...
              Batch print files to file.  If --printer-name is not specified  the
              default  printer  is  used.   If --outdir is not specified then the
              current working directory is used as the output directory  for  the
              converted files.

```

---

### Post by raleigh3 on 2017-06-19
thanks.

---

