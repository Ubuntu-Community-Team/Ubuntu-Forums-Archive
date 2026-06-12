---
title: "PDF saves as post sript"
date: 2008-03-31
forum: General Help
---

### Post by Robbyx on 2008-03-31
In Gutsy, when I  print to file using the cups/ pdf printer it is wrongly saved as a Postsript file. As this must be happening to everyone using this driver I would very much like to know how others have solved it.

---

### Post by xeth_delta on 2008-03-31
I know this is not a solution to your problem, but it is a work-around. You can convert the file from ps to pdf with "ps2pdf".
```
ps2pdf ps_file_name pdf_file_name
```

---

### Post by Robbyx on 2008-03-31
Thank you for that advice. In an emergency I will use that approach.  It will mean that I will have to open up my file manager, copy the url of the saved file into the  command line and run the command. I hope there are other solutions.

In windows I used to use pdffactory pro. Is there a gui program that does the same in Ubuntu?

---

### Post by xeth_delta on 2008-03-31
> **Robbyx said:**
> Thank you for that advice. In an emergency I will use that approach.  It will mean that I will have to open up my file manager, copy the url of the saved file into the  command line and run the command. I hope there are other solutions.

In windows I used to use pdffactory pro. Is there a gui program that does the same in Ubuntu?

There might be a GUI, but I never used one for converting between ps and pdf, sorry.
Using the command line is not that complicated, it is a powerfull tool, it just takes practice.
No need to copy the URL. Open a terminal, cd to the directory where you are saving the file, ls to show the contents, TAB for autocompletion of file/directory and command names. For example:
```
cd Desktop
ls
ps2pdf file.ps file.pdf
```

Don't hesitate to ask if you have further questions.

[EDIT] If you copy the url, and the directories or file name fave spaces, you will have to precede those spaces with a \ in the command line, for instance:
```
ps2pdf ps\ file\ name.ps file.pdf
```

---

### Post by Robbyx on 2008-03-31
Thank you for that further helpful explanation. I was actually referring to a gui that does what pdffactory pro does. It is a virtual printer that pops up and shows the content of the files that have been sent to it. It can then be saved as a pdf, manipulated by removing some of the pages or  printed direct to the printer.

---

### Post by xeth_delta on 2008-03-31
> **Robbyx said:**
> Thank you for that further helpful explanation. I was actually referring to a gui that does what pdffactory pro does. It is a virtual printer that pops up and shows the content of the files that have been sent to it. It can then be saved as a pdf, manipulated by removing some of the pages or  printed direct to the printer.

Just found a program that might be useful to you. Try installing gtklp, it is in the repositories. Let me know what if that's what you were looking for.

[EDIT] Another one you could try: [http://lpy.sourceforge.net/](http://lpy.sourceforge.net/)

---

### Post by Robbyx on 2008-03-31
I had a look at both of your suggestions and thank you for the effort and research.  

I think both are not designed to produce PDFs. They seem to be printer control tools.

---

### Post by xeth_delta on 2008-03-31
> **Robbyx said:**
> I had a look at both of your suggestions and thank you for the effort and research.  

I think both are not designed to produce PDFs. They seem to be printer control tools.

No problem, sorry I could not offer more information. Maybe another user can shed some more light.

---

