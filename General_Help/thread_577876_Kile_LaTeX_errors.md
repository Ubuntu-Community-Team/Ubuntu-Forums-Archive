---
title: "Kile LaTeX errors"
date: 2007-10-16
forum: General Help
---

### Post by kung fu buntu on 2007-10-16
I'm thinking on using *CUED PhD/MPhil Thesis Style* from [http://www-h.eng.cam.ac.uk/help/tpl/textprocessing/reports.html](http://www-h.eng.cam.ac.uk/help/tpl/textprocessing/reports.html) as my MSc thesis template.

It builds fine with make (it has a Makefile) but because I like using Kile (nice IDE for LaTeX) it would be great to have it working there. I have already fixed some minor errors/warnings but I can't get rid of these:
```
[PDFLaTeX] thesis.tex => thesis.pdf (pdflatex)
./Classes/CUEDthesisPSnPDF.cls:0: Values of option `pdfpagelayout':(hyperref) * `SinglePage'(hyperref) * `OneColumn'(hyperref) * `TwoColumnLeft'(hyperref) * `TwoColumnRight'(hyperref) * `TwoPageLeft' (PDF 1.5)
./thesis.tex:158: \fancyhead's `E' option without twoside option is useless on input line 158. \fancyhead's `E' option without twoside option is useless
thesis.tex:0:No file thesis.nls.
./Introduction/introduction.tex:0: destination with the same identifier (name{page.1}) hasbeen already used, duplicate ignored\relaxl.13[1
[PDFLaTeX] 0 errors, 4 warnings, 0 badboxes
[PDFLaTeX] Done!
```These are warnings not errors, but I would still like to have this fixed.

Now, the "No file thesis.nls" message is because makeindex isn't being executed. If I try to run makeindex inside kile (alt+=) it prints an error message *thesis.idx does not exist*... as expected because in the Makefile I have something like this:
```
%.ind: .itmp
	@if [ -f $*.idx ]; then \
		$(MAKEINDEX) $*; \
		touch .rerun; \
		touch .itmp; \
	fi
.......
@$(MAKEINDEX) -s nomencl.ist -o $*.nls $*.nlo
```

Thanks!

---

### Post by glitchBen on 2008-02-21
I was having the same trouble in Kile.  makeindex would run fine at the command line but not in Kile.  To get it to work, I had to change the makeindex settings in the Kile configuration (Settings > Configure Kile).  Under the Tools > Build section, the list of the tools is shown in a pannel.  Change the Options to:
'%S.nlo' -s nomencl.ist -o '%S.nls'
and under the Advanced tab, remove the default extensions.  Hope this helps.

---

### Post by buntu_hugenewbie11 on 2008-05-12
I seem to not be able to use new packages that should be included in the current setup. Or if a university has specific formats set up as documentclass I can't seem to ever compile. Does anyone else have problems with Latex packages and Kile?? It seems to be a permissions issue but I don't really know.
How can I make sure that tetex and texlive are being acessed by Kile?

---

