---
title: "can I print all files in a directory and its subdirectories in a single command?"
date: 2015-05-20
forum: General Help
---

### Post by Bjrn_Kunter on 2015-05-20
Hi,

I have received a scanned financial project report, containing of 400 or so files sorted in a multitude of subdirectories, sub-subdirectories, sub-sub-subdirectories etc.

To avoid opening up every directory and then printing all the files singlehandidly  (and going crazy in the process) I am looking for a nice solution to print 

 
[LIST=1]
[*]the files from all the sub- and sub-subdirectories all into one large pdf-file (or other file I can then print out on paper).
[*]As an additional problem the files are of different types, (pdf, jpg, doc and xls)
[*]An extra bonus would be to have the name of the original files printed in the header or footline.
[/LIST]
 
I checked the forums, but I could not find a solution to print files from subdirectories. 
Does anyone have a clue?

Thank You

    Bjoern

---

### Post by SeijiSensei on 2015-05-20
You can print text, JPEG, and PDF files from the command prompt with the lpr command:
```
lpr /path/to/document.pdf
```
So for the PDFs,you could use:
```

cd /path/to/the/documents 
lpr *.pdf
lpr *.jpg

```
Files in formats like DOC or XLS can only be printed from an application like Word or LibreOffice Writer. Apparently LO can convert documents on-the-fly from the command prompt: [http://ask.libreoffice.org/en/question/2641/convert-to-command-line-parameter/](http://ask.libreoffice.org/en/question/2641/convert-to-command-line-parameter/) so it might be possible to use that method.  Or this one: [http://superuser.com/questions/486130/printing-from-the-command-line-with-libreoffice-lpr-commands](http://superuser.com/questions/486130/printing-from-the-command-line-with-libreoffice-lpr-commands)

You may need to specify the printer's name (actually its CUPS queue) with -P, e.g., 
```
lpr -P myhp chart.jpg
```
or navigate to [http://localhost:631/](http://localhost:631/) on the computer, choose Administration, Manage Printers.  Then click on the printer's name, choose Administration, and Set as Server Default.  Then lpr will use that printer automatically. Enter your username and password when prompted.

You can write a script to recurse through the subdirectories, or just run the lpr command(s) in each subdirectory manually.

You can use **pdftk** to merge PDFs.  **Imagemagick** will convert graphics to PDF. They're both in the repositories.

---

### Post by leunam12 on 2015-05-20
Hi SeijiSensei, 
thanks for the information, very useful. Do you know if this would work with "find" and be recursive?

Thanks

---

### Post by HermanAB on 2015-05-20
Yes, you can use find with exec and lpr - be sure to put quotes around it.  Read the lpr man page for the various options.

---

### Post by Bjrn_Kunter on 2015-05-20
Thanks SeijiSensei,

for the explanations, so in my case it seems I still need a lot of different steps to get everything printed. 

> **SeijiSensei said:**
> 

You can write a script to recurse through the subdirectories, or just run the lpr command(s) in each subdirectory manually.



Unfortunately I have not written scripts yet. I checked some tutorials and could not find what I looked for (but maybe it was there and I just did not understand it)

So in my case the script would have to start in one (root) directory then move to the next subdirectory print all pdf, print all jpg, print docs and exe via libre office, and then move to the next sub-directories, repeat the printing and so on until the complete directory tree has been printed. 

Sounds great, but I am afraid I will be unable to write it... :-(

---

### Post by nerdtron on 2015-05-20
List all files including does in the subdirectories and then print using lpr. (I haven't used lpr yet, but if it works on a single, then it should work will all files)

Here goes:
First run this command, which will just list all files on the directory and subdirectories:
```
find /path/to/directory -type -f 
```

Now if the files that you see listed are the ones you really want to print, then add the lpr command:
```
 find /path/to/directory -type f -exec lpr {} \; 
```

---

