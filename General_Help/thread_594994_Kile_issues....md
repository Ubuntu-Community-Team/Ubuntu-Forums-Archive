---
title: "Kile issues..."
date: 2007-10-28
forum: General Help
---

### Post by rosiny on 2007-10-28
So I keep having this problem that when I try to viewpdf (or viewanything) in Kile, it gives me exit status 127. I tried changing the QuickBuild function to become dvi to ps, then ps to pdf even, and that still gives me the same error... anyone know how to fix this?

---

### Post by rosiny on 2007-10-29
Anyone help?

---

### Post by santbern on 2007-10-30
Rosiny, I was having the same problem and many others before that. If your latex file compiles OK and generates the dvi file, try going to the directory where the dvi file resides and click on it. In my case, I was able to see the file with some unknown 'document opener', but without the figures (all blank spaces). I solved the problem by installing KDVI using the Synaptic Package Manager under Administration. Other more serious problems, like basic latex compiling, I solved by installing Lyx. I'm beginning to love this Ubuntu thing :).

---

### Post by dimkadimon on 2008-01-02
Here is a much better solution:

Open Kile. Go to Settings -> Configure Kile...

Click Tools (on left side) and select Build. For ViewDVI, ViewPDF and ViewPS write the name of your favourite text viewer(s) in the Command textfield. That should fix it.

---

### Post by dfmalh on 2008-06-25
Hi, was having the same problem until last night. I take it you are not working in the KDE environment, but the Gnome one.

This is what works (and creates what) and does not work:

Create a _test.tex_ file... (the first file you need)

- QuickBuild creates:
[LIST]_test.aux_, _test.dvi_ and _test.lo_g[/LIST]  
[LIST]and automatically open/view the _test.dvi_ with KDVI[/LIST]

- LaTeX creates:
[LIST]_test.aux_, _test.dvi_ and _test.log_[/LIST]

- ViewDVI:
[LIST]open/view the _test.dvi_ with KDVI[/LIST]

- DVItoPS creates:
[LIST]_test.ps_[/LIST]

- ViewPS:
[LIST]an error message are displayed with an "exit status 127" message[/LIST]
[LIST]Kile does not come standard with the Gnome desktop environment, you have to install the package. It did not install **kghostview** automatically, which you need to open/view test.ps, you have to do that (Synaptic Package Manager)[/LIST]
[LIST]open/view the _test.ps_ with KGhostView[/LIST]

- PDFLaTeX creates:
[LIST]_test.aux_, _test.log_ and _test.pdf_[/LIST]

- ViewPDF:
[LIST]open/view the _test.pdf_ with KPDF[/LIST]

- DVItoPDF:
[LIST]an error message are displayed with an "exit status 127" message[/LIST]
[LIST]Kile does not come standard with the Gnome desktop environment, you have to install the package. It did not install **dvipdfmx** automatically, which you need to create _test.pdf_ from _test.dvi_, you have to do that (Synaptic Package Manager)[/LIST]
[LIST]create _test.pdf_ from _test.dvi_ with dvipdfmx[/LIST]

- PStoPDF creates:
[LIST]_test.pdf_ from _test.ps_[/LIST]


I also had to install the "**khelpcenter**" package to get the Help (F1) to work in Ubuntu/Gnome.

Once you have these packages, everything should be working in Kile, without having to re-Configure Kile to use other packages to view your *.ps file or convert the *.dvi to the *.pdf :)

Hope this helps someone.

---

